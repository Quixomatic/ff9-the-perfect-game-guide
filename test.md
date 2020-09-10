## Precursor

Record watchers have been around for quite some time to provide real-time data on back-end forms in **ServiceNow** as well as in the **Service Portal**. Changes in instance data trigger an event on the front end, upon receiving the event you can then perform logic based on the change to instance data.

Similarly to making **REST API** calls there is a predefined **npm** package you can install to work just like `@servicenow/ui-effect-http`. This package is named `@servicenow/ui-effect-amb` and you will have to install it to utilize record watching functionality.

> Record watchers can not truly be tested until the components are deployed to the instance directly. This is because there is no way to use the proxy from now-cli.json in websockets which is the paradigm that record watchers use.

> This can make debugging quite difficult, so I apologize for the inconvenience.

## Preparation

First things first you need to install the package.

```
npm install @servicenow/ui-effect-amb
```

This package needs to be imported to create an `actionHandler` similar to when you import `@servicenow/ui-effect-http`.

```
import { createAmbSubscriptionEffect } from "@servicenow/ui-effect-amb";
```

The function `createAmbSubscriptionEffect` takes two main parameters, a `channelid` string and an `options` object.

```
 /*
 * @param {String} channelId - AMB Channel ID
 * @param {Object} options
 * @param {String} options.subscribeStartedActionType - Action dispatched when an amb subscription is started
 * @param {String} options.subscribeSucceededActionType - Action dispatched if an amb subscription succeeds
 * @param {String} options.subscribeFailedActionType - Action dispatched if an amb subscription fails
 * @param {String} options.unsubscribeSucceededActionType - Action dispatched when an amb unsubscribe is successful
 * @param {String} options.messageReceivedActionType - Action dispatched when a message is received on a channel
 * @param {Boolean} options.encodeURIComponentForChannelId - Encode channel id URL (default: true)
 *
 * @return {Object} AMB Subscription Effect Descriptor
 */
```