<template>
  <div>
    <ul>
      <li v-for="color of colors" :key="color" @click="$colorMode.preference = color" >
        <component
          :is="`icon-${color}`"
          
          
        />
      </li>
    </ul>
  </div>
</template>
<script>
import IconSystem from '@/assets/icons/system.svg?inline'
import IconLight from '@/assets/icons/light.svg?inline'
import IconDark from '@/assets/icons/dark.svg?inline'
import IconSepia from '@/assets/icons/sepia.svg?inline'

export default {
    data () {
    return {
      colors: ['system', 'light', 'dark', 'sepia']
    }
  },
  methods: {
    getClasses (color) {
      // Does not set classes on ssr preference is system (because we know them on client-side)
      if (this.$colorMode.unknown) {
        return {}
      }
      return {
        prefered: color === this.$colorMode.preference,
        selected: color === this.$colorMode.value
      }
    }
  }
  
}
</script>
<style scoped>
.feather {
  position: relative;
  top: 0px;
  cursor: pointer;
  padding: 7px;
  background-color: var(--bg-secondary);
  border: 2px solid var(--border-color);
  margin: 0;
  border-radius: 5px;
  transition: all 0.1s ease;
}
.feather:hover {
  top: -3px;
}
.feather.prefered {
  border-color: var(--color-primary);
  top: -3px;
}
.feather.selected {
  color: var(--color-primary);
}
</style>