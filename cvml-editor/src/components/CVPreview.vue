<template>
    <div class="w-1/2 bg-neutral-800 p-4 shadow rounded-lg">
      <h2 class="text-xl font-semibold mb-4">Preview</h2>
      <pre class="p-4 rounded text-left bg-base-300 overflow-auto h-96">{{ formattedYaml }}</pre>
    </div>
  </template>
  
  <script>
  import yaml from 'js-yaml';
  import { computed, defineComponent } from 'vue';
  
  export default defineComponent({
    props: ['cvData'],
    computed: {
      formattedYaml() {
        return yaml.dump(this.cvData);
      }
    }
  });
  </script>
  
  