# start-google-analytics-tracker

`start-google-analytics-tracker` is a Polymer Element for [Google Analytics Web Tracking](https://developers.google.com/analytics/devguides/collection/analyticsjs/), supports page and event tracking.

Script analytics.js is served from local `scripts` dir, because https://www.google-analytics.com/analytics.js have only 2 hours cache.

You need download latest analytics.js file.

```sh
wget https://www.google-analytics.com/analytics.js -O scripts/analytics.js
```

Inspired by this repo https://github.com/matthewlawson/google-analytics-universal-tracker

## Getting Started

### Installation

```sh
bower install start-google-analytics-tracker --save
```

### Usage

#### Initialise

```html
<link rel="import" href="bower_components/start-google-analytics-tracker/start-google-analytics-tracker.html">

<start-google-analytics-tracker code="UA-XXXXX-Y"></start-google-analytics-tracker>
```

If you are using regular anchor links and not push-state links you are ready to go!

If you have a Single Page Application that uses push-state, eg with `page.js` or `<app-router>` you will need to signal to the `start-google-analytics-tracker` element that the page has changed.

The Page Change events are handled using iron-signals so you do not need to do any dom finding to trigger a page track.

#### Track a page Change

```javascript
    this.fire('iron-signal', {name: 'track-page', data: { path: "/about.html" } });
```

#### Track an Event

```javascript
    this.fire('iron-signal', {name: 'track-event',data: {category: "messages",action: "send_text_message",label: "group",value: 1}});
```

#### User id attribution

To use [Google Analytics user id attribution](https://developers.google.com/analytics/devguides/collection/analyticsjs/user-id) set the user id property on the element:

```javascript
    document.querySelector("start-google-analytics-tracker").userId = loggedInUserId;
```
