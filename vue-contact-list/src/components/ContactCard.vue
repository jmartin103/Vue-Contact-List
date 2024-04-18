<template>
  <div>
    <h2>{{ name }}</h2>
    <p>{{ address }}</p>
    <p>{{ phoneNumber }}</p>
    <p>{{ email }}</p>
  </div>
  <div>
    <button @click="$emit('delete')">Delete Contact</button>
  </div>
</template>

<script>
export default {
  props: ['name', 'address', 'phoneNumber', 'email']
}
</script>