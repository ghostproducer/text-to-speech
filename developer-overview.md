---

copyright:
  years: 2015, 2017
lastupdated: "2017-10-20"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:tip: .tip}
{:pre: .pre}
{:codeblock: .codeblock}
{:screen: .screen}
{:javascript: .ph data-hd-programlang='javascript'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:swift: .ph data-hd-programlang='swift'}

# Overview for developers
{: #overview}

You can access the speech synthesis capabilities of the {{site.data.keyword.texttospeechshort}} service via an HTTP Representational State Transfer (REST) API or a WebSocket interface. Several Software Development Kits (SDKs) are also available to simplify application development in various languages and environments. The following sections provide an overview of application development with the service.
{: shortdesc}

## HTTP interface
{: #http}

To synthesize text with the HTTP REST API, you call the `GET` or `POST` version of the service's `/v1/synthesize` method. The two versions of the method offer generally equivalent functionality:

-   *Input text:* The `GET /v1/synthesize` method accepts the text to be synthesized via a query parameter. The `POST /v1/synthesize` method accepts the text in the body of the request. Both methods impose a size limit of 5 KB on the text to be synthesized.

    You can pass the service plain text or text that is annotated with the Speech Synthesis Markup Language (SSML). SSML is an XML-based markup language that provides annotations of text for speech synthesis applications such as the {{site.data.keyword.texttospeechshort}} service. The service augments SSML with service-specific expressive and voice-transformation elements.
-   *Voices:* The service accepts text and produces audio output in a variety of languages, voices, and dialects. The service offers at least one male or female voice, sometimes both, for each supported language and different dialects such as US and British English. You can use the service's `GET /v1/voices` or `GET /v1/voices/{voice}` methods to learn more about the supported voices. The service synthesizes the text into the language of the specified voice; be sure to match the voice to the input text.
-   *Audio formats:* The service can produce audio in the following formats: Ogg or Web Media (WebM) format with the Opus (default) or Vorbis codec, MP3 (Motion Picture Experts Group, or MPEG) format, Waveform Audio File Format (WAV), Free Lossless Audio Codec (FLAC), Linear 16-bit Pulse-Code Modulation (PCM), 8-bit mu-law (u-law), or basic audio.

For more information, see [The HTTP REST interface](/docs/services/text-to-speech/http.html).

## WebSocket interface
{: #websocket}

The service offers a WebSocket interface that you can use to synthesize text. The interface provides a single version of the `/v1/synthesize` method. You specify the text to be synthesized, the voice to be used, and the format for the audio. You can provide plain text or text that is annotated with SSML. For more information, see [The WebSocket interface](/docs/services/text-to-speech/websockets.html).

The WebSocket interface also supports use of the SSML `<mark>` element to identify specific locations in the audio, and it allows you to request word timing information for all words of the input text. For more information, see [Obtaining word timings](/docs/services/text-to-speech/word-timing.html).

## Customization interface
{: #customization}

The service includes a customization interface that you can use to create custom voice models for use during speech synthesis. A custom voice model is a dictionary of words and their translations for a specific language. Each word/translation pair in a model tells the service how to pronounce the word when it occurs in input text.

Custom voice models let you provide application-specific translations for unusual words for which the service's regular pronunciation rules may yield imperfect pronunciations. You can define the custom entry for a word/translation pair in the standard International Phonetic Alphabet (IPA) representation or in the proprietary {{site.data.keyword.IBM_notm}} Symbolic Phonetic Representation (SPR).

For example, your application may routinely encounter special terms with foreign origins, personal or geographic names, or abbreviations and acronyms. Customization lets you define translations to tell the service how you want such terms to be pronounced. For more information, see [Understanding customization](/docs/services/text-to-speech/custom-intro.html).

> **Note:** The customization interface is currently a beta release.

## CORS support
{: #cors}

The service supports Cross-Origin Resource Sharing (CORS). CORS lets web clients request resources directly from a foreign domain, avoiding the same-origin security policy, which otherwise prevents such requests. A web page can communicate directly with the service without passing the request through the web server that hosts the page. For example, a web page that is loaded from a server in {{site.data.keyword.Bluemix_notm}} can call the customization API directly, bypassing the {{site.data.keyword.Bluemix_notm}} server. For more information, see [enable-cors.org ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://enable-cors.org/){: new_window}.

## Using Software Development Kits
{: #sdks}

The {{site.data.keyword.texttospeechshort}} service supports a number of SDKs to simplify the development of speech applications. The SDKs are available for many popular programming languages and platforms, including Node.js, Java, Python, and Apple&reg; iOS. For a complete list of SDKs and information about using them, see [{{site.data.keyword.watson}} SDKs](/docs/services/watson/getting-started-sdks.html). All SDKs are available from the [watson-developer-cloud namespace ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://github.com/watson-developer-cloud){: new_window} on GitHub.

The service also makes available the following sample applications to help you get started:

-   You can access an application that uses the Node.js SDK at the [text-to-speech-nodejs repository ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://github.com/watson-developer-cloud/text-to-speech-nodejs){: new_window}.
-   You can access an application that uses the Java SDK at the [text-to-speech-java repository ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://github.com/watson-developer-cloud/text-to-speech-java){: new_window}.

For mobile development, see the [{{site.data.keyword.watson}} Developer Cloud Swift SDK ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://github.com/watson-developer-cloud/swift-sdk){: new_window} and the [{{site.data.keyword.watson}} Speech Android SDK ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://github.com/watson-developer-cloud/speech-android-sdk){: new_window}.

## Learning more about application development
{: #learn}

Like all {{site.data.keyword.watson}} services, the {{site.data.keyword.texttospeechshort}} service supports two typical programming models: *Direct interaction*, in which the client communicates with the service directly; and *relaying via a proxy*, in which the client and service exchange all data (requests and results) through a proxy application that resides in {{site.data.keyword.Bluemix_notm}}. With the HTTP interface, you can use either programming model; with the WebSocket interface, you must use direct communication.

For more information about working with {{site.data.keyword.watson}} Developer Cloud services and {{site.data.keyword.Bluemix_notm}}, see the following:

-   For an introduction to working with {{site.data.keyword.watson}} services and {{site.data.keyword.Bluemix_notm}}, see [Getting started with {{site.data.keyword.watson}} and {{site.data.keyword.Bluemix_notm}}](/docs/services/watson/index.html).
-   For a language-independent introduction to developing {{site.data.keyword.watson}} services applications in {{site.data.keyword.Bluemix_notm}}, see [{{site.data.keyword.Bluemix_notm}} development approaches](/docs/services/watson/getting-started-bluemix.html).
-   For information about the two programming models available for developing {{site.data.keyword.watson}} applications, see [Programming models for {{site.data.keyword.watson}} services](/docs/services/watson/getting-started-develop.html):
    -   With relaying via a proxy, the client relies on a proxy server that resides in {{site.data.keyword.Bluemix_notm}} to communicate with the service; it passes all requests through the proxy application. Relaying requests via a proxy relies only on service credentials to authenticate with the service; see [Service credentials for {{site.data.keyword.watson}} services](/docs/services/watson/getting-started-credentials.html).
    -   With direct interaction, the client uses the proxy application in {{site.data.keyword.Bluemix_notm}} only to obtain an authentication token for the service, after which it communicates directly with the service. Direct interaction uses service credentials only to obtain a token; see [Tokens for authentication](/docs/services/watson/getting-started-tokens.html).
-   For information about controlling the default request logging that is performed for all {{site.data.keyword.watson}} services, see [Controlling request logging for {{site.data.keyword.watson}} services](/docs/services/watson/getting-started-logging.html).
