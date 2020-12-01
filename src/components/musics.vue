<template>
    <div>
        <div class="container">
            <div class="card" style="width: 30rem;">
                <img :src="current.url">
                <h5>{{current.title}}</h5>
                <section class="player">
                <div class="controls">
           <button class="prev" @click="prev"><i class="fa fa-step-backward"></i></button>
          <button class="play" v-if="!isPlaying" @click="play"><i class="fa fa-play" style="padding:8px"></i></button>
          <button class="pause" v-else @click="pause"><i class="fa fa-pause" style="padding:8px"></i></button>
          <button class="next" @click="next"><i class="fa fa-step-forward"></i></button> 
        </div>
                </section>
                <div class="card-body">
                   <button v-for="song in songs" :key="song.id" @click="play(song)" class="btn">
                      {{song.title}}
                  </button> 
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
  name: 'musics',
  data(){
      return{
      current:{},
      index: 0,
      isPlaying:false,
      songs:[
          {   id:1,
              title:'Calexico - Across The Wire',
              src:"https://archive.org/download/calexico2006-12-02..flac16/calexico2006-12-02d1t02.mp3",
              url:"https://fanart.tv/detailpreview/fanart/music/5e372a49-5672-4fb8-ba14-18c90780c4f9/artistbackground/calexico-54c3f7e14da1b.jpg"
          },
          {
              id:2,
              title:'Ryan Adams & The Cardinals - Cold Roses',
              src:"https://archive.org/download/ra2007-07-21/ra2007-07-21d1t05_64kb.mp3",
              url:"https://upload.wikimedia.org/wikipedia/en/thumb/6/61/Cold_roses.jpg/220px-Cold_roses.jpg"
          },
          {
              id:3,
              title:' The Slackers - Married Girl',
              src:"https://archive.org/download/slac2002-02-15/slac2002-02-15d1t07_64kb.mp3",
              url:"https://images.shazam.com/coverart/t5088098-b1485047069_s400.jpg"
          },
          {
              id:4,
              title:'Blitzen Trapper - Saturday Night',
              src:"https://archive.org/download/blitzentrapper2009-02-24.flac16/blitzentrapper2009-02-24t02_64kb.mp3",
              url:"https://music-b26f.kxcdn.com/wp-content/uploads/2017/09/Blitzen-Trapper-770x470.jpg"
          },
          {
              id:5,
              title:'The Samples - Feel Us Shaking',
              src:"https://archive.org/download/samples2003-11-21.flac16/samples2003-11-21d2t04.mp3",
              url:"https://i.ytimg.com/vi/-x5dG58Ps7I/hqdefault.jpg"
          },
          {
              id:6,
              title:'My Morning Jacket - Phone Went West',
              src:"https://archive.org/download/mmj2003-09-26.shnf/mmj2003-09-26d2t08.mp3",
              url:"https://m.media-amazon.com/images/I/71+B0XiZ0jL._SS500_.jpg"
          },
          {
              id:7,
              title:' G. Love & Special Sauce - Dreamin',
              src:"https://archive.org/download/glove2004-03-18.shnf/glove2004-03-18d1t05.mp3",
              url:"https://i.ytimg.com/vi/pk9-28HgxfE/maxresdefault.jpg"
          },
          {
              id:8,
              title:' Guster - Amsterdam',
              src:"https://archive.org/download/guster2005-11-12.flac16/guster2005-11-12d2t04.mp3",
              url:"https://i.ytimg.com/vi/vGEZoL2ZDLs/maxresdefault.jpg"
          }
      ],
       player: new Audio()
      }
  },
  methods:{
      play(song){
          if (typeof song.src != "undefined") {
        this.current = song;
        this.player.src = this.current.src;
      }
      this.player.play();
      this.player.addEventListener("ended", function(){
          this.index++
           if(this.index>this.songs.length-1){
             this.index=0;
         }
        this.current=this.songs[this.index]
         this.play(this.current)
      }.bind(this)
      )
       this.isPlaying = true;
      },
      pause(){
      this.player.pause();
      this.isPlaying=false;
    },
     prev(){
         if(this.index<0){
             this.index=this.songs.length-1;
         }
         this.index--
         this.current=this.songs[this.index]
         this.play(this.current)
     },
     next(){
         if(this.index>this.songs.length-1){
             this.index=0;
         }
         this.index++
        this.current=this.songs[this.index]
         this.play(this.current) 
     }
  },
  created(){
      this.current=this.songs[this.index]
      this.player.src=this.current.src
      //this.player.play()
  }
}
</script>
<style scoped>

img{
    width:100%;
    height:200px;
}
.card{
    padding:10px;
    margin:5px auto;
    height:98vh;
}
button{
    margin-left:10px;
    outline: none;
}
button:focus{
    outline: none;
}
.play,.pause{
    background:hsl(11, 80%, 63%);
    color:white;
    border:none;
    border-radius:50%;
    font-size:28px;
}
.prev,.next{
    border:none;
}

.btn{
    width:100%;
    margin-left:0px;
    border:none;
    margin-top:5px;
    background:hsl(11, 80%, 63%);
    color:white;
}
.btn:hover{
    color:white;
}
.btn:focus{
  outline:none;
}
</style>