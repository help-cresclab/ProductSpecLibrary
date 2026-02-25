# Journey Status

This page documents the statuses, operating schedules, available actions, and lifecycle definitions for Customer Journeys. Images referenced are preserved as-is.

## Status matrix (summary)

| Status             | Operating schedule                                      | Actions in Customer Journey List                                                                                                         | Actions on Basic Settings Page                                       | Actions on Journey Settings Page                                                                                | Status change — User does...                                     | Status will be...                            | Popup dialog / Note                                                             |
| ------------------ | ------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------- | -------------------------------------------- | ------------------------------------------------------------------------------- |
| New                | —                                                       | Customer Journey List > Click "Create"                                                                                                   | —                                                                    | —                                                                                                               | Create                                                           | Draft (Incomplete)                           | ![](../../../../.gitbook/assets/resourcescellImage_779332349_9.jpg)             |
| Draft (Incomplete) | —                                                       | New Customer Journey > Click "Save" — Before completing trigger settings (Incomplete Draft) — Click "Make a copy" on an incomplete draft | Edit, Duplicate, Delete, Report, Exit (some actions may be disabled) | Save as Draft, Save, Save & Next, Next, Exit, Autosaved, Pause & Edit, Publish, Turn On (some actions inactive) | Completing trigger settings                                      | Draft (Complete)                             | —                                                                               |
| Draft (Complete)   | —                                                       | New Customer Journey > Click "Save" — After completing trigger settings (Complete Draft) — Click "Make a copy" on a complete draft       | Edit, Duplicate, Delete, Report, Exit                                | Save as Draft, Save, Save & Next, Next, Exit, Autosaved, Pause & Edit, Publish, Turn On                         | Publish                                                          | Ongoing (or Scheduled depending on schedule) | ![](../../../../.gitbook/assets/resourcescellImage_779332349_9.jpg)             |
| Paused             | Has schedule? V (varies)                                | Ongoing Customer Journey > Click "Pause & Edit" — Journey without schedule                                                               | Edit, Duplicate, Delete, Report                                      | Pause & Edit, Save, Save & Next, Next, Exit, Publish                                                            | Turn On or Edit                                                  | Ongoing (if turned on)                       | ![](../../../../.gitbook/assets/resourcescellImage_779332349_9.jpg)             |
| Scheduled          | Without schedule: Not Started; With schedule: Scheduled | Published journey with schedule, ready to start                                                                                          | Edit, Duplicate, Delete, Report                                      | Save, Pause & Edit, Publish, Turn On                                                                            | Start at scheduled time / Turn On                                | Paused (in some flows)                       | ![](../../../../.gitbook/assets/resourcescellImage_779332349_9.jpg)             |
| Ongoing            | V or - depending on schedule                            | Draft → Click "Publish"; Paused → Click "Turn On"; Journey without schedule                                                              | View, Duplicate, Pause, Delete, Report                               | Many actions available (see settings)                                                                           | Ended automatically when operating time ends or manually stopped | Ended (when finished)                        | ![](../../../../.gitbook/assets/resourcescellImage_779332349_9.jpg)             |
| Ended              | Journey with schedule ended automatically               | Journey with schedule that ended                                                                                                         | View, Duplicate, Delete, Report                                      | —                                                                                                               | User can replicate in List                                       | Draft (Incomplete) (to edit/replicate)       | Because the operating schedule ended, please replicate the journey and edit it. |

Notes:

* The matrix above is a condensed summary based on the original table and included images (preserved as resource references).
* Some actions are conditional depending on journey state (schedule present/absent) and user permissions.

## Action icons (as seen in original table)

![](../../../../.gitbook/assets/resourcescellImage_779332349_2.jpg) ![](../../../../.gitbook/assets/resourcescellImage_779332349_5.jpg) ![](../../../../.gitbook/assets/resourcescellImage_779332349_6.jpg)

(These images were present in the original spreadsheet and are left as resource references.)

## Scenarios (Johny Playground, TBD)

{% stepper %}
{% step %}
### 長期運作，有開始時間、無結束時間

(Long-term operation: has start time, no end time)

* Current situation: user sets a visible future start time; may require further editing later.
{% endstep %}

{% step %}
### 長期運作，開啟即開始、關閉即結束

(Long-term operation: starts when turned on, ends when turned off)

* Even if you rely on a start-only setup, editing later still forces adjusting the time to a future time — this scenario avoids that by starting immediately on Turn On.
{% endstep %}

{% step %}
### 短期運作，有開始時間、有結束時間

(Short-term operation: has both start and end times)
{% endstep %}

{% step %}
### 短期運作，即刻開始、有結束時間（尚可透過 3 解）

(Short-term operation: starts immediately, has end time — can be modeled via scenario 3)
{% endstep %}
{% endstepper %}

Reference: https://docs.aws.amazon.com/pinpoint/latest/userguide/journeys-best-practices.html#journeys-best-practices-lifecycle

## Lifecycle definitions

### Draft

The journey is being developed and hasn't been published yet. In this phase, you can change any aspect of the journey, including segments, activities, and settings for the journey. You can also leverage Amazon Pinpoint features for reviewing and testing the journey. You can repeat the review and test processes as many times as you want.

### Active

The journey has been developed, reviewed, tested, and published. Depending on the journey's schedule, it might currently be running or scheduled to start running at a later time. In this phase, you can't add, change, or remove activities from the journey.

### Closed

The journey has been developed, reviewed, tested, and published. It has started running and is closed to new participants. Depending on the schedule and settings, it might have passed its scheduled end time. Or the journey might have passed its scheduled start time, and it has an entry activity that's set to never add new segment members. In this phase, you can't add new participants to the journey. Existing participants who are currently waiting to start an activity can resume the journey.

### Stopped

The journey was developed, reviewed, tested, and published, and then subsequently stopped. You can't restart a journey after you stop it; you'll need to recreate it. If you stop a journey, Amazon Pinpoint continues to perform activities that are currently in progress until they complete, and continues to collect and aggregate analytics for those activities. Amazon Pinpoint stops evaluating the journey and doesn't perform any activities that haven't started.

***

If you want, I can:

* Recreate the full detailed matrix as a larger table (including every action column and each icon in its exact cell), or
* Export this content into a GitBook-ready markdown file with retained image paths. Which would you prefer?
