<template>
  
  <div class="filter-nav">
    <button @click="filterby('all')" :class="{ active: current === 'all' }">All</button>
    <button @click="filterby('completed')" :class="{ active: current === 'completed' }">Completed</button>
    <button @click="filterby('ongoing')" :class="{ active: current === 'ongoing' }">Ongoing</button>
  </div>
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
  background-color: #f8f9fa; /* Light gray background */
  padding: 10px 20px; /* Thin padding for a slim design */
  border-radius: 5px; /* Slight rounding */
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1); /* Subtle shadow */
  gap: 10px; /* Space between buttons */
}

/* Buttons inside the navbar */
.filter-nav button {
  background: #ffffff; /* White button background */
  border: 1px solid #ddd; /* Light border */
  color: #333; /* Text color */
  font-size: 0.9rem; /* Small font size */
  padding: 8px 15px; /* Compact padding */
  border-radius: 4px; /* Slightly rounded corners */
  cursor: pointer;
  transition: all 0.3s ease-in-out; /* Smooth transition for hover effects */
}

/* Hover effect for buttons */
.filter-nav button:hover {
  background-color: #e9ecef; /* Light hover background */
  border-color: #ccc; /* Slightly darker border on hover */
  color: #007bff; /* Highlight text on hover */
}

/* Active button style */
.filter-nav button:active {
  background-color: #007bff; /* Blue background on active */
  color: #ffffff; /* White text on active */
  border-color: #0056b3; /* Darker blue border on active */
}

/* Active button style */
.filter-nav button.active {
  background-color: #007bff; /* Blue background on active */
  color: #ffffff; /* White text on active */
  text-transform: uppercase;
}

/* Responsive adjustments */
@media (max-width: 768px) {
  .filter-nav {
    flex-wrap: wrap; /* Allow wrapping on smaller screens */
    gap: 5px; /* Reduce spacing between buttons */
  }

  .filter-nav button {
    font-size: 0.8rem; /* Slightly smaller text on mobile */
    padding: 6px 12px;
  }
}
</style>