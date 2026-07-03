# Event Platform Example Sessions

A Drupal [recipe](https://www.drupal.org/docs/extending-drupal/drupal-recipes) that installs example content for testing and demoing [Event Platform](https://www.drupal.org/project/event_platform) and Event Platform Starter (soon to be renamed Summit).

This is a development tool, not intended for use on production sites. It exists to make it quick to spin up a realistic-looking event site without having to hand-create sessions, speakers, and taxonomy terms every time.

## What it provides

Applying this recipe creates:

- **22 session nodes**, all in the `proposed` moderation state, so they can be used to exercise bulk moderation, scheduling, and review workflows.
- **15 speaker users**, each with the `speaker` role, assigned as authors/speakers on the sessions.
- **Taxonomy terms** for:
  - `event` — a single term for `2025`
  - `session_audience` — Beginner, Intermediate, Advanced, All Attendees
  - `session_category` — Site-Building; Theming, Design, & Usability; Project Management & Consulting; Development & Performance; Off the "Drupal Island"; New to Drupal

All content is defined as UUID-keyed YAML files under `content/`, following the standard format for Drupal's [Content API / default content](https://www.drupal.org/project/default_content) recipe content.

## Requirements

- A Drupal site with [Event Platform](https://www.drupal.org/project/event_platform) or Event Platform Starter installed, since the session content depends on fields and taxonomy vocabularies (e.g. `field_audience`, `field_event`, `field_session_category`) provided by those projects.
- Drupal core's recipe system (Drupal 10.3+ / 11).

## Usage

Apply the recipe with Drush from your site root:

```
drush recipe ../path/to/event_platform_example_sessions
```

Or, if this recipe is placed inside your site's `recipes/` directory:

```
drush recipe recipes/event_platform_example_sessions
```

Recipes are additive and idempotent-ish by UUID — re-applying will not duplicate content that already exists with the same UUIDs, but it's still meant for disposable dev/test environments rather than repeated application to a live site.

## Notes

- Every generated user has the same placeholder password hash; do not use these accounts outside local development.
- All sessions are seeded as `proposed` so you can test moving them through later moderation states (e.g. scheduled, confirmed) yourself.
