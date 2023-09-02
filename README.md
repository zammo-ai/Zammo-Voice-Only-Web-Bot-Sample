# Zammo Bot Voice-Only Web Integration

## Important Note

To understand (or use) this sample, you need to be familiar with [Zammo](https://zammo.ai/) (and ideally have an instance provisioned).

If this is not the case and you are interested in learning more, you can contact the Zammo team by using the form at the bottom of this [web page](https://zammo.ai/).

## Description

The Zammo Bot that you create in the Zammo Portal can be exposed in several ways:

- Web chat integration
- Interactive Voice Response
- Behind a digital agent
- At the front of a contact center

In this repository, we are looking at a Voice-only web integration.

This integration combines the benefits of the voice bot (which can be easier and faster to interact with) and the web (which provides infrastructure and integrations on many platforms).

### Use Cases

#### Feedback Companion

When conducting research or surveys projects, this integration can be very useful for providing a way for participants to share feedback.

As speaking is faster than typing, it enables participants to go through more questions as they can do so hands-free, and from many devices (including their phones).

#### Voice Assistant | IVR Prototype

When creating a Voice Assistant or an IVR, in the early stages, the voice-only experience can help quickly test the interaction.

The available web interface also provides an avenue for multimodal interactions (using the screen for additional interactions).

## How to Set It Up?

### Requirements

#### Zammo Bot Credentials

You will need to have a valid Zammo account and a created bot.

In the Zammo portal, you will fetch the `src`, `cssUrl`, `zammoApiBaseUrl`, and `webchatId`. You will also configure the allowed domains for the web integration instance.

To do this, perform the following steps:

1. Activate the web chat channel in the Zammo Portal and click `Edit`:

![Zammo portal channels page](https://conversational-ai-faq.notion.site/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F5e2eee77-1313-4960-b710-0fe01f3176ba%2FUntitled.png?table=block&id=5356883e-4829-47f5-8f7c-b17a24263166&spaceId=5efc90cc-d9f4-40eb-911e-430937dd3b0a&width=2000&userId=&cache=v2)

2. Set the domains field to allow your desired domains, or allow all by supplying \* (or an exhaustive list of whitelisted domains):

![Zammo portal web chat domain configuration](https://conversational-ai-faq.notion.site/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F41160837-99b1-4e66-8371-f5efb9fc6e5d%2FUntitled.png?table=block&id=9a4b7d97-7da3-443b-a413-e7b55c8eb218&spaceId=5efc90cc-d9f4-40eb-911e-430937dd3b0a&width=2000&userId=&cache=v2)

3. Click on "Get My Webchat Code," and the following modal popup is displayed:

![Zammo portal web chat snippet](https://conversational-ai-faq.notion.site/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F3b6c9199-0509-4424-bb63-76cf9838446c%2FUntitled.png?table=block&id=fc4d85a9-fb27-4492-860c-24e26108babc&spaceId=5efc90cc-d9f4-40eb-911e-430937dd3b0a&width=2000&userId=&cache=v2)

4. Take note of the following values from the modal popup:

- `src`
- `cssUrl`
- `zammoApiBaseUrl`
- `webchatId`

### Installation

Update the sample.HTML page with your credentials in the corresponding section marked with the `<!-- ZAMMO CONFIGURATION SCRIPT -->` and fill in the details from the Zammo bot credentials in the corresponding section.

Host the sample.html file on any web servers capable of serving static content. Some options:

- [Using Azure storage account](https://learn.microsoft.com/en-us/azure/storage/blobs/storage-blob-static-website-how-to?tabs=azure-portal)
- [Using a local http-server](https://github.com/http-party/http-server)

## Demo

https://github.com/zammo-ai/Zammo/assets/4819282/43bd5674-20ae-48a2-ae7c-95164f6273cb

## Libraries

The sample is:

- self-contained for simplicity of hosting
- written in plain JavaScript for extended browser capabilities

The sample makes use of the following open-source libraries:

- [Sweet Alert](https://sweetalert2.github.io/) for all of the dialog modals in the application
- [JS Base64](https://github.com/dankogai/js-base64) to facilitate audio processing

## Integration into Your Product

You can use the code to enable your Zammo build bot as a standalone application or by importing it into your application.

When importing into your own application, you can also export the section under `<!-- APP SCRIPT -->`, and you can adjust or replace any elements to match your branding guidelines.

Some of the key functions are:

- `initializeBot`: which initializes the connection to the bot.
- `processWebSocketMessage`: which allows you to customize how you process the bot response.

### Specificities

#### Mobile Restriction

[Web browsers require](https://developer.chrome.com/blog/autoplay/#web-audio) that a user interaction is performed before allowing Javascript to use the audio output.

On mobile, there is an additional restriction in which audio needs to be played right after the action to allow the app to play audio later in any asynchronous part.

When making changes, you will need to ensure that these two requirements are met; otherwise, you may experience issues where no sound will be played for the bot prompt.

In the sample, we display a modal to inform the user that the application accesses the microphone. When the user approves, we play a short silence which helps meet the two criteria.

#### Troubleshooting on Mobile

When troubleshooting on mobile, it can be difficult to access the console to view error messages. The sample has [Eruda](https://github.com/liriliri/eruda) imported that you can turn on by passing a query argument `debug` to the URL where you host the sample.

You can then add additional `console.log` to the sample and view the debug on mobile or any other device.

### Notes

We recommend ensuring that your changes align with [accessibility standards](https://www.w3.org/WAI/standards-guidelines/wcag/).

## Contribution

Zammo does not accept direct contributions to this repository, but our team would love to get your feedback. The primary channel for sending your feedback will be to use the form on our [website](https://zammo.ai).

If you are already a Zammo customer, please engage with our Customer Success teams or your account manager.

## License

Copyright Zammo.
