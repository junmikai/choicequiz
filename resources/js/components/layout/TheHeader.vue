<template>
  <header>
    <div class="container text-center">
      <div id="app">
    <transition appear>
    <div v-show="show">
      <h1>3分でビジネスが学べる！</h1>
      <h1 id="sitetitle">BusiChoice</h1>
      </div>
      </transition>
    </div>
    </div>
    <nav class="navbar">
      <div class="container">
        <div class="navbar-header">
          <button
            type="button"
            class="navbar-toggle"
            data-toggle="collapse"
            data-target="#navbar-ex-collapse"
          >
            <span class="sr-only">Toggle navigation</span>
            <span class="icon-bar"></span>
            <span class="icon-bar"></span>
            <span class="icon-bar"></span>
          </button>
          <router-link class="navbar-brand" id="header-nav__home" to="/">ホーム</router-link>
        </div>
        <div class="collapse navbar-collapse" id="navbar-ex-collapse">
          <ul class="nav navbar-nav navbar-right" v-if="auth.length === 0">
            <li>
              <router-link id="header-nav__login" to="/login">ログイン</router-link>
            </li>
            <li>
              <router-link id="header-nav__register" to="/register">新規登録</router-link>
            </li>
          </ul>
          <ul class="nav navbar-nav navbar-right" v-if="auth.length !== 0">
            <li class="dropdown">
              <a
                href="#"
                class="dropdown-toggle navbar-brand"
                id="header-nav__name"
                data-toggle="dropdown"
                role="button"
                aria-expanded="false"
              >
                {{ auth.name }}
                <span class="caret"></span>
              </a>
              <ul class="dropdown-menu header-nav__drop-down" role="menu">
                <li>
                  <router-link class="navbar-brand; col-md-offset-1;" id="header-nav__mypage" to="/mypage">マイページ</router-link>
                  <a class="navbar-brand; col-md-offset-1;" style="cursor: hand; cursor:pointer;" id="header-nav__logout" @click="logout">ログアウト</a>
                  <form id="logout-form" action="/logout" method="POST" style="display: none;">
                    <input type="hidden" name="_token" :value="csrf" />
                  </form>
                </li>
              </ul>
            </li>
          </ul>
        </div>
      </div>
    </nav>
  </header>
</template>
<script>
export default {
  data() { 
    return {
       show: true,
       csrf: document
        .querySelector('meta[name="csrf-token"]')
        .getAttribute("content")
    };
  },
  props: {
    auth: {
      type: Object | Array
    }
  },
  methods: {
    logout() {
      document.querySelector("#logout-form").submit();
    }
  }
};
</script>