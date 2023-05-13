<template>
    <header>
        <h1>{{ title }}</h1>
        <KI_BUTTON color='blue' text="Add Schedule"/>
    </header>
    
</template>

<script>
import KI_BUTTON from './Button'

export default {
    name: 'KI_HEADER',
    props: {
        title: {
            type: String,
        }
    },
    components: {
        KI_BUTTON
    }
}
</script>


<style scoped>
header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 20px;
}
</style>