<template>
    <h1 class="title">
      Welcome on ShortLink !
    </h1>


  <div class="tp2">
    <label for="linkInput">Enter long link :</label>
    <br/>
    <form @submit.prevent="shortenLink">
      <input type="text" id="linkInput" v-model="link" placeholder="Enter long link here">
      <button type="submit">Shorten URL</button>
    </form>
    <br/>
    <label for="linkInput">Shortcut link :</label>
    <br/>
    <!-- <input type="text" id="LinkShorted" v-model="res" readonly> -->
    <table>
      <tr>
        <td>
          <a :href="link" target="_blank"> {{ res }}</a>
        </td>
      </tr>
    </table>
  </div>
</template>

<script>

export default {
  data() {
    return {
      link: '' ,
      res: ''
    };
  },
  methods: {
    shortenLink() {
      if (this.link=='') {
      try {  
        throw new Error ('Une URL est nécessaire');
      } catch (error) {
        alert(error.message);
      }
    }
    else 
      if (!this.link.includes('.')) {
        try {  
        throw new Error ('Insérez une URL correcte');
      } catch (error) {
        alert(error.message);
      }
      }
    else {

      const base64 = 'ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789+/';
      let linkId = '';
      const linkSize = 8 ; // Afin de moduler la taille du Short Link
      const baseURL = "https://shortlink.com/" ;
      for (let i = 0; i < linkSize; i++) {
        linkId += base64.charAt(Math.floor(Math.random() * base64.length));
      }
      this.res = baseURL + linkId;  

      // let lastLink= this.link;
      // let lastLinkId = linkId;
      // if (this.link==lastLink) {
      //   linkId = lastLinkId;  
      // }
    }
  },
  }
};
</script>

<style>
.title {
  text-align: center;
}
table {
    margin: 0 auto;
    max-width: 5;
    width: 5cm;
    height: 1cm;
  }
  td {
    border: 1px solid #000000;
    padding: 5px; 
    text-align:left; 
  }
  tr {
    background-color: #c2c7c9; 
  }
.tp2 {
  text-align: center;
}
</style>

<!-- ------------------------------------------------------------------- -->

