<template>
  <div>
    <main>
    	<section class="player">
    		<h2 class="song-title">{{ current.title }} - <span>{{ current.artist }}</span></h2>
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
  created () {
  	this.current = this.songs[this.index];
  	this.player.src = this.current.src;
  	this.player.play();
  }
}
</script>