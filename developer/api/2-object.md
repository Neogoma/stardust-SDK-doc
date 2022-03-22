# Images Endpoints

## POST Create image
```
https://stardust.neogoma.com/api/v1/object/image
```

This endpoint allows the user to create an image.

<!-- tabs:start -->

### ** Request **

**Path Parameters**

| Name | Type | Description | Required |
| --- | --- | --- | --- |
| name | string | Name of the image you want to create | YES |
| image_url | url | Url of the image you want to use (example: https://neogoma.com/images/logoneogoma.png) | YES |

### ** Response **

**200: OK**

```js
{
    "status": 200,
    "data": "ID of the new object"
}
```

**400: Bad request**

Wrong parameters.
```js
//If your image_url is not in the URL format
{
    "status": 400,
    "data": {
        "image_url": [
            "The image url format is invalid."
        ]
    }
}
```

<!-- tabs:end -->

## POST Update image
```
https://stardust.neogoma.com/api/v1/object/image/update
```

This endpoint allows the user to update an image.

<!-- tabs:start -->

### ** Request **

**Path Parameters**

| Name | Type | Description | Required |
| --- | --- | --- | --- |
| id | string | ID of the image you want to update | YES |
| name | string | Name of the image you want to create | OPTIONAL |
| image_url | url | Url of the image you want to use (example: https://neogoma.com/images/logoneogoma.png) | OPTIONAL |

### ** Response **

**200: OK**

Image updated

```js
{
    "status": 200,
    "data": "OK"
}
```

**400: Bad request**

Wrong parameters.

```js
//If your image_url is not in URL format
{
    "status": 400,
    "data": {
        "image_url": [
            "The image url format is invalid."
        ]
    }
}
```

<!-- tabs:end -->

## DELETE Delete image
```
https://stardust.neogoma.com/api/v1/object/image/:id
```

This endpoint allows the user to delete an image.

<!-- tabs:start -->

### ** Request **

**Path Parameters**

| Name | Type | Description | Required |
| --- | --- | --- | --- |
| id | string | ID of the image you want to delete | YES |

### ** Response **

**200: OK**

Image deleted.
```js
{
    "status": 200,
    "data": "OK"
}
```

**404: Not found**

Image not found

```js
{
    "status": 404,
    "data": "Image not found"
}
```

<!-- tabs:end -->