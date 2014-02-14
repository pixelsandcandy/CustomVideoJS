# CustomVideoJS
Customize your own HTML5 video player! CustomVideoJS is built on top of [Video.js](http://videojs.com)

### Easy Implementation
```javascript
var videoPlayer = new CustomVideoJS( 'video-player' );
    
    videoPlayer.mp4( 'http://video-js.zencoder.com/oceans-clip.mp4' );
    videoPlayer.webm( 'http://video-js.zencoder.com/oceans-clip.webm' );
    videoPlayer.ogv( 'http://video-js.zencoder.com/oceans-clip.ogv' );
    
    videoPlayer.create({
		inject: '#video-player-container',
		playPauseBtn: '#play-pause-btn',
		
		play: function( player ) {...},
		pause: function( player ) {...},
		ready: function( player ) {...},
		buffering: function( player ) {...},
		playing: function( player ) {...},
		finishedPlaying: function( player ) {...}
	});
```
### Cue Markers + Segments
```
..* hit
..* hitFirst
..* scrubbedOn
..* scrubbedOff
..* scrubbedOnDrop
```
```javascript
	// marker + segment events
	// hit: function( player, marker ) {...},
	// hitFirst: function( player, marker ) {...},
	// scrubbedOn : function( player, marker ) {...},
	// scrubbedOff : function( player, marker ) {...},
	// scrubbedOnDrop : function( player, marker ) {...}
	
	// x > 1 = time based
	// x < 1 = percentage based
	videoPlayer.addMarker( 6.2, {
		foo: 'bar',
		hit: function( player, marker ) {...}
	});
	
	// startTime, endTime, options
	videoPlayer.addSegment( 2, 10, {
		year: 2009,
		scrubbedOn : function( player, marker ) {...},
		scrubbedOff : function( player, marker ) {...}
	});
	
	// endTime, options - add to end of last segment
	videoPlayer.addNextSegment( 14, {
		title: 'Hello World',
		hitFirst: function( player, marker ) {...}
	});
	
```
