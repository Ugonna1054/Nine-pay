<template>
  <div>
    <nuxt />
  </div>
</template>

<style>
@font-face {
  font-family: Montserrat-Regular;
  src: url('../assets/fonts/Montserrat-Regular.ttf');
}

@font-face {
  font-family: Montserrat-Medium;
  src: url('../assets/fonts/Montserrat-Medium.ttf');
}

@font-face {
  font-family: Montserrat-Light;
  src: url('../assets/fonts/Montserrat-Light.ttf');
}

@font-face {
  font-family: Montserrat-Bold;
  src: url('../assets/fonts/Montserrat-Bold.ttf');
}

html {
  font-family: 'Source Sans Pro', -apple-system, BlinkMacSystemFont, 'Segoe UI',
    Roboto, 'Helvetica Neue', Arial, sans-serif;
  font-size: 16px;
  word-spacing: 1px;
  -ms-text-size-adjust: 100%;
  -webkit-text-size-adjust: 100%;
  -moz-osx-font-smoothing: grayscale;
  -webkit-font-smoothing: antialiased;
  box-sizing: border-box;
}

*,
*:before,
*:after {
  box-sizing: border-box;
  margin: 0;
}

.button--green {
  display: inline-block;
  border-radius: 4px;
  border: 1px solid #3b8070;
  color: #3b8070;
  text-decoration: none;
  padding: 10px 30px;
}
</style>
