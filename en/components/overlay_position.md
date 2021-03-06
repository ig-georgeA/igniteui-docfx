---
title: Overlay Service - Positioning Strategies
_description: Explanation and example about the Overlay Service's IPositionStrategy interface and the classes that implement it.
---

## Position strategies

Position strategies determine where to display the component in the provided IgxOverlayService. There are three position strategies:

1. **Global** - Positions the element based on the directions passed in through `positionSettings`. These are Top/Middle/Bottom for `verticalDirection` and Left/Center/Right for `horizontalDirection`. Defaults to:

    | horizontalDirection        | verticalDirection        |
    |:---------------------------|:-------------------------|
    | HorizontalAlignment.Center | VerticalAlignment.Middle |
<div class="divider"></div>

2. **Connected** - Positions the element based on the directions and start point passed in through `positionSettings`. It is possible to either pass a start point (type `Point`) or an `HTMLElement` as a positioning base. Defaults to:

    | target          | horizontalDirection       |  verticalDirection       | horizontalStartPoint     | verticalStartPoint       |
    |:----------------|:--------------------------|:-------------------------|:-------------------------|:-------------------------|
    | new Point(0, 0) | HorizontalAlignment.Right | VerticalAlignment.Bottom | HorizontalAlignment.Left | VerticalAlignment.Bottom |
<div class="divider"></div>

3. **Auto** - Positions the element as in **Connected** positioning strategy and re-positions the element in the view port (calculating a different start point) in case the element is partially out of view. Defaults to:

    | target          | horizontalDirection       |  verticalDirection       | horizontalStartPoint     | verticalStartPoint       |
    |:----------------|:--------------------------|:-------------------------|:-------------------------|:-------------------------|
    | new Point(0, 0) | HorizontalAlignment.Right | VerticalAlignment.Bottom | HorizontalAlignment.Left | VerticalAlignment.Bottom |
<div class="divider"></div>
*Note*: Will not try to reposition the element if the strategy is using  HorizontalDirection = Center / VerticalDirection = Middle.

## Usage
Position an element based on an existing button as a target, so it's start point is the button's Bottom/Left corner.
```typescript
const positionSettings: PositionSettings = {
    target: buttonElement.nativeElement,
    horizontalDirection: HorizontalAlignment.Right,
    verticalDirection: VerticalAlignment.Bottom,
    horizontalStartPoint: HorizontalAlignment.Left,
    verticalStartPoint: VerticalAlignment.Bottom
};

const strategy =  new ConnectedPositioningStrategy(positionSettings);
strategy.position(contentWrapper, size);
```

### Getting Started
The position strategy is passed as a property in the `overlaySettings` parameter when the `overlay.show()` method is called:
```typescript
    // Initializing and using overlay settings
    const overlaySettings: OverlaySettings = {
        positionStrategy: new GlobalPositionStrategy(), // Passes the positioning strategy
        scrollStrategy: new AbsoluteScrollStrategy(),
        modal: true,
        closeOnOutsideClick: true
    }
    overlay.show(dummyElement, overlaySettings); 
``` 
<div class="divider"></div>

To change the position strategy used by the overlay, override the `positionStrategy` property of the `overlaySettings` object passed to the overlay:
```typescript
    // overlaySettings is an existing object of type OverlaySettings
    // to override the position strategy
    const positionStrategy = new AutoPositionStrategy();
    overlay.show(dummyElement, { positionStrategy }); 
```
<div class="divider"></div>

To change the position settings an already existing strategy is using, override any of the settings of that strategy:
```typescript
    // overlaySettings is an existing object of type OverlaySettings
    // overlaySettings.positionStrategy is an existing PositionStrategy with settings of type PositionSettings
    // to override the position setting of an existing PositionStrategy
    Object.assign(overlaySettings.positionStrategy.settings, {
        target: dummyHTMLElement,
        horizontalStartPoint: HorizontalAlignment.Left,
        horizontalDirection: HorizontalAlignment.Left
    });
    overlay.show(dummyElement, overlaySettings);
    // the element will now start to the left of the target (dimmyHTMLElement)
    // and will align itself to the left
```
<div class="divider--half"></div>

### Dependencies

Import the desired position strategy if needed like:

```typescript
import {AutoPositionStrategy, GlobalPositionStrategy, ConnectedPositioningStrategy } from './position/global-position-strategy';
```
## Demos 

### Horizontal and Vertical Direction
Changing the horizontal and/or vertical direction of the positioning settings determined where the content will align itself. Depending on the positioning strategy chosen, the content will either align relative to the target's container (`AutoPositionStrategy` and `ConnectedPositioningStrategy`) or the body of the document (`GlobalPositioningStrategy`)

<div class="sample-container loading" style="height: 400px">
    <iframe id="overlay-position-sample-1-iframe" frameborder="0" seamless width="100%" height="100%" src="{environment:demosBaseUrl}/overlay-position-sample-1" onload="onSampleIframeContentLoaded(this);"></iframe>
</div>
<div>
    <button data-localize="stackblitz" class="stackblitz-btn" data-iframe-id="overlay-position-sample-1-iframe" data-demos-base-url="{environment:demosBaseUrl}">StackBlitz</button>
</div>
<div class="divider"></div>

### Horizontal and Vertical Start Point
Changing the horizontal and/or vertical start point of the positioning settings determines where the content will try to start from. Start point has effect only if the `target` passed in the `positionSettings` is an `HTMLElement` and works only for `AutoPositionStrategy` and `ConnectedPositioningStrategy`.
In the demo below, the overlay element will position itself starting from the target element depending on the start point chosen. Directions are always `HorizontalAlignment.Right` and `VerticalAlignment.Bottom`:

<div class="sample-container loading" style="height: 400px">
    <iframe id="overlay-position-sample-2-iframe" frameborder="0" seamless width="100%" height="100%" src="{environment:demosBaseUrl}/overlay-position-sample-2" onload="onSampleIframeContentLoaded(this);"></iframe>
</div>
<div>
    <button data-localize="stackblitz" class="stackblitz-btn" data-iframe-id="overlay-position-sample-2-iframe" data-demos-base-url="{environment:demosBaseUrl}">StackBlitz</button>
</div>
<div class="divider"></div>


## API

### Methods
| Position Strategy | Name                                         | Description                                     |
|:------------------|:---------------------------------------------|:------------------------------------------------|
| Global            | `position(contentElement)`                   | Positions the element, based on the horizontal and vertical directions. |
| Connected         | `position(contentElement, size{})`           | Positions the element, based on the position strategy used and the size passed in.|
| Auto              | `position(contentElement, size{}, document?)`| Positions the element, based on the position strategy used and the size passed in.|

### PositionSettings
| Name               | Type                        | Description |
| :----------------- | :-------------------------- | :---------- |
|target              | Point \| HTMLElement         | Attaching target for the component to show          |
|horizontalDirection | HorizontalAlignment         | Direction in which the component should show        |
|verticalDirection   | VerticalAlignment           | Direction in which the component should show        |
|horizontalStartPoint| HorizontalAlignment         | Target's starting point                             |
|verticalStartPoint  | VerticalAlignment           | Target's starting point                             |
|openAnimation       | AnimationReferenceMetadata  | Animation applied while overlay opens               |
|closeAnimation      | AnimationReferenceMetadata  | Animation applied while overlay closes              |
