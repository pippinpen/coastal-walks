<template>
  <div ref="target" :class="`${ animate ? `animate ${ props.name }` : props.name }`">
    <slot></slot>
  </div>
</template>

<script setup>
  /* Imports */
  import { onMounted, onBeforeUnmount, ref } from "vue";

  /* Variables */
  // Name prop passed to this component will be the animation name
  const props = defineProps([ "name", "entryOnly" ]);

  // Targeting element to observe
  const target = ref(null);
  const animate = ref(false);

  /* Observer */
  // Watching for a page scroll past the threshold of 50% to add animating class defined in props
  const observer = new IntersectionObserver(
    ([ entry ]) => {

      // Only animate once on entry if entryOnly prop specified
      if (props.entryOnly) {
        if (entry.isIntersecting) {
          animate.value = true;
        }
      } else {
        // Animate on entry and exit
        animate.value = entry.isIntersecting ? true : false;
      }
    }, 
    {
      threshold: 0.5,
    }
  );

  /* Functions */
  // Adding watcher on component mount
  onMounted(() => {
    observer.observe(target.value)
  })

  // Removing watching on component unmount for performance
  onBeforeUnmount(() => {
    observer.disconnect();
  })

</script>

<style lang="scss" scoped>
//Styling for all animation classes

//Starting styling
.slide-left {
  transform: translateX(-0.5rem);
  opacity: 0;
  //Animation timing
  transition: transform 0.25s ease-in-out, opacity 0.25s ease-in-out;

  //Styling when animation active
  &.animate {
    transform: translateX(0);
    opacity: 1;
  }
}

.slide-right {
  transform: translateX(0.5rem);
  opacity: 0;
  transition: transform 0.25s ease-in-out, opacity 0.25s ease-in-out;

  &.animate {
    transform: translateX(0);
    opacity: 1;
  }
}

.hero {
    transform: translateX(2rem);
  opacity: 0;
  transition: transform 0.25s ease-in-out, opacity 0.25s ease-in-out;

  &.animate {
    transform: translateX(0);
    opacity: 1;
  }
}
</style>