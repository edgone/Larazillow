<template>
  <div
    class="border-2 border-gray-200 dark:border-gray-800 rounded-md p-4 shadow-md dark:text-gray-300 hover:bg-gray-800 hover:shadow-lg">
    <div class="text-gray-500 font-medium mb-1">
      <slot name="header"></slot>
    </div>
    <slot></slot>
  </div>
</template>