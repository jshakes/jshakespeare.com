---
title: The Moon Tonight
thumb: moon-tonight.png
subtitle: Location-based rendering of tonight's moon phase using CSS
type: personal
order: 2
date: 2016-09-19
projectUrl: http://moontonight.co
githubUrl: https://github.com/jshakes/moontonight
technology: Sass, Gulp, Jekyll
---
The Moon Tonight started with a simple idea: could all the moon’s phases be rendered purely with CSS? I ran a [few experiments](https://codepen.io/jshakes/pen/zrByoQ) and discovered that, with a little visual trickery, they could.

The HTML element for the moon contains on two child divs, one for each half of the moon’s face. Within each of these halves is another pair of divs for the light and dark part of the moon. The light part is always a perfect semi-circle, while the dark part (the shadow) is the element that changes in size and position between phases. For a waxing moon, the shadow div in the right half of the moon moves, and for a waning moon it is the shadow in the left half of the moon that moves.

{% include components/figure.html src="/assets/images/work/gifs/moontonight-1.gif" %}

This applies to the northern hemisphere only, in the southern hemisphere the reverse is true. In order to determine the user’s hemisphere I used the browser’s Geolocation API (with a fallback to the Google Places API) to get the user’s latitude and longitude. If the user’s location has a latitude of less than zero, the moon element is flipped 180 degrees.

{% include components/figure.html src="/assets/images/work/gifs/moontonight-2.gif" %}

While determining a user’s hemisphere was fairly trivial, I still needed to determine the current moon phase in the user’s location. Because the time of sunset varies depending on a user’s longitude, the phase of the moon is slightly different from one location to another. Rather than calculate this myself, I used the Dark Sky API.

With the user’s latitude and longitude, Dark Sky provides a decimal value that describes the moon phase, where 0 is a new moon, <0.5 is a waxing moon, and >0.5 is a waning moon.

Converted to percentage, it looks like this:

{% highlight javascript %}
function getPhaseName(phase) {
  switch(true) {
    case (phase < 12.5):
      return 'New moon';
    case (phase < 25):
      return 'Waxing crescent';
    case (phase < 37.5):
      return 'First quarter';
    case (phase < 49):
      return 'Waxing gibbous';
    case (phase < 52):
      return 'Full moon';
    case (phase < 75):
      return 'Waning gibbous';
    case (phase < 87.5):
      return 'Last quarter';
    case (phase < 100):
      return 'Waning crescent';
  }
}
{% endhighlight %}

Using a [Sass mixin and a loop](https://github.com/jshakes/moontonight/blob/master/_assets/scss/modules/_moon.scss) I then created 100 CSS classes to which could I could map these values and provide a visual rendering for each phase.

I wrote a little extra Javascript to provide the ability to look at the coming week's moon phases (Dark Sky provides a seven day forecast), plus a few other features like displaying a warning for days on which heavy cloud was forecast that might obscure the moon.

{% include components/figure.html src="/assets/images/work/gifs/moontonight-3.gif" %}
