---
id: RewardedAd
title: RewardedAd
sidebar_label: RewardedAd
---

Creates [Rewarded Ad](https://developers.google.com/admob/android/rewarded) and register event listeners to various events.

:::tip

If you are going to use Rewarded Ad inside _functional component_, consider using [`useRewardedAd`](useRewardedAd).

:::

## Useage Example

TODO

## Methods

:::info

Methods listed below except [`createAd()`](#createad) must be called from instance created by [`createAd()`](#createad) static method.

:::

### createAd()

```js
static createAd(unitId: string, options?: FullScreenAdOptions): RewardedAd
```

Creates an ad instance.

**Parameters**

`unitId` : Rewarded Ad [unitId](https://support.google.com/admob/answer/7356431).

`options` (Optional) : Options for this ad. 

Properties:

| Name            | Type                             | Default | Description                                                |
| :-------------- | :------------------------------- | :------ | :--------------------------------------------------------- |
| loadOnMounted   | boolean                          | `true`  | Whether your ad to load automatically on mounted.          |
| showOnLoaded    | boolean                          | `false` | Whether your ad to show automatically on loaded.           |
| loadOnDismissed | boolean                          | `false` | Whether your ad to load new ad automatically on dismissed. |
| requestOptions  | [RequestOptions](RequestOptions) | {}      | Optional RequestOptions used to load the ad.               |

**Returns**

`RewardedAd` instance

### load()

```js
load(requestOptions?: RequestOptions): Promise<void>
```

Loads new Rewarded Ad.

Can not call this function if the ad is already loaded but not presented and dismissed. 

**Parameters**

`requestOptions` (Optional) : [RequestOptions](RequestOptions) used to load the ad. 

**Returns**

`Promise` that waits for ad load. When error is occurred while loading ad, the Promise will reject with `Error` object.

### show()

```js
show(): Promise<void>
```

Shows loaded Interstitial Ad. 

Ad must be loaded before calling this function. 

**Returns**

`Promise` that waits for ad present. When error is occurred while presenting ad, the Promise will reject with `Error` object.

### addEventListener()

```js
addEventListener(event: string, handler: (event?: any) => any): void
```

Adds an event handler for an ad event.

**Parameters**

`event` : Event name. Supported events:

| Event Name        | Description                                                                                            |
| ----------------- | ------------------------------------------------------------------------------------------------------ |
| adLoaded          | Fires when the ad has finished loading.                                                                |
| adFailedToLoad    | Fires when the ad has failed to load. The argument to the event handler is `Error` object.             |
| adPresented       | Fires when the ad is presented to user.                                                                |
| adFailedToPresent | Fires when an error occurred while presenting ad. The argument to the event handler is `Error` object. |
| adDismissed       | Fires when the ad is dismissed.                                                                        |
| rewarded          | Fires when user earned reward. The argument to the event handler is Reward object.                     |

`handler` : An event handler.

### removeAllListeners()

```js
removeAllListeners(): void
```

Removes all registered event handlers for this ad.

### setRequestOptions()

```js
setRequestOptions(requestOptions?: RequestOptions): void
```

Sets RequestOptions for this Ad instance.

**Parameters**

`requestOptions` : [RequestOptions](RequestOptions) used to load the ad.