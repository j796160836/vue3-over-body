<script>
import overBody from "./components/vue-over-body.vue";
// import VueGitHubCorners from "vue-gh-corners";

export default {
  name: "App",
  components: {
    "vue-over-body": overBody,
    // "github-corners": VueGitHubCorners,
  },
  methods: {
    showSidebar: function () {
      this.$data.sidebar = this.$data.index;
      this.$data.index += 2;
    },
    showModal: function () {
      this.$data.modal = this.$data.index;
      this.$data.index += 2;
    },
    showNotification: function () {
      this.$data.notification = this.$data.index;
      this.$data.index += 2;
    },
  },
  data: function () {
    return {
      index: 1,
      modal: 0,
      sidebar: 0,
      notification: 0,
      dim: true,
    };
  },
};
</script>

<template>
  <!-- <github-corners repo="marcodpt/vue-over-body"> </github-corners> -->
  <section class="hero is-light">
    <div class="hero-body">
      <div class="container">
        <h1 class="title">Vue Over Body!</h1>
        <h2 class="subtitle">
          Create modals, sidebars, notifications, pop ups with css transitions!
        </h2>
        <button class="button is-primary" @click="showSidebar">
          Show Sidebar
        </button>
        <button class="button is-info" @click="showModal">Show Modal</button>
        <button class="button is-warning" @click="showNotification">
          Show Notication
        </button>
      </div>
    </div>
  </section>
  <vue-over-body
    :dim="dim"
    :open="modal"
    before="modalBefore"
    after="modalAfter"
  >
    <div class="modal-card">
      <header class="modal-card-head">
        <p class="modal-card-title">Modal title</p>
        <button class="delete" @click="modal = 0"></button>
      </header>
      <section class="modal-card-body">
        <p class="title">
          “There are two hard things in computer science: cache invalidation,
          naming things, and off-by-one errors.”
        </p>
        <p class="subtitle">Jeff Atwood</p>
      </section>
      <footer class="modal-card-foot">
        <button class="button is-success">Save changes</button>
        <button class="button">Cancel</button>
      </footer>
    </div>
  </vue-over-body>
  <vue-over-body
    :dim="dim"
    :open="sidebar"
    before="sideBefore"
    after="sideAfter"
  >
    <div style="padding: 10px; background-color: #f8f8f8; min-height: 100%">
      <aside class="menu">
        <p class="menu-label">General</p>
        <ul class="menu-list">
          <li><a>Dashboard</a></li>
          <li><a>Customers</a></li>
        </ul>
        <p class="menu-label">Administration</p>
        <ul class="menu-list">
          <li><a>Team Settings</a></li>
          <li>
            <a class="is-active">Manage Your Team</a>
            <ul>
              <li><a>Members</a></li>
              <li><a>Plugins</a></li>
              <li><a>Add a member</a></li>
            </ul>
          </li>
          <li><a>Invitations</a></li>
          <li><a>Cloud Storage Environment Settings</a></li>
          <li><a>Authentication</a></li>
        </ul>
        <p class="menu-label">Transactions</p>
        <ul class="menu-list">
          <li><a>Payments</a></li>
          <li><a>Transfers</a></li>
          <li><a>Balance</a></li>
        </ul>
      </aside>
    </div>
  </vue-over-body>
  <vue-over-body
    :dim="false"
    :open="notification"
    before="notificationBefore"
    after="notificationAfter"
  >
    <div class="notification is-warning">
      <button class="delete" @click="notification = 0"></button>
      <p>A little alert message!</p>
      <p>For the users of your app!</p>
    </div>
  </vue-over-body>
</template>

<style>
.modalBefore {
  top: -300px;
  margin: auto;
}

.modalAfter {
  top: 200px;
}

.sideBefore {
  height: 100%;
  width: 300px;
  top: 0;
  left: -300px;
}

.sideAfter {
  left: 0;
}

.notificationBefore {
  top: 50px;
  width: 300px;
  right: -300px;
  position: absolute;
}

.notificationAfter {
  right: 50px;
}
</style>
