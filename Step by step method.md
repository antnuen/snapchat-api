# An Nguyen - API Support Engineer Technical Test

## **Part 1:** Steps to obtaining the neccessary credentials for making Snapchat Marketing API requests:
1. Create a Snapchat Business Account at https://ads.snapchat.com/ and create a new Organization

2. Set up an OAuth app with App name, Snap redirect URI, Snap client ID, Snap client secret code

3. Authorize new user to make API requests via browser: 
```
https://accounts.snapchat.com/login/oauth2/authorize?client_id=bf0f0cf6-9f8a-48c4-ab8b-1dd1bde4f29c&redirect_uri=https://test.animalfarm.com/callback&response_type=code&scope=snapchat-marketing-api
```

4. Authorise the new user via browser pop-up

5. Obtain the "code" query parameter in the redirect weblink:
```
https://test.animalfarm.com/callback?code=yJhqNgyaLKGJzb1tF1kcuWAA1Xqaqvl12vpV0qkjH-4
```

6. Exchange "code" for access token + refresh token via cURL in Postman:
```
curl -X POST -d "code=yJhqNgyaLKGJzb1tF1kcuWAA1Xqaqvl12vpV0qkjH-4" -d "client_id=bf0f0cf6-9f8a-48c4-ab8b-1dd1bde4f29c" -d "client_secret=4b6ecb819bb5b8b7b0bd" -d "grant_type=authorization_code" -d "redirect_uri=redirect_uri" https://accounts.snapchat.com/login/oauth2/access_token
```
Result:
```
{
	"access_token": "eyJpc3MiOiJodHRwczpcL1wvYWNjb3VudHMuc25hcGNoYXQuY29tXC9hY2NvdW50c1wvb2F1dGgyXC90b2tlbiIsInR5cCI6IkpXVCIsImVuYyI6IkExMjhDQkMtSFMyNTYiLCJhbGciOiJkaXIiLCJraWQiOiJhY2Nlc3MtdG9rZW4tYTEyOGNiYy1oczI1Ni4wIn0..wbazD1TepoLMhzN_pXcWqQ.fI90jxzhwvhip747gkKmI5lP7-62KR3vl3rDDPH3vtC4DaDCvM84Xsr6QO_wnh7h3IFgtC9hShB4CETaeTEApmt11ALWPhhy9DsqteDt0jgR7XRHbpQbEbXXSUWVAeNDKhBuKnhXUrs_hBC4QgZ1RH4ZM-tOETG3dZ95CZJunBhHlmM7eTz2UR4hBzDEy_RyDWMsQHZ-s1-_4g0tLVvHpAxTXorAGl8eZQ0lSZI6WqozHk5_R9WQxm4oMTXI7R2CvfZeKNw5itsv-edoCteBIr93SeCVgEXiwk-tngMQfBQJZ8kvQ05D5Xb8qq_zz2w8-VZTDr4mSVuk3sKplMnVP5hhgSEUbxFZwaYjOJfuMNrbjqbpDmUJ5Rd6ovvXe-jYiC6hcFVoz8QsUblP90wTuH12H6vTcJf_hhrRyXUgRBCFAXoVdtISs9htgoVJKUYGQ28UQ_G6h9DaS_jrKwJu6y2vNCGR8xVfIQYPcn5Z1i_cHRn1nAt5fHfmGpSW6KWR3MSX10XbMmzhpQn2g-wU9i8D748ZDVZT3A3ib0iA08aepyFryvSWQWkZz59KAeBPdM88EFBVnph9CS6hO8acVPjz4_19hlj6Zq9zNlzluRcLbjf4Y8mMTBQCCKDm3gC8D8kiT9fJokZovScpSU6TH0Xp5OSBlTgcqefJm4luxx9nO_AtXu8XpZ7E4OrMjPLsghD71UlSGK77MZ_sxg3XTy2Dru59VPp9MRUPRDH8NVw.2-SGPjogf6K_279YI1hbMw",
	"token_type": "Bearer",
	"expires_in": 3600,
	"refresh_token": "eyJraWQiOiJyZWZyZXNoLXRva2VuLWExMjhnY20uMCIsInR5cCI6IkpXVCIsImVuYyI6IkExMjhHQ00iLCJhbGciOiJkaXIifQ..YnYSk_FIeCtqWfmW.hWJpJ2LyBWBwKaJ5ZBRbifDKDavNar7PSwLbdR9GbaZi4DiA7zZFYJWSxEOJRmGksg1HMDOp-nxST9m2jNvXTJk_X7W0whmxez1yKkGktMI-DeeUfhWv-DJQDol7DD3n0X8bz7h3TTmppceDoPERdBFuJeVqSz9H0ncE-UsteTE2QkMe2lS1l6RhzRyaTcINO5e_LM5WvNljyayCIGqkzWBFgjXH9WJASa8BeJcOKy8A7SFOLOZv_tNjl62n7WjkMdtB39cRZAbpX-Y.cypj1Rv2FO9o_mcd8dse3g",
	"scope": "snapchat-marketing-api"
}

```

7. Invite Ben Ridley to the Organisation via cURL in Postman::

```
curl -X POST -d '{"members": [{"email": "ben.ridley@kleene.ai","organization_id": "86dbe41d-0c40-4c06-ae4c-01bcb979df2d","display_name": "Ben Ridley"}]}' -H "Content-Type: application/json" -H "Authorization: Bearer eyJpc3MiOiJodHRwczpcL1wvYWNjb3VudHMuc25hcGNoYXQuY29tXC9hY2NvdW50c1wvb2F1dGgyXC90b2tlbiIsInR5cCI6IkpXVCIsImVuYyI6IkExMjhDQkMtSFMyNTYiLCJhbGciOiJkaXIiLCJraWQiOiJhY2Nlc3MtdG9rZW4tYTEyOGNiYy1oczI1Ni4wIn0..wbazD1TepoLMhzN_pXcWqQ.fI90jxzhwvhip747gkKmI5lP7-62KR3vl3rDDPH3vtC4DaDCvM84Xsr6QO_wnh7h3IFgtC9hShB4CETaeTEApmt11ALWPhhy9DsqteDt0jgR7XRHbpQbEbXXSUWVAeNDKhBuKnhXUrs_hBC4QgZ1RH4ZM-tOETG3dZ95CZJunBhHlmM7eTz2UR4hBzDEy_RyDWMsQHZ-s1-_4g0tLVvHpAxTXorAGl8eZQ0lSZI6WqozHk5_R9WQxm4oMTXI7R2CvfZeKNw5itsv-edoCteBIr93SeCVgEXiwk-tngMQfBQJZ8kvQ05D5Xb8qq_zz2w8-VZTDr4mSVuk3sKplMnVP5hhgSEUbxFZwaYjOJfuMNrbjqbpDmUJ5Rd6ovvXe-jYiC6hcFVoz8QsUblP90wTuH12H6vTcJf_hhrRyXUgRBCFAXoVdtISs9htgoVJKUYGQ28UQ_G6h9DaS_jrKwJu6y2vNCGR8xVfIQYPcn5Z1i_cHRn1nAt5fHfmGpSW6KWR3MSX10XbMmzhpQn2g-wU9i8D748ZDVZT3A3ib0iA08aepyFryvSWQWkZz59KAeBPdM88EFBVnph9CS6hO8acVPjz4_19hlj6Zq9zNlzluRcLbjf4Y8mMTBQCCKDm3gC8D8kiT9fJokZovScpSU6TH0Xp5OSBlTgcqefJm4luxx9nO_AtXu8XpZ7E4OrMjPLsghD71UlSGK77MZ_sxg3XTy2Dru59VPp9MRUPRDH8NVw.2-SGPjogf6K_279YI1hbMw" https://adsapi.snapchat.com/v1/organizations/86dbe41d-0c40-4c06-ae4c-01bcb979df2d/members

```

8. Get all Members of the current Organization via cURL in Postman::
```
curl "https://adsapi.snapchat.com/v1/organizations/86dbe41d-0c40-4c06-ae4c-01bcb979df2d/members" -H "Authorization: Bearer eyJpc3MiOiJodHRwczpcL1wvYWNjb3VudHMuc25hcGNoYXQuY29tXC9hY2NvdW50c1wvb2F1dGgyXC90b2tlbiIsInR5cCI6IkpXVCIsImVuYyI6IkExMjhDQkMtSFMyNTYiLCJhbGciOiJkaXIiLCJraWQiOiJhY2Nlc3MtdG9rZW4tYTEyOGNiYy1oczI1Ni4wIn0..wbazD1TepoLMhzN_pXcWqQ.fI90jxzhwvhip747gkKmI5lP7-62KR3vl3rDDPH3vtC4DaDCvM84Xsr6QO_wnh7h3IFgtC9hShB4CETaeTEApmt11ALWPhhy9DsqteDt0jgR7XRHbpQbEbXXSUWVAeNDKhBuKnhXUrs_hBC4QgZ1RH4ZM-tOETG3dZ95CZJunBhHlmM7eTz2UR4hBzDEy_RyDWMsQHZ-s1-_4g0tLVvHpAxTXorAGl8eZQ0lSZI6WqozHk5_R9WQxm4oMTXI7R2CvfZeKNw5itsv-edoCteBIr93SeCVgEXiwk-tngMQfBQJZ8kvQ05D5Xb8qq_zz2w8-VZTDr4mSVuk3sKplMnVP5hhgSEUbxFZwaYjOJfuMNrbjqbpDmUJ5Rd6ovvXe-jYiC6hcFVoz8QsUblP90wTuH12H6vTcJf_hhrRyXUgRBCFAXoVdtISs9htgoVJKUYGQ28UQ_G6h9DaS_jrKwJu6y2vNCGR8xVfIQYPcn5Z1i_cHRn1nAt5fHfmGpSW6KWR3MSX10XbMmzhpQn2g-wU9i8D748ZDVZT3A3ib0iA08aepyFryvSWQWkZz59KAeBPdM88EFBVnph9CS6hO8acVPjz4_19hlj6Zq9zNlzluRcLbjf4Y8mMTBQCCKDm3gC8D8kiT9fJokZovScpSU6TH0Xp5OSBlTgcqefJm4luxx9nO_AtXu8XpZ7E4OrMjPLsghD71UlSGK77MZ_sxg3XTy2Dru59VPp9MRUPRDH8NVw.2-SGPjogf6K_279YI1hbMw"

```
Result:
```
{
	"request_status": "SUCCESS",
	"request_id": "ac428fd9-a03b-4620-b125-bb583e5e94a7",
	"members": [
		{
			"sub_request_status": "SUCCESS",
			"member": {
				"id": "177f686d-d3c4-4f87-a287-d3dc1e6056f9",
				"updated_at": "2023-06-15T19:07:01.441Z",
				"created_at": "2023-06-15T19:07:01.441Z",
				"email": "antnuen@gmail.com",
				"organization_id": "86dbe41d-0c40-4c06-ae4c-01bcb979df2d",
				"display_name": "An Nguyen",
				"snapchat_username": "antnuen",
				"member_status": "MEMBER"
			}
		},
		{
			"sub_request_status": "SUCCESS",
			"member": {
				"id": "e2b218a7-20bd-45ee-b04d-773b7b0cdfee",
				"updated_at": "2023-06-16T20:09:07.608Z",
				"created_at": "2023-06-16T20:09:07.608Z",
				"email": "ben.ridley@kleene.ai",
				"organization_id": "86dbe41d-0c40-4c06-ae4c-01bcb979df2d",
				"display_name": "Ben Ridley",
				"member_status": "INVITED"
			}
		}
	]
}

```
## **Part 2:** Customer Questions
**1. Which requests should be sent to retrieve the data clients are likely to find most valuable?**
Snapchat Marketing API provides a wide range of endpoints, the data clients are likely to find most valuable heavily depend on their business goals and the metrics that are most relevant to their objectives. Generally speaking, the data points clients will find most valuable are:
* Campaign & Ad Insights: Return performance metrics and insights of campaigns, ad accounts and individual ads. These can include data such as impressions, clicks, spend, reach,conversion rates etc. For example, to retrive performance insights of a specific campaign, *v1/campaigns/{campaign_id}/stats?fields=impressions,swipe,spend,conversion_add_cart,conversion_add_cart_swipe_up,conversion_add_cart_view,conversion_purchases,conversion_purchases_swipe_up,conversion_purchases_view*.
* Audience Insights: Returns insights about the audience, such as demographic data, interests, and behaviours. These insights can be obtained through *v1/adaccounts/{ad_account_id}/targeting_insights*. Estimated audience size can also be acquired for ad squads through *v1/adaccounts/{ad_account_id}/audience_size_v2*. 


**2. How can we deal with the tradeoff between usability and flexibility such that users (who lack technical expertise) are easily able to ingest all the data that is relevant for the analysis they will do?**

Some suggestions to strike a balance between usability and flexibility and facilitate easy access and ingestion of relevant data for users without technical expertise:
*  Clear and comprehensive user documentations to help all users navigate the platform. Use of visual aids, clear instructions, and simple workflows can help with the navigation process.
* Responsive support to assist users in any data-related and platform-related queries they might have. 
* Pre-implement data transformation of raw data so users can quickly access and manipulate the data they need even when they are not skilled in coding.

**3. What issues might come up when using the connector and how should we prevent them?**
* Authentication issues: For this particular Snapchat Marketing API, the access token is only valid 1 hour. Users need to ensure the token is valid before sending API requests.
* API updates: Users need to keep abreast of any changes from Snapchat and update their application accordingly by following the API guidelines and monitoring developer announcements. 
* Test, validate, and debug API changes: Before applying any new changes, the application should be tested thoroughly. Postman is a tool that can be used for testing and validating different scenarios to identify potential issues.
* Event deduplication: Check for the Total Deduplication Percentage to prevent the same event from being counted multiple times when it occurs across multiple sources.

