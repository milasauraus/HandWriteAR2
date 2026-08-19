# HandWriteAR: Fist-Controlled Air Writing

A kid-friendly, camera-based air-writing prototype for GitHub Pages. Learners use intentional hand gestures to control when their index-finger movement is recorded:

```
✊ Fist       → PAUSED
🖐️ Open hand  → TRACKING
☝️ Index finger → air-write
✊ Fist       → pause / finish stroke
```

## What changed

The interaction is state-based rather than hand-presence-based. The app records only while a learner has deliberately opened their hand; a fist stops recording. This creates clearer start and stop events for later analysis of trajectory, speed, hesitation, stroke direction, and stroke order.

Index-finger coordinates use exponential smoothing and a small movement threshold, which filters camera jitter before it reaches the drawing canvas.

## Publish to GitHub Pages

1. Put `index.html` and this `README.md` at the root of your `HandWriteAR` repository.
2. Commit and push the files.
3. In GitHub, open **Settings → Pages**, choose the branch that contains `index.html`, then save.
4. Open the deployed **HTTPS** site—not the downloaded `index.html` file—and select **Allow** when the browser asks to use the camera.

The page requests camera permission as soon as the learner selects **Start camera**, before downloading the hand-tracking library. Camera access is available only from a secure context: GitHub Pages (`https://…`) or `localhost` during development. The page loads MediaPipe's hand-landmark model from its official hosted model URL, so an internet connection is also required when the page starts.

## Research direction

The next meaningful step is to treat each open-hand-to-fist interval as one independently assessed stroke. This would support feedback about starting point, direction, unwanted strokes, reversals, and eventually letter-level stroke order.
