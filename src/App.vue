<template>
  <div id="app">
    <tab-nav :tabs="tabs" @select="selectTab" :selected="selected">
      <tab-content :isSelected="selected === 'Tab 1'">
        <div class="card" style="width: 18rem">
          <img
            src="data:image/jpeg;base64,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"
            class="card-img-top"
            alt="vue logo"
          />
          <div class="card-body">
            <h5 class="card-title">Card title</h5>
            <p class="card-text">
              Some quick example text to build on the card title and make up the
              bulk of the card's content.
            </p>
            <a href="#" class="btn btn-primary">Go somewhere</a>
          </div>
        </div>
      </tab-content>
      <tab-content :isSelected="selected === 'Tab 2'">
        <form class="form-style">
          <div class="mb-3">
            <label for="exampleInputEmail1" class="form-label"
              >Email address</label
            >
            <input
              type="email"
              class="form-control"
              id="exampleInputEmail1"
              aria-describedby="emailHelp"
            />
            <div id="emailHelp" class="form-text">
              We'll never share your email with anyone else.
            </div>
          </div>
          <div class="mb-3">
            <label for="exampleInputPassword1" class="form-label"
              >Password</label
            >
            <input
              type="password"
              class="form-control"
              id="exampleInputPassword1"
            />
          </div>
          <div class="mb-3 form-check">
            <input
              type="checkbox"
              class="form-check-input"
              id="exampleCheck1"
            />
            <label class="form-check-label" for="exampleCheck1"
              >Check me out</label
            >
          </div>
          <button type="submit" class="btn btn-primary">Submit</button>
        </form>
      </tab-content>
      <tab-content :isSelected="selected === 'Tab 3'">
        <div class="alert alert-primary" role="alert">
          A simple primary alert—check it out!
        </div>
        <div class="alert alert-secondary" role="alert">
          A simple secondary alert—check it out!
        </div>
        <div class="alert alert-success" role="alert">
          A simple success alert—check it out!
        </div>
        <div class="alert alert-danger" role="alert">
          A simple danger alert—check it out!
        </div>
      </tab-content>
    </tab-nav>
  </div>
</template>

<script>
import TabContent from './components/Tabs/TabContent.vue';
import TabNav from './components/Tabs/TabNav.vue';

export default {
  data() {
    return {
      tabs: ['Tab 1', 'Tab 2', 'Tab 3'],
      selected: 'Tab 1',
    };
  },

  methods: {
    selectTab(tab) {
      this.selected = tab;
    },
  },

  components: { TabNav, TabContent },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  display: flex;
}

.form-style {
  border: 1px solid #ccc;
  padding: 2rem;
}
</style>
