# Tutorial｜SSO - Single Sign On – Crescendo Lab Help Center

Created Mar 19, 2024 — Created By: Crescender Lab

***

## Advanced

* Crescendo Lab proudly announces its attainment of ISO 27001 certification in 2024.
* We can integrate your Identity Provider (IdP) to support Single Sign-on (SSO) authentication for logging into the Crescendo Lab products.
* Providing a more secure product usage environment.

***

## To help you integrate your existing SSO (Single Sign-On) system with our platform

Please first confirm which protocol your SSO system uses:

* **SAML** (Security Assertion Markup Language)
* **OIDC** (OpenID Connect, also known as OAuth 2.0 with OpenID)

If you are using **SAML**, please provide:

* Single Sign-On URL
* Audience URI (i.e., SP Entity ID)
* IdP Entity ID (Identity Provider Identifier)
* X.509 Certificate (used to verify the signature)
* Email Domain (domain used for login)

If you are using **OIDC (OpenID Connect)**, please provide:

* Client ID
* Client Secret
* Issuer URL (authentication server URL)
* Email Domain (domain used for login)

***

## How to login with SSO on MAAC

{% stepper %}
{% step %}
### Click on Sign in with SSO on MAAC

![Click on Sign in with SSO on MAAC](<../../../.gitbook/assets/ea6b3ce7 ab6c 4202 857f 6a548d50eb55.png>)
{% endstep %}

{% step %}
### Enter the mail domain configured for the SSO

![Enter the mail domain configured for the SSO.](<../../../.gitbook/assets/f36f2f73 0851 4b18 9fbc 6bd5b5c4a9b5.png>)
{% endstep %}

{% step %}
### Click on Continue

![Click on Continue](<../../../.gitbook/assets/ebb89246 3d99 43a0 964d 11cb810df12a.png>)
{% endstep %}

{% step %}
### Permission management

To invite a new MAAC user, go to Permission management.

![Click on Permission management](<../../../.gitbook/assets/96c3947c c230 4259 9d7d 3ecbefa11b9d.png>)
{% endstep %}

{% step %}
### Add user

![Click on Add user](<../../../.gitbook/assets/43ff733a baf0 49f1 a82c 56e470d093de.png>)
{% endstep %}
{% endstepper %}

{% hint style="info" %}
The initial login page will redirect to the brand's SSO configuration page. Please follow the instructions to log in.
{% endhint %}

Related tutorial: [How to add MAAC users ?](https://crescendolab.zendesk.com/hc/en-us/articles/36359736768281-Tutorials-How-to-add-MAAC-users)

***

## How to login with SSO on CAAC

{% stepper %}
{% step %}
### Open CAAC SSO login

![](<../../../.gitbook/assets/0a4ac63a c1fd 4de2 a1a8 88dddf7ab68c.png>)
{% endstep %}

{% step %}
### Enter the mail domain configured for the SSO

![Enter the mail domain configured for the SSO.](<../../../.gitbook/assets/d01dac99 7d82 4500 9124 850688a451f5.png>)
{% endstep %}

{% step %}
### Click on Continue

![Click on Continue](<../../../.gitbook/assets/6b16d91e 4bd7 4e71 9c08 4649d648f193.png>)
{% endstep %}

{% step %}
### Open Organization settings

Go to Setting > Organization settings.

![Click on Setting > Organization settings](<../../../.gitbook/assets/902fab69 987f 414c 9725 ddc49bf0ca07.png>)
{% endstep %}

{% step %}
### People > Add

Click on People > Add to invite new users.

![Click on People > Add](<../../../.gitbook/assets/5c3f960a 8d36 410f b55f 5b48dfd4c823.png>)
{% endstep %}
{% endstepper %}

{% hint style="info" %}
The initial login page will redirect to the brand's SSO configuration page. Please follow the instructions to log in.
{% endhint %}

Related tutorial: [CAAC Team Management](https://crescendolab.zendesk.com/hc/en-us/articles/17559997074713-Tutorials-CAAC-Team-Management)\
If you try to use CAAC App to login with SSO, please refer to: [CAAC App Notification Settings & Login Instructions](https://crescendolab.zendesk.com/hc/en-us/articles/43739120905497-Tutorials-CAAC-App-Notification-Settings-Login-Instructions#h_01JTSZX07RA8WGQF75SR7RSE5A)

***

Created with Tango.us

***

Related articles

* Why can't I login to MAAC? Why does the MAAC function page not display properly?\
  https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCJnsaTjYBDoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCBnkW7deGzoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJ0L2hjL2VuLXVzL2FydGljbGVzLzUzMjY3MDU5MTI5ODUtV2h5LWNhbi10LUktbG9naW4tdG8tTUFBQy1XaHktZG9lcy10aGUtTUFBQy1mdW5jdGlvbi1wYWdlLW5vdC1kaXNwbGF5LXByb3Blcmx5BjsIVDoJcmFua2kG--74f57041948e0ecea6a71ae6dc7ec277b7c8f527
* Integration of MAAC and CAAC Customer(Contact) Data - Customer data hub\
  https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCJk12ZpvEjoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCBnkW7deGzoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJ1L2hjL2VuLXVzL2FydGljbGVzLzIwMjcwNTQ4NTk2MTIxLVR1dG9yaWFscy1JbnRlZ3JhdGlvbi1vZi1NQUFDLWFuZC1DQUFDLUN1c3RvbWVyLUNvbnRhY3QtRGF0YS1DdXN0b21lci1kYXRhLWh1YgY7CFQ6CXJhbmtpBw%3D%3D--535215bab1906f9ff1befcd8bf32179b83f3ce23
* CAAC Users\
  https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCJnaVfz6BjoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCBnkW7deGzoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSI6L2hjL2VuLXVzL2FydGljbGVzLzc2NzUwNDUwNzU2MDktVHV0b3JpYWxzLUNBQUMtVXNlcnMGOwhUOglyYW5raQg%3D--0222b9038da127fdf5c8f5b2bf64f4c32812305c
* Billing Dashboard ✨\
  https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCBmDOrxoGzoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCBnkW7deGzoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJBL2hjL2VuLXVzL2FydGljbGVzLzMwMTM2NjQ4NDk5OTkzLVR1dG9yaWFsLUJpbGxpbmctRGFzaGJvYXJkBjsIVDoJcmFua2kJ--8094c66c3dbcd62eb6eca81f2125f675b70725ab
* CAAC Assignment's Types & Ways, and FAQs\
  https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCBlkZASjDDoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCBnkW7deGzoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJVL2hjL2VuLXVzL2FydGljbGVzLzEzODk0MjkyODkwNjQ5LVR1dG9yaWFsLUNBQUMtQXNzaWdubWVudC1zLVR5cGVzLVdheXMtYW5kLUZBUXMGOwhUOglyYW5raQo%3D--afc46d3ede34914fca87fc307ea41bd66963cd8f
