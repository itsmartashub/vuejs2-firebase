<template>
  <div id="app">
    <h1>{{ naslov }}</h1>
    <Navbar />
    <AllFriends :prijatelji="friends" v-on:brisanje="deleteFriend" /><!-- posto i za online prijatelje i za sve prijatelje nam treb ovaj niz friends, pa da ne stavljamo u svaku komponentu taj niz, stavili smo u ovu glavnu App.vue, i onda cemo da bajndujemo ovde u druge komponente sa :. Posle dvotacke mozemo koje god ime hocemo i potom u navodnicima stavljamo propery koji zelimo da koristimo u toj i toj komponenti. Da nismo stavili :, ovo friends ne bi bio property za ovaj niz vec obican string.
    Dakle, ovako prosledjujemo property, ali kako "PRIHVATAMO"/primamamo u komponentama? Pa preko props propertyja.
    JU! Meni nece sa ovim :prijatelji iako kao moze koji god naziv, kao mora friends. Joj budale, to je jer i u komponentama u v-for mora da pise taj kao i ovde friend in PRIJATELJI a ne friends
    Za evente mozemo koristiti v-on:brisanje ili @ simbol -->
    <OnlineFriends :prijatelji="friends"/>
    <hr>
    
    <Blog />
  </div>
</template>

<script>
import Nav from "./components/Navbar";
import AllFriends from './components/AllFriends';
import OnlineFriends from './components/OnlineFriends';
import Blog from './components/Blog'

export default {
  name: 'app',

  components: {
    Navbar: Nav,
    AllFriends: AllFriends, // AllFriends moze zbog es6
    OnlineFriends,
    Blog
  },

  data() {
    return {
      naslov: 'Cao, dobrodosla u Vue.js',
      friends: [
        { name: 'Pavle', online: true },
        { name: 'Marija', online: false },
        { name: 'Nina', online: true },
        { name: 'Marta', online: false }
      ]
    }
  },

  methods: {
    deleteFriend(payload) {
      // console.log(payload)
      this.friends = this.friends.filter(friend => {
        console.log(friend.name !== payload.ime);
        return friend.name !== payload.ime 
      }) // ako vrati true, zadrzava tog prijatelja unutar niza, ukoliko je false, filteruje tj izbacuje tog prijatelja iz niza. A sta zelimo da proverimo? Da li je ime iz ovog friends niza jednako imenu iz f-je deleteFriend tj iz payload. Ako je istoime, onda to znaci da sa filterom zelimo da vratimo false, tj da ga izbaci iz niza
      // console.log(this.friends);
    }
  }

}
</script>

<style>
h1 {
  font-family: 'Times New Roman'; 
  background: #eee;
  color: orangered;
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>
