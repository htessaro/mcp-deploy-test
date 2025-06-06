# Cats TypeScript SDK 1.0.0

Welcome to the Cats SDK documentation. This guide will help you get started with integrating and using the Cats SDK in your project.

[![This SDK was generated by liblab](https://public-liblab-readme-assets.s3.us-east-1.amazonaws.com/built-by-liblab-icon.svg)](https://liblab.com/?utm_source=readme)

## Versions

- API version: `1.0.0`
- SDK version: `1.0.0`

## About the API

![cat-api-logo](https://thecatapi.com/_app/immutable/assets/thecatapi-logo.78868573.svg)

## An open, free, read & write API all about Cats

The Cat API gives you access to 10000's of Cat images, and breeds.

- Upload your own Images
- Get detailed info on all Cat Breeds
- Allow your Users to Favourite or Vote on Images
- Save a custom value with each request so you can match data to your Users

## How do i get access?

Just sign up for an API Key from https://thecatapi.com for free. We're looking forward to seeing what you build!
Don't forget to checkout it's sister API - TheDogAPI.com

## Table of Contents

- [Setup & Configuration](#setup--configuration)
  - [Supported Language Versions](#supported-language-versions)
  - [Installation](#installation)
- [Authentication](#authentication)
  - [Access Token Authentication](#access-token-authentication)
- [Setting a Custom Timeout](#setting-a-custom-timeout)
- [Sample Usage](#sample-usage)
- [Services](#services)
- [Models](#models)
- [License](#license)

# Setup & Configuration

## Supported Language Versions

This SDK is compatible with the following versions: `TypeScript >= 4.8.4`

## Installation

To get started with the SDK, we recommend installing using `npm`:

```bash
npm install cats
```

## Authentication

### Access Token Authentication

The Cats API uses an Access Token for authentication.

This token must be provided to authenticate your requests to the API.

#### Setting the Access Token

When you initialize the SDK, you can set the access token as follows:

```ts
const sdk = new Cats({ token: 'YOUR_TOKEN' });
```

If you need to set or update the access token after initializing the SDK, you can use:

```ts
const sdk = new Cats();
sdk.token = 'YOUR_TOKEN';
```

## Setting a Custom Timeout

You can set a custom timeout for the SDK's HTTP requests as follows:

```ts
const cats = new Cats({ timeout: 10000 });
```

# Sample Usage

Below is a comprehensive example demonstrating how to authenticate and call a simple endpoint:

```ts
import { Cats } from 'cats';

(async () => {
  const cats = new Cats({
    token: 'YOUR_TOKEN',
  });

  const { data } = await cats.images.imagesListSearchOrRandom({
    size: 'size',
    mimeTypes: 'mime_types',
    format: 'format',
    hasBreeds: true,
    order: 'order',
    page: 2,
    limit: 9,
    contentType: 'Content-Type',
    xApiKey: 'x-api-key',
  });

  console.log(data);
})();
```

## Services

The SDK provides various services to interact with the API.

<details> 
<summary>Below is a list of all available services with links to their detailed documentation:</summary>

| Name                                                             |
| :--------------------------------------------------------------- |
| [ImagesService](documentation/services/ImagesService.md)         |
| [BreedsService](documentation/services/BreedsService.md)         |
| [FactsService](documentation/services/FactsService.md)           |
| [FavouritesService](documentation/services/FavouritesService.md) |
| [VotesService](documentation/services/VotesService.md)           |
| [WebhooksService](documentation/services/WebhooksService.md)     |

</details>

## Models

The SDK includes several models that represent the data structures used in API requests and responses. These models help in organizing and managing the data efficiently.

<details> 
<summary>Below is a list of all available models with links to their detailed documentation:</summary>

| Name                                                                           | Description |
| :----------------------------------------------------------------------------- | :---------- |
| [CreateImagesUploadRequest](documentation/models/CreateImagesUploadRequest.md) |             |

</details>

## License

This SDK is licensed under the MIT License.

See the [LICENSE](LICENSE) file for more details.

<!-- This file was generated by liblab | https://liblab.com/ -->
