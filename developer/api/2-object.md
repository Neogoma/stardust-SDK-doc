# Images Endpoints

### POST Create image
```
https://stardust.neogoma.com/api/v1/object/image
```

This endpoint allows the user to delete a map.

<!-- tabs:start -->

#### ** Request **

**Path Parameters**

| Name | Type | Description | Required |
| --- | --- | --- | --- |
| name | string | Name of the image you want to create | YES |
| image_url | url | Url of the image you want to use (example: https://neogoma.com/images/logoneogoma.png) | YES |

#### ** Response **

**200: OK**

```js
{
    "status": 200,
    "data": "ID of the new object"
}
```

**400: Bad request**

Wrong parameters.
<!-- tabs:end -->