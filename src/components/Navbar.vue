<template>
        <nav class="main-nav">
            <router-link to="/">Projects</router-link>
            <router-link :to="{name: 'AddProject'}">Add Project</router-link>
        </nav>
</template>

<script>
export default {

}
</script>

<style>
/* General styling for the navigation bar */
.main-nav {
  background-color: #1e3c72; /* Dark gradient blue for the navbar */
  background: linear-gradient(135deg, #1e3c72, #2a5298);
  padding: 10px 20px;
  display: flex;
  justify-content: center; /* Centers the links horizontally */
  align-items: center; /* Vertically centers the content */
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  border-radius: 30px 5px 20px 5px;
}

/* Styling for the links */
.main-nav a {
  text-decoration: none; /* Remove underline */
  color: #ffffff; /* White text */
  font-size: 18px; /* Slightly larger text for readability */
  margin: 0 15px; /* Space between links */
  padding: 8px 12px; /* Padding for clickable area */
  border-radius: 8px; /* Rounded corners for hover effect */
  transition: background-color 0.3s, color 0.3s; /* Smooth hover effects */
}

/* Hover effect for links */
.main-nav a:hover {
  background-color: #ffffff; /* Highlight with white background */
  color: #1e3c72; /* Blue text */
  text-shadow: 0 1px 3px rgba(0, 0, 0, 0.2); /* Add a subtle text shadow */
}

/* Active link styling */
.main-nav a.router-link-active {
  background-color: #ffffff; /* Slightly darker background for active link */
  color: #004567; /* Light grey text for contrast */
  font-weight: bold;
}
</style>