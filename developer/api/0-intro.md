# Intro

First of all, in order to use the API endpoints, you need to use a paid plan. If you haven't subscribed to a paid plan yet, you can do it [here](https://stardust.neogoma.com/pricing).

## Headers
The following headers need to be setup to authenticate your account in the request. You can find your API token [here](https://stardust.neogoma.com/profile).

| Name | Value |
| --- | --- |
| Authorization | "Bearer "+[API KEY] |

If you don't provide the token or you try to access data that are not yours, a HTTP 403 forbidden error will be returned in the response.