<template>
    <div class="card">
        <h1> {{ name }}</h1>
        <h2>Student Profile</h2>
        <div class="card">
            <img v-bind:src="profile_picture" v-bind:alt="name" width="">
            <h3>{{ degree }}</h3>
            <p>Contact: <a href="mailto:">{{ contact }}</a></p>
            <h3>Education: {{ education }}</h3>
        </div>
    </div>
</template>

<script>
export default {
    props: ["name", "profile_picture", "education", "contact", "degree"],
}

</script>


<style>
body {
    font-family: Arial, sans-serif;
}

.container {
    max-width: 800px;
    margin: 0 auto;
}

h1 {
    text-align: center;
    margin-top: 50px;
}

h2 {
    margin-top: 30px;
}

.card {
    background-color: #f1f1f1;
    padding: 20px;
    border-radius: 5px;
    box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2);
    margin-top: 30px;
}

.card img {
    width: 50px;
    border-radius: 50%;
}

.card h3 {
    margin-top: 30px;
    text-align: center;
}

.card p {
    margin-top: 10px;
    text-align: justify;
}

.card a {
    text-decoration: none;
    color: blue;
}
</style>