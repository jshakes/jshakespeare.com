---
title: Milkshake
thumb: milkshake.png
subtitle: Create and listen to playlists in real-time with a friend over websockets
type: personal
order: 1
technology: Marionette, Sass, Grunt, Socket.io, MongoDB, Node.js with Express
projectUrl: http://milkshake.mu/
---
Milkshake is a web application that allows two friends to create playlists collaboratively and listen to them in real time. Listening to music online is often a private experience; Milkshake is an attempt to capture the feeling of listening to music with someone else.

Originally, Milkshake allowed users to select only three songs for their playlist, which users would then listen to together. However after listening to user feedback, we rebuilt the platform from the ground up to give users a more fluid, less restrictive experience. Now both users can collaboratively add, reorder and remove as many tracks as they like, even during playback.

The application uses the Songkick and Youtube search and embed APIs to power a Spotify-like media player.

{% include components/figure.html src="/assets/images/work/gifs/milkshake-1.gif" %}

The creator shares the playlist with a friend using a short URL and the music starts when both users are connected. The start time is recorded on the server to synchronize playback for both users, even across page reloads. 

Programmatically controlling the media player with remote messaging posed one of the biggest engineering challenges of the project. Since tracks can be embedded from Youtube or Spotify, we needed a wrapper to control the playback of the music and seek to a specific point in a track in order to keep both users in sync. This wrapper came in the form of Popcorn, a now defunct project by Mozilla.    

{% include components/figure.html src="/assets/images/work/gifs/milkshake-2.gif" %}

Milkshake intentionally does not have user accounts in an effort to reduce the barrier to entry for new users. This way, nothing about the user is recorded remotely and the whole experience is completely anonymous. Instead, each user is assigned an avatar of a famous musician so they can chat while the music is playing. 

The back-end of the application runs on Node.js and MongoDB and uses Socket.io for real-time websocket messaging. The front-end of the application is built in Marionette.

{% include components/figure.html src="/assets/images/work/gifs/milkshake-3.gif" %}

#### In the press

[The Next Web: Milkshake is a simple way to share three-track music playlists and chat with friends in real-time](https://thenextweb.com/apps/2014/10/21/milkshake-simple-way-share-three-track-music-playlists-chat-friends-real-time)
