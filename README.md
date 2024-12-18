# Expo Linking.getInitialURL() returns null after navigation

This repository demonstrates a bug in Expo's `Linking.getInitialURL()` method.  When the app is launched via a deep link, navigates away from the initial screen, and then returns,  `getInitialURL()` may return `null` instead of the expected deep link URL.

## Bug Description

The `Linking.getInitialURL()` method is used to retrieve the initial URL that launched the app. However, if the app navigates away from the screen that initially handles the deep link and then returns to that screen, the method inconsistently returns `null`. This prevents the deep link from being processed correctly.

## Reproduction

1. Clone this repository.
2. Run `expo start`.
3. Launch the app from a deep link (e.g., `myapp://my-path`).
4. Navigate to a different screen within the app.
5. Navigate back to the initial screen.
6. Observe that `Linking.getInitialURL()` returns `null`, instead of the original deep link URL.

## Solution

See `bugSolution.js` for a potential workaround that involves persisting the deep link URL after the initial retrieval or using other methods like event listeners.