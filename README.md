# posthog-gtm-template

A GTM template for capturing events to PostHog.

## Prerequisites

💡 The tag does NOT load PostHog to the page.

PostHog must already be initialized on the page before this tag runs (e.g., PostHog snippet or SDK present).
If `window.posthog.capture` is not available by the final attempt, the tag fails.

## What this tag does

- Calls `posthog.capture(eventName, properties)` in the page context.
- Builds properties by merging:
  1. an optional Event Parameters Object (must resolve to an object), and
  2. a manual parameters table (overrides the object on key conflicts, including empty strings).
- Optionally retries when PostHog isn’t ready yet (e.g., SPA timing), then fails gracefully if retries exhaust.
