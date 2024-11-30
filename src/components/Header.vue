<template>
  <header class="header_area">
    <div class="header-content">
      <!-- 왼쪽 상단 제목 -->
      <h1 class="logo">KMH's Portfolio</h1>

      <!-- 오른쪽 상단 네비게이션 -->
      <nav class="navbar" :class="{ 'is-active': isMenuOpen }">
        <button class="menu-toggle" @click="toggleMenu">
          <span v-if="!isMenuOpen">&#9776;</span>
          <span v-else>&times;</span>
        </button>
        <ul class="navbar-item">
          <li><a href="#aboutme">About me</a></li>
          <li><a href="#skills">Skills</a></li>
          <li><a href="#licenses">Licenses</a></li>
          <li><a href="#portfolio">Portfolio</a></li>
          <li><a href="#experiences">Experiences</a></li>
        </ul>
      </nav>
    </div>
    <!-- 중앙 큰 글씨 -->
    <div class="center-content">
      <h2>Welcome to My Portfolio</h2>
      <h3>열정을 다하는 개발자 김민호 입니다!</h3>
    </div>

  </header>
</template>

<script setup>
  import { ref, onMounted, onUnmounted } from 'vue';

  const isMenuOpen = ref(false);
  const toggleMenu = () => {
    isMenuOpen.value = !isMenuOpen.value;
  };

  
  const navbarClass = ref('');
  const handleScroll = () => {
    if (window.scrollY > 10) {
      navbarClass.value = 'scrolled';
    } else {
      navbarClass.value = '';
    }
  };

  // 마운트 시 이벤트 리스너 추가
  onMounted(() => {
    window.addEventListener('scroll', handleScroll);
  });

  // 언마운트 시 이벤트 리스너 제거
  onUnmounted(() => {
    window.removeEventListener('scroll', handleScroll);
  });
</script>

<style scoped>
  .header_area {
    position: relative;
    height: 50vh;
    background-image: url('@/assets/img/navbackground.jpg');
    background-size: cover;
    background-position: center;
    background-repeat: no-repeat;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    color: white;
    text-shadow: 0px 0px 10px rgba(0, 0, 0, 0.7);
  }

  .header-content {
    display: flex;
    justify-content: space-between;
    align-items: center;
    width: 70%;
    padding: 1rem 2rem;
  }

  /* 로고 스타일 */
  .logo {
    font-size: 1.5rem;
    font-weight: bold;
    margin: 0;
  }

  /* 네비게이션 바 */
  .navbar {
    display: flex;
    align-items: center;
    transition: background-color 0.3s ease; /* 배경색 변화 애니메이션 */
  }

  .navbar.scrolled {
    background-color: white; /* 스크롤 시 배경색 변경 */
    color: black; /* 스크롤 시 글자 색상 변경 */
  }



  .navbar-item {
    display: flex;
    gap: 1.5rem;
    list-style: none;
    padding: 0;
    margin: 0;
  }

  .navbar-item a {
    text-decoration: none;
    color: white;
    font-size: 1rem;
    font-weight: bold;
  }
  .navbar-item a:hover {
    font-size: 1.1rem;
    font-weight: bold;
  }


  .menu-toggle {
    display: none;
    background: none;
    border: none;
    color: white;
    font-size: 1.5rem;
    cursor: pointer;
  }


  .center-content {
    text-align: center;
    margin: auto;
  }

  .center-content h2 {
    font-size: 4rem;
    font-weight: bold;
    margin: 0;
  }
  .center-content h3 {
    font-size: 2rem;
    font-weight: bold;
    margin: 0;
  }



  /* 모바일 */
  @media (max-width: 768px) {
    .menu-toggle {
      display: block;
    }

    .navbar-item {
      display: none;
      position: absolute;
      top: 100%;
      right: 0;
      background: rgba(0, 0, 0, 0.8);
      flex-direction: column;
      gap: 1rem;
      padding: 1rem;
      border-radius: 0.5rem;
    }

    .navbar.is-active .nav-links {
      display: flex;
    }
  }
</style>