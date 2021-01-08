<template>
  <div>
    <header>{{ content.name }}</header>
    <section>
      <main>
      </main>
      <aside>
        <a :href="instagram"
          ><span><i class="fab fa-instagram"></i></span
        ></a>
        <a :href="twitter"
          ><span><i class="fab fa-twitter"></i></span
        ></a>
        <a :href="snapchat"
          ><span><i class="fab fa-snapchat"></i></span
        ></a>
        <a :href="email"
          ><span><i class="fas fa-envelope-square"></i></span
        ></a>
      </aside>
    </section>
    <nav>
      <ul>
        <li>HOME</li>
        <li>ABOUT</li>
        <li><img alt="Vue logo" src="../assets/brown_girl.png" /></li>
        <li>GALLERY</li>
        <li>CONTACT</li>
      </ul>
    </nav>
  </div>
</template>

<script>
export default {
  name: 'Home',
  data() {
    return {
      content: {
        name: '',
        twitter: '',
        instagram: '',
        snapchat: '',
        email: '',
        social_media: [],
      },
    };
  },
  created() {
    // fetch the aquilla API
    fetch('https://hirng-x2021.glitch.me/api')
      .then((response) => response.json())
      .then(({name, social_media}) => {
        this.content.name = name;
        this.content.twitter = social_media.twitter;
        this.content.instagram = social_media.instagram;
        this.content.snapchat = social_media.snapchat;
        this.content.email = social_media.email;
      })
      .catch(console.error);
  },
  computed: {
    twitter: function() {
      return 'https://www.twitter.com/' + this.content.twitter;
    },
    instagram: function() {
      return 'https://www.instagram.com/' + this.content.instagram;
    },
    snapchat: function() {
      return 'https://www.snapchat.com/' + this.content.snapchat;
    },
    email: function() {
      return 'mailto:' + this.content.email;
    },
  },
};
</script>

<style scoped>
header {
  height: 100px;
  padding: 10px;
  font-size: 38px;
  text-transform: uppercase;
}
section {
  height: 400px;
  align-items: center;
  display: flex;
}
section main {
  width: 50%;
  height: 100%;
  margin: 0px auto;
  border: 1px solid inherit;
  text-align: center;
  background: rgba(76, 175, 80, 0.6);
  background-image: url('../assets/girl4.jpeg');
  background-size: cover;
  background-repeat: no-repeat;
  background-position: 50% 15%;
  box-shadow: -1px 1px 22px -8px #3f3a3c;
  box-sizing: border-box;
}
section aside {
  display: flex;
  flex-direction: column;
  position: fixed;
  left: 90%;
  padding: 1em;
}
section aside a {
  padding: 0.4em;
}
section aside span {
  font-weight: 600;
  font-size: 2.4em;
  color: white;
}
nav ul {
  list-style-type: none;
  height: 100px;
  line-height: 100px;
  text-align: center;
}
nav li {
  display: inline-block;
  width: 50px;
  height: 50px;
  margin: 12px;
  padding: 12px;
  cursor: pointer;
  font-size: 18px;
}
nav li img {
  width: inherit;
  height: inherit;
  border-radius: 50%;
}
</style>
