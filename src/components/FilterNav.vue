<template>

  <nav class="filter-nav">
    <button @click="filterby('All')" :class="{'active': current === 'All'}">all</button>
    <button @click="filterby('Completed')" :class="{'active': current === 'Completed'}">completed</button>
    <button @click="filterby('Ongoing')" :class="{'active': current === 'Ongoing'}">onging</button>
  </nav>

  <hr>
  
</template>

<script>

export default {
    props: ['current'],

    methods: {
        filterby(value){
            // console.log(value)
            this.$emit('filtervalue', value)
    }
}
}
</script>

<style scoped>
/* Navigation bar container */
.filter-nav {
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: #99a6bd; /* Navbar background color */
  padding: 8px 15px; /* Thin padding for a slim look */
  border-radius: 5px 10px 20px 5px; /* Slight rounding */
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1); /* Subtle shadow */
}

/* Buttons inside the navbar */
.filter-nav button {
  font-size: 1rem;
  font-family: 'Poppins', sans-serif;
  background: none;
  border: none;
  color: #ffffff;
  font-weight: 600;
  padding: 5px 15px;
  margin: 0 5px;
  cursor: pointer;
  transition: color 0.3s ease-in-out, background-color 0.3s ease-in-out;
  border-radius: 3px;
}

/* Hover effect for buttons */
.filter-nav button:hover {
  background-color: rgba(255, 255, 255, 0.2); /* Light hover background */
  color: #ffdd57; /* Highlight text on hover */
}

/* Active button style */
.filter-nav button:active {
  background-color: rgba(255, 255, 255, 0.3); /* Slightly darker hover */
  color: #ffd700; /* Highlighted text color */
  transform: scale(0.95); /* Slight shrink on click */
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.2); /* Subtle shadow on click */

}

.filter-nav button.active {
  background-color: crimson; /* Slightly darker hover */
  color: #ffffff; /* Highlighted text color */
  text-transform: uppercase;
}

/* Responsiveness */
@media (max-width: 600px) {
  .filter-nav {
    flex-wrap: wrap; /* Allow wrapping on smaller screens */
    gap: 5px; /* Space between buttons */
  }

  .filter-nav button {
    font-size: 0.9rem; /* Slightly smaller text on mobile */
    padding: 5px 10px;
  }
}
</style>