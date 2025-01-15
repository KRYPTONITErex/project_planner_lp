<template>
    <div>
        <h1>Add Project</h1>
    </div>

    <form action="">

        <h2>Add your project</h2>

        <label for="">project name</label>
        <input type="text" placeholder="Enter project name">

        <label for="">project details</label>
        <input type="text" placeholder="Enter project details">

        <label for="">project status</label>
        <input type="text" placeholder="Enter project status">

        <button type="submit">Add Project</button>

    </form>
</template>

<script>
export default {

}
</script>

<style scoped>

/* Overall body styling */
body {
    margin: 0;
    height: 100vh;
    background: linear-gradient(120deg, #cfcfcf, #06456e); /* Vibrant gradient background */
    font-family: 'Arial', sans-serif;
    color: #fff;
    display: flex;
    flex-direction: column;
    align-items: center;
    /* justify-content: center; */
}

/* Center content container */
div {
    /* text-align: center; */
    margin-bottom: 20px;
}

h1 {
    font-size: 2.5rem;
    font-weight: bold;
    text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.5);
}

/* Form styling */
form {
    background: rgba(255, 255, 255, 0.9); /* Slightly transparent white background */
    padding: 30px 40px;
    border-radius: 15px;
    box-shadow: 0px 8px 15px rgba(0, 0, 0, 0.2);
    /*width*/
    width: 400px;
    margin: 0 auto;
    display: flex;
    flex-direction: column;
    /* align-items: center; */


}

/* Headings inside the form */
form h2 {
    font-size: 1.8rem;
    color: #333;
    margin-bottom: 20px;
    text-align: center;
}

/* Labels styling */
form label {
    display: block;
    font-weight: bold;
    font-size: 14px;
    margin-bottom: 10px;
    color: #555;
   
}

/* Input field styling */
form input[type="text"] {
    width: 90%;
    padding: 10px;
    margin: 10px auto 20px auto; /* Center horizontally */
    border: 1px solid #ddd;
    border-radius: 10px;
    font-size: 14px;
    box-shadow: inset 0 2px 5px rgba(0, 0, 0, 0.1);
    transition: border-color 0.3s ease-in-out;
    display: block;
    color: #555;;

    
}

form input[type="text"]:focus {
    outline: none;
    border-color: #6a11cb;
    box-shadow: 0px 0px 8px rgba(106, 17, 203, 0.5);
}

/* Submit button styling */
form button[type="submit"] {
    width: 70%;
    padding: 12px 20px;
    font-size: 16px;
    font-weight: bold;
    color: #fff;
    background: linear-gradient(120deg, #6a11cb, #2575fc);
    border: none;
    border-radius: 10px;
    cursor: pointer;
    transition: background 0.3s ease-in-out;
    display: block;
    align-items: center;
    margin: auto;
}

form button[type="submit"]:hover {
    background: linear-gradient(120deg, #2575fc, #6a11cb);
}

</style>