<template>
  <nav id="nav" >
    <img src="../assets/Dasdas.png" alt="logo" />
    <ul id="nav__items" >
      <li><img src="../assets/twitter.svg" alt="twitter" class="nav__items-social" /> </li>
      <li>.</li>
      <li><img src="../assets/dribbble.svg" alt="dribble" class="nav__items-social" /> </li>
      <li>.</li>
      <li><img src="../assets/figma.svg" alt="figma" class="nav__items-social" /> </li>
      <li>.</li>
      <li><img src="../assets/github.svg" alt="github" class="nav__items-social" /> </li>
    </ul>
  </nav>
</template>

<script>
export default {
  name: 'NavBar'
}
</script>

<style lang="scss" scoped>
#nav {
  padding-top: 10px;
  margin-bottom: 66px;
  display: flex;
  justify-content: space-between;
  align-items: center;

  @media (max-width: 768px) {
    flex-direction: column;
  }

  &__items {
    display: flex;
    align-items: flex-start;
    gap: 8px;
    list-style: none;
  }
}
.nav__items-social {
  cursor: pointer;
}

.nav__items-social:hover {
  transition: 0.4s;
  transform: scale(1.4);
}
</style>