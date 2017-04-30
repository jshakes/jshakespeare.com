---
title: The Moon Tonight
thumb: moon-tonight.png
blurb: Location-based rendering of tonight's moon phase using CSS
type: personal
order: 2
projectUrl: http://moontonight.co
githubUrl: https://github.com/jshakes/moontonight
---
The Moon Tonight started with a simple thought: could all the moon’s phases be rendered purely with CSS? I ran a [few experiments](https://codepen.io/jshakes/pen/zrByoQ) and discovered that they could.

<img src="/assets/images/gifs/moontonight-1.gif" alt="The Moon Tonight">

The next step was to find a source of data for determining what phase the moon was in given the user’s location. For this I used the Dark Sky API and supplied location data using the browser’s Geolocation API (with a fallback to the Google Places API).

With the user’s latitude and longitude, Dark Sky can provide a decimal value that describes the moon phase, where <0.5 is a new moon waxing to full, and >0.5 is a waning moon. Using a Sass loop I then created 100 CSS classes to which could I could map this decimal value and provide a visual rendering for each phase.

