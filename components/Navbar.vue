<template>
  <nav>
    <div
      class="w-full text-center text-3xl font-bold bg-gray-500 text-white py-8"
    >
      Test Frontend
    </div>
    <ul
      class="flex justify-center space-x-8 py-6 text-lg font-bold text-gray-800"
    >
      <li
        :class="[
          'cursor-pointer hover:text-green-500',
          { 'text-green-500': $nuxt.$route.path === '/' },
        ]"
      >
        <NuxtLink to="/"> Home </NuxtLink>
      </li>
      <li
        :class="[
          'cursor-pointer hover:text-green-500',
          { 'text-green-500': $nuxt.$route.path === '/pokemon' },
        ]"
      >
        <NuxtLink to="/pokemon">Pokemon</NuxtLink>
      </li>
      <li
        :class="[
          'cursor-pointer hover:text-green-500',
          { 'text-green-500': $nuxt.$route.path === '/function1' },
        ]"
      >
        <NuxtLink to="/function1">Function1</NuxtLink>
      </li>
      <li
        :class="[
          'cursor-pointer hover:text-green-500',
          { 'text-green-500': $nuxt.$route.path === '/function2' },
        ]"
      >
        <NuxtLink to="/function2">Function2</NuxtLink>
      </li>
      <li
        :class="[
          'cursor-pointer hover:text-green-500',
          { 'text-green-500': $nuxt.$route.path === '/function3' },
        ]"
      >
        <NuxtLink to="/function3">Function3</NuxtLink>
      </li>
    </ul>
  </nav>
</template>
