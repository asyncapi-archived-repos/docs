## A basic example

```yaml
asyncapi: '1.0.0'
info:
  title: Streetlights API
  version: '1.0'
  description: |
    The Smartylighting Streetlights API allows you
    to remotely manage the city lights.
  license:
    name: Apache 2.0
    url: 'https://www.apache.org/licenses/LICENSE-2.0'
baseTopic: smartylighting.streetlights.1.0

servers:
  - url: api.streetlights.smartylighting.com:{port}
    scheme: mqtt
    description: Test broker
    variables:
      port:
        description: Secure connection (TLS) is available through port 8883.
        default: '1883'
        enum:
          - '1883'
          - '8883'

topics:
  event.{streetlightId}.lighting.measured:
    publish:
      $ref: '#/components/messages/lightMeasured'

components:
  messages:
    lightMeasured:
      summary: Inform about environmental lighting conditions for a particular streetlight.
      payload:
        $ref: "#/components/schemas/lightMeasuredPayload"

  schemas:
    lightMeasuredPayload:
      type: object
      properties:
        lumens:
          type: integer
          minimum: 0
          description: Light intensity measured in lumens.
        sentAt:
          $ref: "#/components/schemas/sentAt"
    sentAt:
      type: string
      format: date-time
      description: Date and time when the message was sent.
```

This example describes a very basic streetlights service. It says there's a service you can connect at`api.streetlights.smartylighting.com`\(port 1883 or 8883\) and it allows you to publish information about environmental lighting conditions.

Afterwards, the service might decide to turn on or off certain lights or it might simply log it for statistics. Or both! That's up to your implementation.

If you are familiar with the OpenAPI specification I'm sure you already found lots of similarities. But, what's this `topics` section in the file? And what's this `event.{streetlightId}.lighting.measured`? Let's dive into it!

