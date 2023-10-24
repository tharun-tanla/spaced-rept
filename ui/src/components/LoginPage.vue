<template>
  <div class="main-container">
    <div class="description-container">
      <div class="description-sub-container">
        <h1 class="heading">Spaced Repetition</h1>
        <p class="description">
          Spaced repetition is an evidence-based learning technique that is
          usually performed with flashcards. Newly introduced and more difficult
          flashcards are shown more frequently, while older and less difficult
          flashcards are shown less frequently in order to exploit the
          psychological spacing effect.
        </p>
      </div>
    </div>
    <div class="login-container">
      <div class="login-form">
        <input type="text" name="" id="" />
        <v-btn class="ma-2 g-btn" @click="handleGoogleLogin">
          <v-icon class="mr-2">fa-brands fa-google </v-icon>
          <span style="color: blue">Login With Google</span>
        </v-btn>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "LogigenPage",
  methods: {
    async handleGoogleLogin() {
      console.log("google Login clicked");

      // Google's OAuth 2.0 endpoint for requesting an access token
      var oauth2Endpoint = "https://accounts.google.com/o/oauth2/v2/auth";

      // Create <form> element to submit parameters to OAuth 2.0 endpoint.
      var form = document.createElement("form");
      form.setAttribute("method", "GET"); // Send as a GET request.
      form.setAttribute("action", oauth2Endpoint);

      // Parameters to pass to OAuth 2.0 endpoint.
      var params = {
        client_id: "96389664731-ioblis7shfqfal11v7bertvvs6mnfui7.apps.googleusercontent.com",
        redirect_uri: "http://localhost:8081",
        response_type: "token",
        scope: "https://www.googleapis.com/auth/drive.metadata.readonly",
        include_granted_scopes: "true",
        state: "pass-through value",
      };

      // Add form parameters as hidden input values.
      for (var p in params) {
        var input = document.createElement("input");
        input.setAttribute("type", "hidden");
        input.setAttribute("name", p);
        input.setAttribute("value", params[p]);
        form.appendChild(input);
      }

      // Add form to page and submit it to open the OAuth 2.0 endpoint.
      document.body.appendChild(form);
      form.submit();
    },
  },
  data: () => ({}),
};
</script>
<style scoped>
.main-container {
  width: 100vw;
  height: 100vh;
  background-image: linear-gradient(to left, black, white);
  display: flex;
}
.description-container {
  width: 50vw;
  display: flex;
  align-items: center;
  justify-content: space-around;
}
.login-container {
  width: 50vw;
  display: flex;
  align-items: center;
  justify-content: space-around;
}
.description-sub-container {
  width: 30vw;
}
.heading {
  font-family: "Courier New", Courier, monospace;
  font-size: 70px;
  opacity: 0.5;
}
.description {
  font-family: "Franklin Gothic Medium", "Arial Narrow", Arial, sans-serif;
  font-size: 20px;
}
.g-btn {
  padding: 27px 22px !important;
}
.fa-google {
  background: conic-gradient(
      from -45deg,
      #ea4335 110deg,
      #4285f4 90deg 180deg,
      #34a853 180deg 270deg,
      #fbbc05 270deg
    )
    73% 55%/150% 150% no-repeat;
  -webkit-background-clip: text;
  background-clip: text;
  color: transparent;
  -webkit-text-fill-color: transparent;
}
</style>
