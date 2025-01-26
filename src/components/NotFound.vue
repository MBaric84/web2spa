<template>
    <div>
        <h1>Sorry, {{ $route.params.catchAll }}
            is not found.</h1>
        Try <router-link to="/">home</router-link>
    </div>
</template>