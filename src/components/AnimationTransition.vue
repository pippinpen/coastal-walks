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

<style lang="scss">
//Styling for all animation classes

//Starting styling
.slide-left {
  transform: translateX(-5vw);
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
  transform: translateX(5vw);
  opacity: 0;
  transition: transform 0.25s ease-in-out, opacity 0.25s ease-in-out;

  &.animate {
    transform: translateX(0);
    opacity: 1;
  }
}

.fade {
  opacity: 0.1;
  transition: opacity 0.3s ease;

  &.animate {
    opacity: 1;
  }
}

.hero {
  transform: translateX(0);
  opacity: 1;
  width: 100%;

  transition: transform 0.25s ease-in-out, opacity 0.25s ease-in-out, width 0.5s ease;

  .icon-sun {
    transform: translateX(2rem);
    opacity: 0;
    transition: transform 0.4s ease-in-out, opacity 0.25s ease-in-out;
  }

  .icon-bird-tiny {
    transform: translateX(2rem);
    opacity: 0;
    transition: transform 0.25s ease-in-out 0.225s, opacity 0.25s ease 0.225s;
  }

  .icon-bird-big {
    transform: translateX(2rem);
    opacity: 0;
    transition: transform 0.25s ease-in-out 0.25s, opacity 0.25s ease 0.25s;
  }

  .icon-bird-sml {
    transform: translateX(-4rem);
    opacity: 0;
    transition: transform 0.25s ease-in-out 0.35s, opacity 0.25s ease 0.35s;
  }

  .icon-scroll {
    transform: translateY(-2rem);
    opacity: 0;
    transition: transform 0.25s ease-in-out 0.4s, opacity 0.25s ease 0.4s;
  }

  .icon-rock-big {
    transform: translateX(2rem);
    opacity: 0;
    transition: transform 0.25s ease-in-out 0.45s, opacity 0.25s ease 0.45s;
  }
  .icon-rock-sml {
    transform: translateX(-2rem);
    opacity: 0;
    transition: transform 0.25s ease-in-out 0.48s, opacity 0.25s ease 0.48s;
  }

  .icon-lighthouse {
    transform: translateX(-2rem);
    opacity: 0;
    transition: transform 0.25s ease-in-out 0.5s, opacity 0.25s ease 0.5s;
  }

  &.animate {
    transform: translateX(0);
    opacity: 1;

    .icon-sun,
    .icon-bird-big,
    .icon-bird-tiny,
    .icon-bird-sml,
    .icon-rock-sml,
    .icon-lighthouse,
    .icon-rock-big {
      transform: translateX(0);
      opacity: 1;
    }

    .icon-scroll {
      transform: translateY(0);
      opacity: 1;
    }

  }
}
</style>