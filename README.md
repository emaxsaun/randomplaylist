JW Player Ramdom Playlist
==========

This is a small example for use with the JW Player. It allows for playlists to be shuffled randomly.

### [Demo](http://www.pluginsbyethan.com/github/randomplaylist.html)

Implementation:
==========

You need the following script after your JW Player embed instance(s), please note that maxPlayers should be 1, unless you have more than one player on your page. In our demo, it is 2:

<pre>
var maxPlayers = 2;
function randomPl(id){
	return function(){
		var playlist = jwplayer(id).getPlaylist();
		var playlistsize = playlist.length;
		var randomnumber=Math.floor(Math.random()*playlistsize);
		jwplayer(id).playlistItem(randomnumber);
	}
}
function randomPl2(id){
	return function(){
		var playlist = jwplayer(id).getPlaylist();
		var playlistsize = playlist.length;
		var randomnumber=Math.floor(Math.random()*playlistsize);
		jwplayer(id).playlistItem(randomnumber);
		jwplayer(id).stop();
	}
}
for(var i = 0; i < maxPlayers; i++) { 
	var player = jwplayer(i).id;
	jwplayer(player).onComplete(randomPl(player));
	jwplayer(player).onPlaylistItem(randomPl2(player));
}
</pre>

Full Example:
==========
<pre>
&lt;!DOCTYPE html&gt;
&lt;head&gt;
&lt;title&gt;Random Playlist Item&lt;/title&gt;
&lt;script type=&quot;text/javascript&quot; src=&quot;http://p.jwpcdn.com/6/8/jwplayer.js&quot;&gt;&lt;/script&gt;
&lt;/head&gt;
&lt;body&gt;
&lt;div id=&quot;container&quot;&gt;&lt;/div&gt;&lt;br /&gt;&lt;div id=&quot;container2&quot;&gt;&lt;/div&gt;
&lt;script&gt;
jwplayer(&quot;container&quot;).setup({<br />
&nbsp;&nbsp;playlist: &quot;http://content.jwplatform.com/feeds/13ShtP5m.rss&quot;,<br />
&nbsp;&nbsp;displaytitle: false,<br />
&nbsp;&nbsp;width: 640,<br />
&nbsp;&nbsp;height: 360<br />
});
&lt;/script&gt;
&lt;script&gt;
jwplayer(&quot;container2&quot;).setup({<br />
&nbsp;&nbsp;playlist: &quot;http://content.jwplatform.com/feeds/13ShtP5m.rss&quot;,<br />
&nbsp;&nbsp;displaytitle: false,<br />
&nbsp;&nbsp;width: 640,<br />
&nbsp;&nbsp;height: 360<br />
});
&lt;/script&gt;
&lt;script type=&quot;text/javascript&quot;&gt;
var maxPlayers = 2;
function randomPl(id){<br />
	return function(){<br />
		var playlist = jwplayer(id).getPlaylist();
		var playlistsize = playlist.length;
		var randomnumber=Math.floor(Math.random()*playlistsize);
		jwplayer(id).playlistItem(randomnumber);
	}<br />
}<br />
function randomPl2(id){<br />
	return function(){<br />
		var playlist = jwplayer(id).getPlaylist();
		var playlistsize = playlist.length;
		var randomnumber=Math.floor(Math.random()*playlistsize);
		jwplayer(id).playlistItem(randomnumber);
		jwplayer(id).stop();
	}<br />
}<br />
for(var i = 0; i &lt; maxPlayers; i++) { <br />
	var player = jwplayer(i).id;
	jwplayer(player).onComplete(randomPl(player));
	jwplayer(player).onPlaylistItem(randomPl2(player));
}<br />
&lt;/script&gt;
&lt;/body&gt;
&lt;/html&gt;
</pre>

The source code is available for this example. There is just a .html file. Publishing the html can be simply done with any text editor. Enjoy~! :)
