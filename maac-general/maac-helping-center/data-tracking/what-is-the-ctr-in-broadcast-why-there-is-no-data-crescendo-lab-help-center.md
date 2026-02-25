# What is the CTR in Broadcast? Why there is no data? – Crescendo Lab Help Center

According to different purchase plans, our Broadcast shows different data that can be recorded.

Please refer to the instructions below. If the broadcast you push is not in the following types, the data will not be displayed.

On 2022/10/05, we optimized the system for the number of clicks, reduced the time cost of operation on MAAC, and added the number of repeated clicks and unique clicks at the same time, so that you can accurately analyze the performance brought by each push message.

#### ▶︎ Applicable to MAAC Basic plan

【 Before optimization 】You had to first go to "Tracelink" and put it in the broadcast before you could track the click results.

【 After optimization 】Now you can directly put links and texts in the editor of Broadcast, MAAC will automatically convert the links into MAAC short links and track the number of repeated clicks.

{% stepper %}
{% step %}
### Trigger auto-reply (repeated clicks)

This type of broadcast is tracked as repeated clicks.
{% endstep %}

{% step %}
### An image that is set to pop up a text message when users click it (repeated clicks)

This type of broadcast is tracked as repeated clicks.
{% endstep %}

{% step %}
### Link clicks (repeated clicks)

This type of broadcast is tracked as repeated clicks.
{% endstep %}
{% endstepper %}

* From 2022/10/05, you don't need to go to the "Tracelink" to forward and then put it into Broadcast; you can now directly see the click results in the broadcast list.

#### ▶︎ Applicable to MAAC EC-Plan (need to be connected in series with UA/GA4)

When broadcasting, as in the past, you can put links and texts in the editor. After sending, MAAC will not only capture the information of unique clicks but also add tracking of repeated clicks.

{% stepper %}
{% step %}
### Trigger auto-reply (repeated clicks)

This type of broadcast is tracked as repeated clicks.
{% endstep %}

{% step %}
### An image that is set to pop up a text message when users click it (repeated clicks)

This type of broadcast is tracked as repeated clicks.
{% endstep %}

{% step %}
### A domain link that is in line with GA and has clicks for UTM

This type of broadcast is tracked and supports UTM-based unique click measurement.
{% endstep %}
{% endstepper %}

* Before 15:00, 2022/10/05, there were only unique clicks.
* From 15:00, 10/05/2022, the number of unique clicks and repeated clicks can be calculated at the same time (no need to go to the "Tracelink" to track the number of repeated clicks!).

📚 Review： [Tutorials｜Broadcast - Open counts, Segment - Retargeting](https://crescendolab.zendesk.com/hc/en-us/articles/4413211963417)

#### FAQ

<details>

<summary>For MAAC Basic plan — After optimization, although we don't need to shorten the link in "Tracklink", the click results of all URLs in the same push will be counted together. What should we do if we want to see the results of each link separately?</summary>

A：After optimization, it is more convenient for users. You can track the click-through rate of the entire broadcast without track link forwarding. However, if you want to see the results of different links separately, please go back to "Tracklink", come back and put the link into the broadcast.

</details>

<details>

<summary>Customers who purchase e-commerce functions — Originally there was data on the click-through rate(CTR), but after the optimization on 2022/10/05, why did the old broadcast have both repeated CTR and unique CTR?</summary>

A：In the old push, there were both "a text message pops up after clicking" and "a link with a UTM setting", so the effect of "a text message pops up after clicking" will be classified as a repeated click rate, and "with a setting" UTM Links" would be classified as unique CTR.

</details>

### Related articles

* [Tutorials｜Broadcast - Open counts, Segment - Retargeting](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCBlw7ocDBDoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCBkCt4gDBDoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJZL2hjL2VuLXVzL2FydGljbGVzLzQ0MTMyMTE5NjM0MTctVHV0b3JpYWxzLUJyb2FkY2FzdC1PcGVuLWNvdW50cy1TZWdtZW50LVJldGFyZ2V0aW5nBjsIVDoJcmFua2kG--5142563beb5ee7d921ea5489d850632dddbbabd9)
* [SMS Broadcast](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCJnlSWCkGDoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCBkCt4gDBDoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSI0L2hjL2VuLXVzL2FydGljbGVzLzI3MDk0MjY5MTU4ODA5LVNNUy1Ccm9hZGNhc3QGOwhUOglyYW5raQc%3D--e542c116624f45a1f151a968b311eb9cbdd88588)
* [Tutorials｜BigQuery Connector](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCBlyQwxwFjoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCBkCt4gDBDoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJDL2hjL2VuLXVzL2FydGljbGVzLzI0NjcwNDk3ODk0OTM3LVR1dG9yaWFscy1CaWdRdWVyeS1Db25uZWN0b3IGOwhUOglyYW5raQg%3D--682293c79c43c44ae706d392ff4dd224de3c2e39)
* [MAAC Feature Report Update Time and Frequency](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCBk118UDBDoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCBkCt4gDBDoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJTL2hjL2VuLXVzL2FydGljbGVzLzQ0MTQyNTA2MjgzNzctTUFBQy1GZWF0dXJlLVJlcG9ydC1VcGRhdGUtVGltZS1hbmQtRnJlcXVlbmN5BjsIVDoJcmFua2kJ--d532b6b5e9bbb609f8953d2785cf83ed69317e06)
* [Tutorial｜CAAC x CDH - Profile Unification](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCJl%2FlyruHDoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCBkCt4gDBDoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJOL2hjL2VuLXVzL2FydGljbGVzLzMxODA5MjQyMzY1ODQ5LVR1dG9yaWFsLUNBQUMteC1DREgtUHJvZmlsZS1VbmlmaWNhdGlvbgY7CFQ6CXJhbmtpCg%3D%3D--6cf111eb2690b7b805cde52b56ba55534241a902)
