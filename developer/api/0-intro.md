# Intro

First of all in order to use the API endpoints you need to use a paid plan. If you didn't subscribe a paid plan yet, you can do it [here](https://stardust.neogoma.com/pricing).

## Headers
The follwing headers need to be setup to authenticate your account on the request. You can find your token [here](https://stardust.neogoma.com/profile).

| Name | Value |
| --- | --- |
| Authorization | "Bearer "+[API KEY] |

If you don't provide the token or you try to access data that are not yours you trigger a 403 forbidden error.