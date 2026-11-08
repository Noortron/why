# Project: App Modification Request

## 1. Goals (summary)
Four changes, in priority order:
1. Make the unlock-reason prompt impossible to dismiss accidentally.
2. Make the "are you still doing X?" reminder prompt impossible to dismiss accidentally.
3. Allow custom times (not just presets) for three settings.
4. Allow user-defined day start/end times (not fixed midnight-to-midnight).

## 2. Feature specs

### F1 — Unlock-reason prompt: prevent accidental dismissal
**Problem**: When the phone is unlocked, the reason-selection dialog/page can be dismissed
by an accidental tap elsewhere. User then bypasses the mindful check.

**Required behavior**:
- Present as a **full-screen** page (not a dismissible dialog).
- Must NOT be dismissible by:
  - tapping outside the content area
  - Android back gesture / back button
  - swiping down / dismissing the activity
- Only way to proceed: user makes a selection (preset reason, "Just habit", or
  types a custom reason) and confirms.
- [DECIDE: is there ANY escape hatch? e.g., a long-press "cancel" for emergencies.

**Acceptance criteria**:
- [ ] Unlocking shows a full-screen page.
- [ ] Back button/gesture does nothing.
- [ ] Tapping outside content does nothing.
- [ ] Selection + confirm is the only exit.
- [ ] Unlock is still recorded as a pebble after confirmation.

### F2 — "Still doing X?" reminder: prevent accidental dismissal
**Problem**: Same as F1 — the reminder prompt during use can be dismissed accidentally.

**Required behavior**: Apply the **same non-dismissible, full-screen treatment as F1**.

**Acceptance criteria**: Same as F1, applied to the reminder prompt.

### F3 — Custom times for three settings
Settings affected (in Settings screen):
- "Nudge me after"
- "Skip question after quick relock"
- "Evening summary"

**Current**: preset time values only.
**Required**:
- Add a **"Custom…"** option alongside presets for each of the three settings.
- When chosen, open a time input (HH:MM, 24h) with validation.
- Custom value persists across app restarts.

**Acceptance criteria**:
- [ ] Each of the three settings offers a Custom option.
- [ ] Custom value is saved and restored.
- [ ] Invalid input is rejected with feedback.
- [ ] Existing preset behavior unchanged.

### F4 — User-defined day start/end
**Problem**: App assumes day = midnight to midnight. Users have different day boundaries
(e.g., wake 10:00, sleep 04:00).

**Required**:
- Add settings for **Day start time**(HH:MM).
- "Day" (for pebble-jar reset, weekly views) is defined
  by these boundaries, not midnight.

**Acceptance criteria**:
- [ ] User can set day start and end.
- [ ] Pebble jar / daily count resets at custom start.
- [ ] Weekly view respects custom boundaries.

## 3. Out of scope
- Do not touch anything else other than what has been mentioned above.
