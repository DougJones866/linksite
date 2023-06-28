<template>
  <div id="app">
    <header></header>
    <div class="maincontainer">
      <div class="header__icon-box">
        <img
          src="/images/avatar1.png"
          alt="icon"
          class="header__icon"
        />
        <h3>Name Goes Here</h3>
        <button @click="linkAdd = !linkAdd">Add Link</button>

        <div class="linkForm" v-if="linkAdd">
          <form @submit.prevent="submitData">
            <input v-model="enteredTitle" placeholder="title" name="title" />
            <input v-model="enteredUrl" placeholder="URL" />
            <input class="inputbutton" type="submit" value="Submit" />
          </form>
        </div>
      </div>
      <div class="container">
        <div class="linkbox">
          <a
            :href="link.href"
            class="link"
            v-for="link in links"
            :key="link.href"
            @click="goTo($event, link.href)"
          >
            {{ link.name }}
          </a>
        </div>
      </div>

      <footer>
        <ul class="icons">
          <li><box-icon type="logo" name="github" color="white"></box-icon></li>
          <li>
            <box-icon name="linkedin" type="logo" color="white"></box-icon>
          </li>
          <li>
            <box-icon name="codepen" type="logo" color="white"></box-icon>
          </li>
        </ul>
      </footer>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      linkAdd: false,
      links: [
        { name: "Twitter", href: "http://www.twitter.com" },
        { name: "Github", href: "http://www.github.com" },
        { name: "Linkedin", href: "http://www.linkedin.com" },
        { name: "Patreon", href: "http://www.linkedin.com" },
        { name: "Linkedin", href: "http://www.linkedin.com" },
      ],
      enteredTitle: "",
      enteredUrl: "",
    };
  },
  methods: {
    goTo(e, href) {
      e.preventDefault();
      window.open(href);
    },
    submitData() {
      this.links.push({ name: this.enteredTitle, href: this.enteredUrl });
    },
  },
};
</script>

<style scoped>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

header {
  color: white;
  padding: 5px;
  display: flex;
  justify-content: center;
}
.maincontainer {
  display: flex;
  padding: 25px;
}
.container {
  flex: 50%;
  justify-content: center;
  padding: 100px;

  color: white;
}

.linkbox {
  display: flex;
  flex-direction: column;
}
input {
  display: block;
  margin: 1px;
}

.link {
  border-radius: 25px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  padding: 15px;
  margin-bottom: 15px;
  border-bottom: solid black 6px;
  border-right: solid black 6px;
  background-color: #2ed16a;
  color: white;
  text-decoration: none;
  text-transform: uppercase;
  transition: all 0.15s;
}

.link:hover {
  background-color: #532c6e;
}

a {
  font-family: "Roboto", sans-serif;
  font-weight: 900;
}

.header__icon-box {
  flex: 50%;

  position: relative;
}

.header__icon-box img {
 
  max-width: 400px;
  height: 300px;
 
  margin-top: 75px;
}

footer {
  position: fixed;
  left: 0;
  bottom: 0;
  right: 0;
  background-color: black;
  color: white;
}

.icons li {
  list-style: none;
  display: inline-flex;
}

@media only screen and (max-width: 500px) {
  .maincontainer {
    display: flex;
    flex-direction: column;
    justify-content: center;
    wrap: nowrap;
  }

  .linkbox {
  }
  .link {
    width: 100%;
  }
}

button {
  border-radius: 25px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  padding: 15px 25px;
  margin-bottom: 15px;
  border: none;
  border-bottom: solid black 6px;
  border-right: solid black 6px;
  background-color: #2ed16a;
  color: white;
  text-decoration: none;
  text-transform: uppercase;
}

button:hover {
  transition: all 0.15s;
  background-color: #532c6e;
}

form {
  transition: all 0.45s;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

.linkForm {
  display: flex;
  align-items: center;
  justify-content: center;
}

.inputbutton {
  background-color: orangered;
  border-radius: 25px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  padding: 15px 25px;
  margin: 15px;
  border: none;
  border-bottom: solid black 6px;
  border-right: solid black 6px;
  color: white;
  text-decoration: none;
  text-transform: uppercase;
}

input {
  padding: 10px;
  border: solid 1px;
}
</style>
