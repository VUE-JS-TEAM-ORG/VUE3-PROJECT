<template><h1>Vue 3 and Fetch Example</h1> 
  <ul v-if="!loading && data && data.length">
    <li v-for="post of data">
      <p><strong>zzzzzzzzz</strong></p>
      <p></p>
    </li>
  </ul>

  <p v-if="loading">
    Still loading..
  </p>
  <p v-if="error">


  </p>
</template> 

<script lang="ts">

import { ref, computed, onMounted,   } from "vue";   
export default {
  name: 'Posts',
  props: {
  },
  setup() {
    const data = ref(null);
    const loading = ref(true);
    const error = ref(null);

       function fetchData() {
        loading.value = true;
        // I prefer to use fetch
        // you can use use axios as an alternative
        return fetch('http://jsonplaceholder.typicode.com/posts', {
          method: 'get',
          headers: {
            'content-type': 'application/json'
          }
        })
          .then(res => {
            // a non-200 response code
            if (!res.ok) {
              // create error instance with HTTP status text
              const error = new Error(res.statusText);
              error.json = res.json();
              throw error;
            }  
            return res.json();
          })
          .then((json:any) => {
            // set the response data
            // data.value = json.data;
            console.log("fitch data")
          })
          .catch(err => {
            error.value = err;
            // In case a custom JSON error response was provided
            if (err.json) {
              return err.json.then((json:any) => {
                // set the JSON response message
               // error.value.message = json.message;
              });
            }
          })
          .then(() => {
            loading.value = false;
          });
      }
  

    onMounted(() => {
      fetchData();
    });

    return {
      data,
      loading,
      error
    };
  }
}
</script>