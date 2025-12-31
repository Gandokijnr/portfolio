<template>
  <div>
    <NuxtLayout>
      <NuxtPage />
    </NuxtLayout>
  </div>
</template>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

:root {
  --primary-50: #ffeae0;
  --primary-100: #ffd1b8;
  --primary-500: #ff6a3d;
  --primary-600: #ff4b3a;
  --primary-700: #e0363a;

  --accent-purple-500: #8a1eff;
  --accent-purple-700: #2b004f;

  --neutral-50: #fdf7ff;
  --neutral-100: #f4e9ff;
  --neutral-200: #d9c2ff;
  --neutral-300: #a89ac4;
  --neutral-600: #5b5270;
  --neutral-700: #3c3550;
  --neutral-800: #241c38;
  --neutral-900: #12051f;
  --neutral-950: #05000a;

  --spacing-xs: 0.5rem;
  --spacing-sm: 1rem;
  --spacing-md: 1.5rem;
  --spacing-lg: 2rem;
  --spacing-xl: 3rem;
  --spacing-2xl: 4rem;
  --spacing-3xl: 6rem;
}

html,
body {
  scroll-behavior: smooth;
}

body {
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, sans-serif;
  color: var(--neutral-50);
  line-height: 1.5;
  background:
    radial-gradient(circle at 0% 0%, rgba(255, 106, 61, 0.18), transparent 55%),
    radial-gradient(circle at 100% 100%, rgba(138, 30, 255, 0.45), transparent 55%),
    linear-gradient(135deg, #05000a 0%, #12051f 45%, #2b004f 80%);
  background-attachment: fixed;
  color-scheme: dark;
}

h1, h2, h3, h4, h5, h6 {
  line-height: 1.2;
  font-weight: 700;
}

h1 {
  font-size: 3rem;
  font-weight: 800;
}

h2 {
  font-size: 2.25rem;
}

h3 {
  font-size: 1.5rem;
}

p {
  line-height: 1.5;
}
</style>
