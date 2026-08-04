# 1. OBJECTIVE
* Enhance the Quiet Garden web application (`quietgarden.html`) by improving state persistence, fixing random element flickering, providing clearer audio feedback, adding a warning sound when thresholds are crossed, making the current quiet streak prominent, and enhancing accessibility.
* Deliver a polished, robust single-file user experience without adding unnecessary dependencies or altering core gameplay mechanics.

# 2. CONTEXT SUMMARY
* The application is a single self-contained HTML file (`quietgarden.html`) using vanilla JavaScript, Web Audio API, Canvas 2D, and `localStorage`.
* Key areas identified for improvement:
  - Settings (Threshold, Smoothing, Drain Rate) and session counters (`quiet`, `alarms`) do not persist in `localStorage`.
  - The random owl visitor (`🦉`) flickers due to `Math.random()` being evaluated on every `render()` call.
  - Audio permission and active microphone state feedback can be improved.
  - Basic accessibility (ARIA labels, roles) for meters and dynamic elements is missing.
  - Users requested an option/feature for a warning sound when the threshold is crossed, and making the "Current Quiet Streak" much larger and more prominent since kids look at it most.

# 3. APPROACH OVERVIEW
* Implement targeted, clean enhancements directly within `quietgarden.html`.
* Maintain the lightweight, zero-build-step nature of the project.
* Follow structured steps covering persistence, bug fixing, audio/warning feedback, UI prominence for the streak, and accessibility.

# 4. IMPLEMENTATION STEPS
* **Step 1: Expand LocalStorage Persistence**
  - Goal: Save user engine tweaks (threshold, smoothing, drain rate) and session stats (`quiet`, `alarms`) alongside `score` and `achievements`.
  - Method: Update `save()` and initialization logic to load/store all configuration and progress variables.
* **Step 2: Fix Random Animal Visitor Flicker**
  - Goal: Ensure random visitors (like the owl `🦉`) appear and persist stably rather than flickering every frame.
  - Method: Store visitor appearance state or throttle the random trigger condition instead of calling `Math.random()` unconditionally in `render()`.
* **Step 3: Enhance Audio State, Visual Feedback & Warning Sound**
  - Goal: Provide clear visual indication of microphone status and audio context readiness, and trigger a subtle warning sound when approaching or crossing the threshold.
  - Method: Add distinct UI states for active monitoring vs stopped/suspended audio, and play a warning tone when noise exceeds the threshold.
* **Step 4: Promote Current Quiet Streak UI**
  - Goal: Make the "Current Quiet Streak" prominent and much larger in the UI.
  - Method: Redesign/reposition the current streak into a prominent card or large display element in the layout.
* **Step 5: Add Accessibility (a11y) Improvements**
  - Goal: Improve screen reader support for key UI components.
  - Method: Add appropriate `aria-label`, `role="meter"`, and semantic attributes to progress bars, mood indicators, and badges.

# 5. TESTING AND VALIDATION
* **Persistence Testing:** Adjust sliders and stats, refresh the page, and verify values are correctly restored from `localStorage`.
* **Visual Stability & Prominence Testing:** Run the app, ensure dynamic animal visitors do not flicker, and verify the current quiet streak is prominent.
* **Audio & Warning Sound Testing:** Test microphone activation, threshold crossing warning tone, and status message clarity.
* **Accessibility Check:** Inspect DOM elements for proper ARIA attributes.
