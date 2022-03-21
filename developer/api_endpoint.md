# Endpoints

## Maps

### GET Batches
```
https://stardust.neogoma.com/api/v1/map/batches/:id
```

This endpoint allows the user to get all the mapping data of the map.

<!-- tabs:start -->

#### ** Request **

**Path Parameters**

| Name | Type | Description | Required |
| --- | --- | --- | --- |
| id | string | Your map id | The ID of the Stardust map you want to get data for |

#### ** Response **

**200: OK**

Data successfully retrieved.

**Note**: The quaternion field of the anchor is a json string containing the Quaternion rotation of the anchor.

```js
[
    {
        "created_at": "2022-03-18T06:55:22.000000Z",
        "updated_at": "2022-03-18T06:55:22.000000Z",
        "phone_model": "Google Pixel 6",
        "width": 1920,
        "height": 1080,
        "time": "2022-03-18 06:55:22",
        "anchors": [
            {
                "x": -0.05812509,
                "y": 0.003635053,
                "z": 0.02638943,
                "quaternion": "{\"x\":0.25233352184295657,\"y\":-0.02092771977186203,\"z\":0.013822555541992188,\"w\":0.9673152565956116}",
                "created_at": "2022-03-18T06:55:36.000000Z",
                "updated_at": "2022-03-18T06:55:36.000000Z"
            },
            ...
            ,
            {
                "x": -0.1220546,
                "y": 0.127442,
                "z": -0.03395549,
                "quaternion": "{\"x\":0.08376258611679077,\"y\":-0.169703409075737,\"z\":-0.0076171765103936199,\"w\":0.9818994998931885}",
                "created_at": "2022-03-18T06:55:37.000000Z",
                "updated_at": "2022-03-18T06:55:37.000000Z"
            },
           
        ]
    }
]
```

**400: Bad parameters**

Wrong parameters.

**404: Not found**

Requested ID doesn't match any map.

<!-- tabs:end -->

### GET Exists
```
https://stardust.neogoma.com/api/v1/map/exists/:id
```

This endpoint allows the user to know if a map exists or not.

<!-- tabs:start -->

#### ** Request **

**Path Parameters**

| Name | Type | Description | Required |
| --- | --- | --- | --- |
| id | string | Your map id | The ID of the Stardust map you want to get data for |

#### ** Response **

**200: OK**

Data successfully retrieved.

```
0 if the map doesn't exist
1 otherwise
```
<!-- tabs:end -->



### GET Point Cloud
```
https://stardust.neogoma.com/api/v1/map/point_cloud/:id
```

This endpoint downloads the point cloud of the map on CSV format. (If the map has NO point cloud calculated yet, this endpoint **WILL NOT** work.)

<!-- tabs:start -->

#### ** Request **

**Path Parameters**

| Name | Type | Description | Required |
| --- | --- | --- | --- |
| id | string | Your map id | The ID of the Stardust map you want to get point cloud for |

#### ** Response **

**200: OK**

CSV file containing the list of all the points position and their color. Note that the RGB colors are normalized (between 0 and 1);

```js
x_value y_value z_value red_value_normalized green_value_normalized blue_value_normalized
```

**404: Not found**

The map or the point cloud could not be found

**403: Unauthorized access**

You are trying to access a map that is not yours

<!-- tabs:end -->

### DELETE Delete map
```
https://stardust.neogoma.com/api/v1/map/delete/:id
```

This endpoint allows the user to delete a map.

<!-- tabs:start -->

#### ** Request **

**Path Parameters**

| Name | Type | Description | Required |
| --- | --- | --- | --- |
| id | string | Your map id | The ID of the Stardust map you want to delete |

#### ** Response **

**200: OK**

Map succesfully deleted

**400: Bad parameters**

Wrong parameters.

**404: Not found**

Requested ID doesn't match any map

<!-- tabs:end -->


## Images
