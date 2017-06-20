<template>
  <div class="container mt-2">
    <h3>Demo VueJS component VueSlideoutPanel</h3>
    <a href='https://github.com/lyollix/vue-slideout-panel'>
      View on github https://github.com/lyollix/vue-slideout-panel
    </a>
    <hr></br>
    <div>
      <h6><a @click="d1.v=true" href='#demo1'>Demo 1 /Simple 1-section/</a></h6>
      <pre>{{d1.code}}</pre>
    </div>
    <div>
      <h6><a @click="d2.v=true" href='#demo2'>Demo 2 /Simple 2-sections/</a></h6>
      <pre>{{d2.code}}</pre>
    </div>
    <div>
      <h6><a @click="d3.v=true" href='#demo3'>Demo 3 /Customizing/</a></h6>
      <pre>{{d3.code}}</pre>
    </div>
    <div>
      <h6><a @click="d4.v=true" href='#demo4'>Demo 4 /Customizing/</a></h6>
      <pre>{{d4.code}}</pre>
    </div>
    <div>
      <h6><a @click="d5.v=true" href='#demo5'>Demo 5 (+Demo 6) /Nested blocks/</a></h6>
      <pre>{{d5.code}}</pre>
    </div>

    <vue-slideout-panel v-model="d1.v" @close="d1.v=false">
         {{lorem}}
    </vue-slideout-panel>

    <vue-slideout-panel v-model="d2.v" :count=2 @close="d2.v=false">
         {{lorem}}
         <div slot="extra">{{lorem}}</div>
    </vue-slideout-panel>

    <vue-slideout-panel v-model="d3.v"
         closeHtml='<i class="ti-close" aria-hidden="true"></i>'
         :widths="['30%']"
         :styles="d3.styles"
         @close="d3.v=false">
         {{lorem}}
    </vue-slideout-panel>

    <vue-slideout-panel v-model="d4.v"
         :count=2
         :widths="['col-8', '60%']"
         :styles="[{padding:0},{padding:'1rem 1rem 4rem'},{same:true}]"
         :classes="['','bg-success','same']"
         closeHtml="<button class='btn btn-success'>Закрыть</button>"
         @close="d4.v=false">
         {{lorem}}
         <div slot="extra">{{lorem}}</div>
    </vue-slideout-panel>

    <vue-slideout-panel v-model="d5.v"
         :count=2
         :widths="['70%', '70%']"
         @close="d5.v=false">

         <div>
           <input type="checkbox" id="chb" v-model="d6.v">
           <label for="chb">Demo 6</label>
         </div>

         {{lorem}}

         <vue-slideout-panel v-model="d6.v"
              :widths="['40%']"
              @close="d6.v=false">
              {{lorem}}
         </vue-slideout-panel>

      <div slot="extra">{{lorem}}</div>

    </vue-slideout-panel>

    <footer class="footer mt-2">
      <div class="container">
        <p class="text-center">&copy; 2017 lyollix</p>
      </div>
    </footer>

  </div>
</template>

<script>
//  import VueSlideoutPanel from './components/VueSlideoutPanel'
  import VueSlideoutPanel from 'vue-slideout-panel'

  let lorem = "Lorem ipsum dolor sit amet, consectetur adipiscing elit,\
sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.\
Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.\
Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.\
Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum."

export default {
  name: 'app',

  mounted() {
    $('a[href*=\\#]').on('click', function(event){
        event.preventDefault();
        $('html,body').animate({scrollTop:$(this).offset().top}, 400);
    });
  },

  data() {
    return {
      value: 1,
      lorem: lorem,
      d1: {
        v:false,
        code:
`<vue-slideout-panel v-model="d1" @close="d1=false">
     {{lorem}}
</vue-slideout-panel>`
      },

      d2: {
        v:false,
        code:
`<vue-slideout-panel v-model="d2" :count=2 @close="d2=false">
     {{lorem}}
     <div slot="extra">{{lorem}}</div>
</vue-slideout-panel>`
      },

      d3: {
        v:false,
        styles: [
          {},
          {
            backgroundColor: '#ffc29c',
            paddingTop: '2rem',
            paddingBottom: '1rem'
          },
          {},
          {
            color: '#555',
            textDecoration: 'none',
            top: '8px',
            right: '1rem'
          }
        ],
        code:

`d3.styles: [
  {},
  {
    backgroundColor: 'lightyellow',
    paddingTop: '2rem',
    paddingBottom: '1rem'
  },
  {},
  {
    color: '#555',
    textDecoration: 'none',
    top: '8px',
    right: '1rem'
  }
],

<vue-slideout-panel v-model="d3.v"
     closeHtml='<i class="ti-close" aria-hidden="true"></i>'
     :widths="['30%']"
     :styles="d3.styles"
     @close="d3.v=false">
     {{lorem}}
</vue-slideout-panel>`

      },

      d4: {
        v:false,
        code:
`<vue-slideout-panel v-model="d4.v"
     :count=2
     :widths="['col-8','60%']"
     :styles="[{padding:0},{padding:'1rem 1rem 4rem'},{same:true}]"
     :classes="['','bg-success','same']"
     closeHtml="<button class='btn btn-success'>Закрыть</button>"
     @close="d4.v=false">
     {{lorem}}
     <div slot="extra">{{lorem}}</div>
</vue-slideout-panel>`
      },

      d5: {
        v:false,
        code:
`<vue-slideout-panel v-model="d5.v"
     :count=2
     :widths="['70%','70%']"
     @close="d5.v=false">

     <div>
       <input type="checkbox" id="chbx" v-model="d5.v">
       <label for="chbx">Demo 6</label>
     </div>

     {{lorem}}

     <vue-slideout-panel v-model="d6.v"
          :widths="['40%']"
          @close="d6.v=false">
          {{lorem}}
     </vue-slideout-panel>

     <div slot="extra">{{lorem}}</div>

</vue-slideout-panel>`
      },

      d6: {v:false}

    }
  },

  components: {
    VueSlideoutPanel
  }
}
</script>

<style>
  @font-face {
   font-family: themify;
   src: url(https://cdn.jsdelivr.net/themify-icons/0.1.2/fonts/themify.ttf);
  }
</style>

<style scoped>
  pre {
    font-size: 12px;
    display: inline-block;
    background-color: lightyellow;
    padding: 10px;
    border: 1px dotted black;
  }
</style>
