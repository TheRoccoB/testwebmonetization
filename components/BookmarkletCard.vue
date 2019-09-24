<template>
  <v-card id="bookmarklet">
    <v-card-title class="headline">Bookmarklet for Testing</v-card-title>
    <v-card-text>
      <p>Don't have a paid coil account? Here is a bookmarklet for testing.</p>

<!--      <video width="320" height="240" controls>-->
<!--        <source src="/static/images/bm.mp4" type="video/mp4">-->
<!--      </video>-->

      <ol class="mb-3">
        <li>Make sure the Coil extension (<a href="https://chrome.google.com/webstore/detail/coil/locbifcbeldmnphbgkdigjmkbfkhbnca">Chrome</a> |
          <a href="https://addons.mozilla.org/en-US/firefox/addon/coil/">Firefox</a>) is installed. You don't need to log in.</li>
        <li>Drag <a class="white--text text--darken-2 pa-1 mx-1" style="text-decoration:none; border:1px dashed grey" :href="simulateBookmarklet">Simulate Monetization</a> onto your bookmarks bar.</li>
        <li>Go to a <a href="/demo.html">test page</a>.</li>
        <li>Click "Simulate Monetization" in your bookmarks bar.</li>
      </ol>

      <p>The bookmarklet sets <span class="code">document.monetization.state</span> to started, sends a <span class="code">monetizationstarted</span> event, and sends
        <span class="code">monetizationprogress</span> events every two seconds. Here is the source code:</p>

      <pre class="pa-3 ma-2" style="overflow-x:scroll; border:1px solid #ccc; height:300px;" v-text="simulateJS"></pre>

    </v-card-text>
    <v-card-actions>
      <v-spacer></v-spacer>
      <v-btn class="primary" v-clipboard="simulateJS">Copy Source</v-btn> <v-btn class="primary" href="https://github.com/TheRoccoB/testwebmonetization/blob/master/static/bookmarklet/simulateMonetization.js">view on github</v-btn>
      <v-spacer></v-spacer>
    </v-card-actions>
    <v-card-text><p>Hint: if you want to change parameters, you can run the <a href="/static/bookmarklet/simulateMonetization.js" style="inline-block">bookmarklet source code</a> as a script <a href="https://developers.google.com/web/tools/chrome-devtools/javascript/snippets">snippet</a> in Google Chrome.</p></v-card-text>
    <v-card-title class="headline">Is this an Exploit?</v-card-title>
    <v-card-text>
      <p>If anybody can run this bookmarklet from their browser, is it an exploit?</p>
      <p>In a way it is, but you can also independently verify that payments are made to your wallet with <a
        href="https://github.com/sharafian/web-monetization-access">Web Monetization access</a>.</p>

    </v-card-text>
  </v-card>
</template>

<script>
  import simulateJS from '~/static/bookmarklet/simulateMonetization';
  import simulateBookmarklet from '~/static/bookmarklet/simulateBookmarklet.txt';

  export default{
    data() {
      return {
        simulateJS,
        simulateBookmarklet
      }
    }
  }


</script>
