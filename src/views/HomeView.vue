<template>

    <h1>Home</h1>

    <SingleProject></SingleProject>

</template>

<script>
import SingleProject from '../components/SingleProject'
export default {
  components: {
    SingleProject },

}
</script>

<style>

h1 {
    font-size: 2.5rem;
    font-weight: bold;
    text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.5);
}

</style>
