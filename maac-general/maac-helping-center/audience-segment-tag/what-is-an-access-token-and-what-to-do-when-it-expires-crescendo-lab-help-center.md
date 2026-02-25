# What is an Access Token and What to Do When It Expires? – Crescendo Lab Help Center

#### What is an Access Token?

<details>

<summary>An Access Token is essentially a pass required for a program to perform actions that need authorization from another program.</summary>

When a program needs to make an authorized request, it must first obtain an Access Token from the other program. This token, which is a string of alphanumeric characters, is then included in the request to ensure it is accepted.

</details>

#### What to Do When Your LINE Access Token Expires?

<details>

<summary>If the Access Token issued by LINE to MAAC has expired, contact Crescendo Lab to refresh it.</summary>

MAAC frequently needs to make authorized requests to LINE for various operations such as data transmission, push notifications, and running rich menus. Without a valid token, many MAAC functions will be affected.

</details>

#### What to Do When Your MAAC API Token Expires?

<details>

<summary>If your MAAC Open API token is about to expire, contact Crescendo Lab to extend its validity.</summary>

If you have purchased the MAAC Open API, you will also need a token for making authorized requests or actions such as push notifications. If you receive a system notification that your API token is about to expire, you need to contact Crescendo Lab to extend the token’s validity. Otherwise, functions related to the MAAC Open API will be impacted.

</details>

#### Why Does the LINE Access Token Frequently Expire?

<details>

<summary>LINE limits the number of Access Tokens that can be issued; when exceeded, older tokens expire.</summary>

Crescendo Lab has designed a mechanism to automatically refresh the Access Token one day before its expiration. If your Access Token frequently expires, check the following possible causes:

</details>

{% stepper %}
{% step %}
### Internal use

Whether other IT personnel within your organization are using the token.
{% endstep %}

{% step %}
### Other vendors

Whether current or previous LINE API vendors have mechanisms that request tokens excessively or have not stopped requesting tokens.
{% endstep %}
{% endstepper %}

You should coordinate with relevant internal and external personnel to address the token request mechanism.

### Related articles

* [Why Are the Pre-set Auto-reply and Rich Menu Not Working?](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCJletogDBDoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCBljCasDBDoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJeL2hjL2VuLXVzL2FydGljbGVzLzQ0MTMyMjUwNjYxMzctV2h5LUFyZS10aGUtUHJlLXNldC1BdXRvLXJlcGx5LWFuZC1SaWNoLU1lbnUtTm90LVdvcmtpbmcGOwhUOglyYW5raQY%3D--597c466adf1ffb51c1cfd94edc381ed334754481)
* [How to share LINE OA platform, LINE Developers, GA(UA) / GA4 access to Crescendo Lab?](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCJmp1FFgBzoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCBljCasDBDoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJ1L2hjL2VuLXVzL2FydGljbGVzLzgxMTAyNzExNDYzOTMtSG93LXRvLXNoYXJlLUxJTkUtT0EtcGxhdGZvcm0tTElORS1EZXZlbG9wZXJzLUdBLVVBLUdBNC1hY2Nlc3MtdG8tQ3Jlc2NlbmRvLUxhYgY7CFQ6CXJhbmtpBw%3D%3D--0d9bc7ea8bd21d12beaab8defacd7a29783fc293)
* [Tutorials｜Webhook](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCJnyT08EBDoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCBljCasDBDoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSI3L2hjL2VuLXVzL2FydGljbGVzLzQ0MTY1NTcwMTk4MDEtVHV0b3JpYWxzLVdlYmhvb2sGOwhUOglyYW5raQg%3D--9160f729ded921531c9fd26d947f6378fbb8f810)
* [Why there are no friends in the MAAC when I finish the connection ?](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCBm%2BDMgDBDoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCBljCasDBDoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJnL2hjL2VuLXVzL2FydGljbGVzLzQ0MTQyODc2OTEyODktV2h5LXRoZXJlLWFyZS1uby1mcmllbmRzLWluLXRoZS1NQUFDLXdoZW4tSS1maW5pc2gtdGhlLWNvbm5lY3Rpb24GOwhUOglyYW5raQk%3D--a99684c92ee41d806e2bccf2b8351478cc92c17a)
* [Tutorials｜CAAC Users](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCJnaVfz6BjoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCBljCasDBDoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSI6L2hjL2VuLXVzL2FydGljbGVzLzc2NzUwNDUwNzU2MDktVHV0b3JpYWxzLUNBQUMtVXNlcnMGOwhUOglyYW5raQo%3D--48c1d0f6dd6068fd724a05fce02b8999265d974c)
