# ImagesService

A list of all methods in the `ImagesService` service. Click on the method name to view detailed information about that method.

| Methods                                                                       | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| :---------------------------------------------------------------------------- | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [imagesListSearchOrRandom](#imageslistsearchorrandom)                         | Searches or returns Random selection from all approved images. Default is to return RANDOM images, but with an API-Key you can use 'order=DESC' or 'order=ASC' along with the 'page' and 'limit' parameters to paginate through them in the order they were approved. Pagination-Count, Pagination-Page, and Pagination-Limit headers are present in the response so you know the total number of images that can be paginated through for the passed search filters. |
| [getImagesBkIEhN3pG](#getimagesbkiehn3pg)                                     | Get the raw analysis results for any uploaded image                                                                                                                                                                                                                                                                                                                                                                                                                   |
| [getImages](#getimages)                                                       | Only returns images from your account, uploaded via 'api/v1/images/upload'                                                                                                                                                                                                                                                                                                                                                                                            |
| [createImagesUpload](#createimagesupload)                                     | Make sure you're using the right field to send the image, and Content-Type header                                                                                                                                                                                                                                                                                                                                                                                     |
| [deleteImagesByImageId](#deleteimagesbyimageid)                               |                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| [getImagesByImageIdBreeds](#getimagesbyimageidbreeds)                         |                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| [createImagesByImageIdBreeds](#createimagesbyimageidbreeds)                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| [deleteImagesByImageIdBreedsByBreedId](#deleteimagesbyimageidbreedsbybreedid) |                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |

## imagesListSearchOrRandom

Searches or returns Random selection from all approved images. Default is to return RANDOM images, but with an API-Key you can use 'order=DESC' or 'order=ASC' along with the 'page' and 'limit' parameters to paginate through them in the order they were approved. Pagination-Count, Pagination-Page, and Pagination-Limit headers are present in the response so you know the total number of images that can be paginated through for the passed search filters.

- HTTP Method: `GET`
- Endpoint: `/images/search`

**Parameters**

| Name        | Type    | Required | Description                                                                                     |
| :---------- | :------ | :------- | :---------------------------------------------------------------------------------------------- |
| size        | string  | ❌       | [optional] thumb , small, med or full - small is perfect for Discord                            |
| mimeTypes   | string  | ❌       | [optional] a comma separated string of types to return e.g. jpg,png for static, or gif for gifs |
| format      | string  | ❌       | [optional] json \| src                                                                          |
| hasBreeds   | boolean | ❌       | [optional] - only return images with breed data                                                 |
| order       | string  | ❌       | [optional] default:RANDOM - RANDOM \| ASC \| DESC                                               |
| page        | number  | ❌       | [optional] paginate through results                                                             |
| limit       | number  | ❌       | [optional] number of results to return, up to 25 with a valid API-Key                           |
| contentType | string  | ❌       |                                                                                                 |
| xApiKey     | string  | ❌       | [optional] without it only the a basic set of images can be searched                            |

**Return Type**

`any`

**Example Usage Code Snippet**

```typescript
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

## getImagesBkIEhN3pG

Get the raw analysis results for any uploaded image

- HTTP Method: `GET`
- Endpoint: `/images/BkIEhN3pG`

**Parameters**

| Name    | Type   | Required | Description                                                 |
| :------ | :----- | :------- | :---------------------------------------------------------- |
| xApiKey | string | ❌       | [optional] will save this request to your account analytics |

**Return Type**

`any`

**Example Usage Code Snippet**

```typescript
import { Cats } from 'cats';

(async () => {
  const cats = new Cats({
    token: 'YOUR_TOKEN',
  });

  const { data } = await cats.images.getImagesBkIEhN3pG({
    xApiKey: 'x-api-key',
  });

  console.log(data);
})();
```

## getImages

Only returns images from your account, uploaded via 'api/v1/images/upload'

- HTTP Method: `GET`
- Endpoint: `/images/`

**Parameters**

| Name        | Type   | Required | Description                                                                                   |
| :---------- | :----- | :------- | :-------------------------------------------------------------------------------------------- |
| xApiKey     | string | ✅       | - will return all the images from your account                                                |
| limit       | number | ❌       | [Optional] number of images to return valid 1 to 10 - default: 1                              |
| page        | number | ❌       | [Optional] only works if account_id is present to page through your own uploads               |
| order       | string | ❌       | [Optional] only works if account_id is present, either ASC or DESC - ascending or descending. |
| contentType | string | ❌       |                                                                                               |

**Return Type**

`any`

**Example Usage Code Snippet**

```typescript
import { Cats } from 'cats';

(async () => {
  const cats = new Cats({
    token: 'YOUR_TOKEN',
  });

  const { data } = await cats.images.getImages({
    limit: 8,
    page: 2,
    order: 'order',
    contentType: 'Content-Type',
    xApiKey: 'x-api-key',
  });

  console.log(data);
})();
```

## createImagesUpload

Make sure you're using the right field to send the image, and Content-Type header

- HTTP Method: `POST`
- Endpoint: `/images/upload`

**Parameters**

| Name        | Type                                                                | Required | Description                                 |
| :---------- | :------------------------------------------------------------------ | :------- | :------------------------------------------ |
| body        | [CreateImagesUploadRequest](../models/CreateImagesUploadRequest.md) | ❌       | The request body.                           |
| xApiKey     | string                                                              | ✅       | - saves the uploaded image to your account. |
| contentType | string                                                              | ❌       |                                             |

**Return Type**

`any`

**Example Usage Code Snippet**

```typescript
import { Cats, CreateImagesUploadRequest } from 'cats';

(async () => {
  const cats = new Cats({
    token: 'YOUR_TOKEN',
  });

  const createImagesUploadRequest: CreateImagesUploadRequest = {
    file: new ArrayBuffer(0),
    subId: 'sub_id',
    breedIds: 'breed_ids',
  };

  const { data } = await cats.images.createImagesUpload(createImagesUploadRequest, {
    contentType: 'Content-Type',
    xApiKey: 'x-api-key',
  });

  console.log(data);
})();
```

## deleteImagesByImageId

- HTTP Method: `DELETE`
- Endpoint: `/images/{image_id}`

**Parameters**

| Name        | Type   | Required | Description |
| :---------- | :----- | :------- | :---------- |
| imageId     | string | ✅       |             |
| contentType | string | ❌       |             |
| xApiKey     | string | ❌       |             |

**Return Type**

`any`

**Example Usage Code Snippet**

```typescript
import { Cats } from 'cats';

(async () => {
  const cats = new Cats({
    token: 'YOUR_TOKEN',
  });

  const { data } = await cats.images.deleteImagesByImageId('image_id', {
    contentType: 'Content-Type',
    xApiKey: 'x-api-key',
  });

  console.log(data);
})();
```

## getImagesByImageIdBreeds

- HTTP Method: `GET`
- Endpoint: `/images/{image_id}/breeds`

**Parameters**

| Name        | Type   | Required | Description |
| :---------- | :----- | :------- | :---------- |
| imageId     | string | ✅       |             |
| contentType | string | ❌       |             |

**Return Type**

`any`

**Example Usage Code Snippet**

```typescript
import { Cats } from 'cats';

(async () => {
  const cats = new Cats({
    token: 'YOUR_TOKEN',
  });

  const { data } = await cats.images.getImagesByImageIdBreeds('image_id', {
    contentType: 'Content-Type',
  });

  console.log(data);
})();
```

## createImagesByImageIdBreeds

- HTTP Method: `POST`
- Endpoint: `/images/{image_id}/breeds`

**Parameters**

| Name        | Type   | Required | Description                                              |
| :---------- | :----- | :------- | :------------------------------------------------------- |
| body        | any    | ❌       | The request body.                                        |
| imageId     | string | ✅       |                                                          |
| xApiKey     | string | ✅       | - for now, you can only tag your own images with a breed |
| contentType | string | ❌       |                                                          |

**Return Type**

`any`

**Example Usage Code Snippet**

```typescript
import { Cats } from 'cats';

(async () => {
  const cats = new Cats({
    token: 'YOUR_TOKEN',
  });

  const input = {};

  const { data } = await cats.images.createImagesByImageIdBreeds('image_id', {
    contentType: 'Content-Type',
    xApiKey: 'x-api-key',
  });

  console.log(data);
})();
```

## deleteImagesByImageIdBreedsByBreedId

- HTTP Method: `DELETE`
- Endpoint: `/images/{image_id}/breeds/{breed_id}`

**Parameters**

| Name        | Type   | Required | Description                                   |
| :---------- | :----- | :------- | :-------------------------------------------- |
| imageId     | string | ✅       |                                               |
| breedId     | string | ✅       |                                               |
| xApiKey     | string | ✅       | - only you can delete breeds from your images |
| contentType | string | ❌       |                                               |

**Return Type**

`any`

**Example Usage Code Snippet**

```typescript
import { Cats } from 'cats';

(async () => {
  const cats = new Cats({
    token: 'YOUR_TOKEN',
  });

  const { data } = await cats.images.deleteImagesByImageIdBreedsByBreedId('image_id', 'breed_id', {
    contentType: 'Content-Type',
    xApiKey: 'x-api-key',
  });

  console.log(data);
})();
```

<!-- This file was generated by liblab | https://liblab.com/ -->
