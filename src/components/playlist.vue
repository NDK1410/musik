<template>
  <div>
    <main>
    	<section class="player">
    		<h2 class="song-title">{{ current.title }} - <span>{{ current.artist }}</span></h2>
    		<div class="control">
	    		<button class="prev" @click="prev">Prev</button>
	    		<button class="play" v-if="!isPlaying" @click="play">Play</button>
	    		<button class="pause" v-else @click="pause">Pause</button>
	    		<button class="next" @click="next">Next</button>
    		</div>
    	</section>
    	<section class="playlist">
    		<h3>The Playlist</h3>
    		<button v-for="song in songs" :key="song.src" @click="play(song)" :class="(song.src == current.src) ? 'song playing' : 'song'">{{ song.title }} - {{ song.artist }}
    		</button>
    	</section>
    </main>
  </div>
</template>

<script>
export default {
  name: 'Playlist',
  data () {
  	return {
  		current: {},
  		index: 0,
  		isPlaying: false,
  		songs: [
	  		{
	  			title: "Bánh Mì Không",
	  			artist: "Đạt G ft Du uyên",
	  			src: require("../assets/Banh-Mi-Khong-Dat-G-DuUyen.mp3")
	  		},
	  		{
	  			title: "The Riven",
	  			artist: "Axel Johansson",
	  			src: require("@/assets/The-River-Axel-Johansson.mp3")
	  		},
	  		{
	  			title: "Beautiful In White",
	  			artist: "Shayne Ward",
	  			src: require("@/assets/Beautiful-In-White-Shayne-Ward.mp3")
	  		},
	  		{
	  			title: "Chống Dịch Như Chống Giặc",
	  			artist: "Ưng Đại Vệ",
	  			src: require("../assets/Chong-Dich-Nhu-Chong-Giac-Ung-Dai-Ve.mp3")
	  		},
	  		{
	  			title: "Phía Say Em",
	  			artist: "Kay Trần ft Binz",
	  			src: require("../assets/Phia-Sau-Em-Kay-Tran-Binz.mp3")
	  		}
  		],
  		player: new Audio()
  	}
  },
  methods: {
  	play (song) {
  		if (typeof song.src != "undefined") {
  			this.current = song;

  			this.player.src = this.current.src;
  		}
  		this.player.play();
  		this.isPlaying = true;
  	},
  	pause () {
  		this.player.pause();
  		this.isPlaying = false;
  	},
  	prev () {
  		this.index--;
  		if (this.index < 0) {
  			this.index = this.songs.length - 1;
  		}
  		this.current = this.songs[this.index];
  		this.play(this.current);
  	},

  	next () {
  		this.index++;
  		if (this.index > this.songs.length - 1) {
  			this.index = 0;
  		}
  		this.current = this.songs[this.index];
  		this.play(this.current);
  	}
  },
  created () {
  	this.current = this.songs[this.index];
  	this.player.src = this.current.src;
  }
}
</script>