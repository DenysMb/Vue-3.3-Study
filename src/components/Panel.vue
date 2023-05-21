<script setup lang="ts">
// Since the `inheritAttrs` is setted as false in `defineOptions`, it will not inherit any attribute
// from parent component. So, in this example, the `class` attribute will not be inherited.
// If we set it to true, we'll inherit the class 'this-class-wont-show-because-of-inherit-attrs-false'.
defineOptions({ inheritAttrs: false })
</script>

<template>
    <div class="border border-pink-500 border-solid p-4 w-80 h-40 flex flex-col items-center justify-center gap-4 shadow">
        <h1>A Panel component to test `defineOptions`</h1>
    </div>
</template>