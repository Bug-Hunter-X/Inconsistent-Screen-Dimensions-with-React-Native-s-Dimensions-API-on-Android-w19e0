# React Native Dimensions API Inconsistency on Android

This repository demonstrates a bug where React Native's `Dimensions.get('window')` API returns incorrect screen dimensions on Android devices under certain circumstances.  The problem manifests as inconsistent layout, where components are rendered with incorrect sizes or positions.  The solution involves using the `onLayout` event or `useEffect` hook to ensure that dimensions are fetched after the layout has properly stabilized. 

## Bug Description

The core issue is that `Dimensions.get('window')` doesn't always provide accurate dimensions immediately after component mounting or during certain lifecycle events. This is especially apparent on Android. The timing of when the dimensions are retrieved significantly affects the accuracy.

## Reproduction

1. Clone the repository.
2. Run the app on an Android device or emulator.
3. Observe layout inconsistencies or unexpected behavior.  This might involve rotating the screen, minimizing and restoring the app, or even just waiting for a short period.

## Solution

The included `DimensionsBugSolution.js` file provides a working solution. It utilizes the `onLayout` prop to ensure that the component's layout is fully rendered before obtaining the window dimensions.  Alternatively, one could use the `useEffect` hook in conjunction with the `Dimensions` API and the `layout` event.