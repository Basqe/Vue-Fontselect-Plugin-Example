<template>
  <div>
    <h1>{{title}}</h1>
    <div @click="expandList" class="font-selector">
        <span :style="changeStyle(selected)">{{fontName}}<span :class="{arrowUp: selectUp}" class="arrowDown" ></span></span>
      <ul v-if="showList"
          @click="expandList"
          class="font-select">
        <li v-for="font in fonts"
            @click="changeFont(font)"
            :key="font"
            :style="changeStyle(font)">
          {{font}}
        </li>
      </ul>
    </div>
    <p :style="changeStyle(selected)">Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.</p>
</div>
</template>

<script>
  const fonts =  [
        "Aclonica",
        "Allan",
        "Annie+Use+Your+Telescope",
        "Anonymous+Pro",
        "Allerta+Stencil",
        "Allerta",
        "Amaranth",
        "Anton",
        "Architects+Daughter",
        "Arimo",
        "Artifika",
        "Arvo",
        "Asset",
        "Astloch",
        "Bangers",
        "Bentham",
        "Bevan",
        "Bigshot+One",
        "Bowlby+One",
        "Bowlby+One+SC",
        "Brawler",
        "Buda:300",
        "Cabin",
        "Calligraffitti",
        "Candal",
        "Cantarell",
        "Cardo",
        "Carter One",
        "Caudex",
        "Cedarville+Cursive",
        "Cherry+Cream+Soda",
        "Chewy",
        "Coda",
        "Coming+Soon",
        "Copse",
        "Corben:700",
        "Cousine",
        "Covered+By+Your+Grace",
        "Crafty+Girls",
        "Crimson+Text",
        "Crushed",
        "Cuprum",
        "Damion",
        "Dancing+Script",
        "Dawning+of+a+New+Day",
        "Didact+Gothic",
        "Droid+Sans",
        "Droid+Sans+Mono",
        "Droid+Serif",
        "EB+Garamond",
        "Expletus+Sans",
        "Fontdiner+Swanky",
        "Forum",
        "Francois+One",
        "Geo",
        "Give+You+Glory",
        "Goblin+One",
        "Goudy+Bookletter+1911",
        "Gravitas+One",
        "Gruppo",
        "Hammersmith+One",
        "Holtwood+One+SC",
        "Homemade+Apple",
        "Inconsolata",
        "Indie+Flower",
        "IM+Fell+DW+Pica",
        "IM+Fell+DW+Pica+SC",
        "IM+Fell+Double+Pica",
        "IM+Fell+Double+Pica+SC",
        "IM+Fell+English",
        "IM+Fell+English+SC",
        "IM+Fell+French+Canon",
        "IM+Fell+French+Canon+SC",
        "IM+Fell+Great+Primer",
        "IM+Fell+Great+Primer+SC",
        "Irish+Grover",
        "Irish+Growler",
        "Istok+Web",
        "Josefin+Sans",
        "Josefin+Slab",
        "Judson",
        "Jura",
        "Jura:500",
        "Jura:600",
        "Just+Another+Hand",
        "Just+Me+Again+Down+Here",
        "Kameron",
        "Kenia",
        "Kranky",
        "Kreon",
        "Kristi",
        "La+Belle+Aurore",
        "Lato:100",
        "Lato:100italic",
        "Lato:300",
        "Lato",
        "Lato:bold",
        "Lato:900",
        "League+Script",
        "Lekton",
        "Limelight",
        "Lobster",
        "Lobster Two",
        "Lora",
        "Love+Ya+Like+A+Sister",
        "Loved+by+the+King",
        "Luckiest+Guy",
        "Maiden+Orange",
        "Mako",
        "Maven+Pro",
        "Maven+Pro:500",
        "Maven+Pro:700",
        "Maven+Pro:900",
        "Meddon",
        "MedievalSharp",
        "Megrim",
        "Merriweather",
        "Metrophobic",
        "Michroma",
        "Miltonian Tattoo",
        "Miltonian",
        "Modern Antiqua",
        "Monofett",
        "Molengo",
        "Mountains of Christmas",
        "Muli:300",
        "Muli",
        "Neucha",
        "Neuton",
        "News+Cycle",
        "Nixie+One",
        "Nobile",
        "Nova+Cut",
        "Nova+Flat",
        "Nova+Mono",
        "Nova+Oval",
        "Nova+Round",
        "Nova+Script",
        "Nova+Slim",
        "Nova+Square",
        "Nunito:light",
        "Nunito",
        "OFL+Sorts+Mill+Goudy+TT",
        "Old+Standard+TT",
        "Open+Sans:300",
        "Open+Sans",
        "Open+Sans:600",
        "Open+Sans:800",
        "Open+Sans+Condensed:300",
        "Orbitron",
        "Orbitron:500",
        "Orbitron:700",
        "Orbitron:900",
        "Oswald",
        "Over+the+Rainbow",
        "Reenie+Beanie",
        "Pacifico",
        "Patrick+Hand",
        "Paytone+One",
        "Permanent+Marker",
        "Philosopher",
        "Play",
        "Playfair+Display",
        "Podkova",
        "PT+Sans",
        "PT+Sans+Narrow",
        "PT+Sans+Narrow:regular,bold",
        "PT+Serif",
        "PT+Serif Caption",
        "Puritan",
        "Quattrocento",
        "Quattrocento+Sans",
        "Radley",
        "Raleway:100",
        "Redressed",
        "Rock+Salt",
        "Rokkitt",
        "Ruslan+Display",
        "Schoolbell",
        "Shadows+Into+Light",
        "Shanti",
        "Sigmar+One",
        "Six+Caps",
        "Slackey",
        "Smythe",
        "Sniglet:800",
        "Special+Elite",
        "Stardos+Stencil",
        "Sue+Ellen+Francisco",
        "Sunshiney",
        "Swanky+and+Moo+Moo",
        "Syncopate",
        "Tangerine",
        "Tenor+Sans",
        "Terminal+Dosis+Light",
        "The+Girl+Next+Door",
        "Tinos",
        "Ubuntu",
        "Ultra",
        "Unkempt",
        "UnifrakturCook:bold",
        "UnifrakturMaguntia",
        "Varela",
        "Varela Round",
        "Vibur",
        "Vollkorn",
        "VT323",
        "Waiting+for+the+Sunrise",
        "Wallpoet",
        "Walter+Turncoat",
        "Wire+One",
        "Yanone+Kaffeesatz",
        "Yanone+Kaffeesatz:300",
        "Yanone+Kaffeesatz:400",
        "Yanone+Kaffeesatz:700",
        "Yeseva+One",
        "Zeyada"
];
  export default{
    data() {
      return{
        title:'Vue Fontselect Plugin Example',
        selected: '',
        fonts: fonts,
        showList: false,
        fontName: "Select a font",
        styleFont: '',
        selectUp: false
      }
    },
    methods: {
      changeStyle(font){
        const slicer = font.indexOf(':');
        return ~slicer ?
          this.styleFont = {fontFamily: font.slice(0,slicer), fontWeight: font.slice(slicer+1,slicer+4)} :
          this.styleFont={fontFamily: font, fontWeight: 400};
      },
      expandList(){
      this.selectUp = !this.showList;
      this.showList = !this.showList;
      },
    changeFont(value){
      this.fontName= value;
      this.selected = this.fontName;
      this.showList = false;
      }
    },
    created(){
        const link = document.createElement('link');
        link.type = "text/css";
        link.rel = "stylesheet";
        link.href = `https://fonts.googleapis.com/css?family=${fonts.join().replace(/,/g , '|')}`;
        document.head.appendChild(link);
        this.fonts.forEach((el, i, arr) =>
          arr[i] = el.replace(/\+/g, " ")
        )
    }
  }
</script>

<style>

.font-selector {
  position: relative;
  background-color: white;
  width: 210px;
  border: 1px solid black;
  -webkit-border-radius: 5px;
  -moz-border-radius: 5px;
  border-radius: 5px;
  padding: 5px;
  cursor: pointer;
}


.arrowDown {
  float: right;
  background-image: url(/images/fs-sprite.png);
  background-position: 15% -50%;
  background-repeat: no-repeat;
  width: 5%;
  height: 30px;
}

.arrowDown::after,
.arrowDown::before {
  content: '';
  clear: both;
}

.arrowUp {
  float: right;
  background-image: url(/images/fs-sprite.png);
  background-position: 85% -50%;
  background-repeat: no-repeat;
  width: 5%;
  height: 30px;
}

.font-select {
  box-sizing: border-box;
  position: absolute;
  background-color: white;
  width: 210px;
  list-style-type: none;
  margin: 0;
  padding-left: 4px;
  left: 0;
  max-height: 180px;
  width: 100%;
  overflow-y: scroll;
  -webkit-border-radius: 0 0 5px 5px;
  -moz-border-radius: 0 0 5px 5px;
  border-radius: 0 0 5px 5px;
  border-right: 2px solid rgb(170, 170, 170);
  border-left: 2px solid white;
}

ul > li {
  padding-top: 5px;
  padding-bottom: 5px;
}

ul > li:hover {
  background-color: #5F9EA0;
  color: white;
}

</style>
