<template>
  <v-layout
    column
    justify-center
    align-center
    :class="backgroundClass"
  >
    <v-flex
      xs12
      sm8
      md6
      pt-3
    >
      <div class="text-center">
        <img v-if="hasMonetization" src="/rich.svg" style="width:300px;">
        <img v-else src="/poor.svg" class="spin" style="width:300px;">
      </div>
      <v-card class="mt-3 mw640">
        <v-card-title class="headline">
          Test Web Monetization
        </v-card-title>
        <v-card-text>
          <p>This simple site tells you if you are sending money to a content creator via the <a href="https://webmonetization.com">web monetization api</a>. Something interesting will happen if you are monetizing this page. This site also contains a full demo of the Web Monetization Javascript API in action.</p>
          <hr>
          <p class="headline my-1" v-if="hasMonetization"><v-icon class="primary--text display-2">mdi-check-circle</v-icon> Monetization events have occurred on this page!</p>

          <p class="headline my-1" v-else><v-icon class="red--text text--darken-1 display-2">mdi-minus-circle</v-icon> No monetization events have occurred on this page.</p>
          <hr>
          <p class="mt-3">You can learn more about supporting creators with web monetization at <a href="https://coil.com">Coil.com</a>. Coil is a major sponsor of <a href="">Grant for the Web</a>.</p>
        </v-card-text>
      </v-card>
      <v-card class="mw640 mt-2">
        <v-card-title>Implementation</v-card-title>
        <v-card-text>
          <p>The simplest implementation of web monetization is to place a <span style="font-family:monospace">&lt;meta&gt;</span> tag in your HTML page like this:</p>
          <pre class="mb-3 pa-2" v-text='simpleSource' style="border:1px solid #ccc;"></pre>
          <v-card-actions>
            <v-spacer></v-spacer>
            <v-btn class="primary" v-clipboard="simpleSource">Copy Source</v-btn>
            <v-spacer></v-spacer>
          </v-card-actions>

          <p>You can get your payment pointer (<span style="font-family:monospace">$coil....</span>) at <a
            href="https://coil.com">coil.com</a> for free.</p>
          <p>For more complex implementations, you can review the <a href="https://coil.com/docs">developer docs</a> at coil.com or continue reading for some sample code.</p>
        </v-card-text>

      </v-card>

      <v-card class="mw640 mt-2">
        <v-card-title class="headline">Full API Demo</v-card-title>
        <v-card-text>
          <p>Here is a full demo of the Web Monetization API in action. For the best compatibility, it's written in ES5 with vanilla javascript.</p>
          <p>For this demo to work locally, you must run it from a <a href="https://developer.mozilla.org/en-US/docs/Learn/Common_questions/set_up_a_local_testing_server">localhost server</a> and not the file system.</p>
        </v-card-text>
        <v-card-actions>
          <v-spacer></v-spacer>
          <v-btn class="primary" to="/demo.html" target="_blank">run demo</v-btn>
          <v-btn class="primary" href="https://github.com/TheRoccoB/testwebmonetization/blob/master/static/demo.html">view on github</v-btn>
          <v-spacer></v-spacer>
        </v-card-actions>

        <v-card-text>
          <pre class="pa-3 ma-2" style="overflow-x:scroll; border:1px solid #ccc; height:300px;" v-text="demoHtml"></pre>
        </v-card-text>

        <v-card-actions>
          <v-spacer></v-spacer>
          <v-btn class="primary" v-clipboard="demoHtml">Copy Source</v-btn>

          <v-spacer></v-spacer>
        </v-card-actions>

      </v-card>
      <BookmarkletCard class="mw640 mt-2"></BookmarkletCard>

      <v-card class="mw640 my-2">
        <v-card-title class="headline">About this site</v-card-title>
        <v-card-text>
          <p>I'm Rocco Balsamo and I built this site. My <a href="https://simmer.io">html5 games platform</a>, SIMMER.io is the first one available that allows creators to <a href="https://simmer.io/">add web monetization</a> to their game via our simple UI.</p>
          <p>You can view the source for this site (or contribute!) <a href="https://github.com/TheRoccoB/testwebmonetization">on Github</a>.</p>
        </v-card-text>
      </v-card>


    </v-flex>
  </v-layout>
</template>

<script>

import demoHtml from '~/static/demo.html';
import BookmarkletCard from '~/components/BookmarkletCard';

export default {

  data () {
    return {
      hasMonetization: false,
      simpleSource:'<meta name="monetization"\n      content="$coil.xrptipbot.com/JABJLDXNSje7h_bY26_6wg">',
      demoHtml
    }
  },
  created(){
    if (process.browser){
      console.log(window.innerWidth, window.innerHeight);
      const m = window.document.monetization;
      if (m){
        m.addEventListener('monetizationstart', () => {
          this.hasMonetization = true;
        })
      }
    }

  },
  computed:{
    backgroundClass(){
      return {green:this.hasMonetization};
    }
  },
  components:{
    BookmarkletCard
  },
  head:{
    meta:[{
      name:'monetization',
      content:'$coil.xrptipbot.com/JABJLDXNSje7h_bY26_6wg'
    }]
  }
}
</script>
<style scoped>

  .mw640{
    max-width:640px;
  }

  .green{
    background-color:#3FC28D;
    transition:all 1s;
  }

  @keyframes spin {
    from{
      transform: rotateY(0deg);
    }
    to{
      transform: rotateY(360deg);
    }
  }
  .imageSpin{
    animation-name: spin;
    animation-timing-function: ease-in-out;
    animation-iteration-count: infinite;
    animation-duration: 2s;
  }
</style>

<!-- global style-->
<style>
  .code{
    font-family:monospace;
  }
</style>
