<script setup></script>
<template>
  <h1>Hi from {{ $route.params.blah && $route.params.blah[0] }}</h1>
</template>
