<template>
  <div class="frontend-layout">
    <header class="navbar-wrapper">
      <div class="navbar-container">
        <div class="brand-section">
          <img class="brand-logo" :src="robotFill" alt="心理健康AI助手" />
          <h1 class="brand-name">心理健康AI助手</h1>
        </div>

        <nav class="nav-section">
          <router-link to="/" class="nav-link">首页</router-link>
          <router-link to="/consulation" class="nav-link" v-if="isLogin">AI咨询</router-link>
          <router-link to="/emotional-diary" class="nav-link" v-if="isLogin">情绪日记</router-link>
          <router-link to="/knowledge" class="nav-link">知识库</router-link>
          <el-button size="small" @click="handleLogin">
            {{ isLogin ? '退出登录' : '登录' }}
          </el-button>
          <el-button size="small" @click="handleRegister" v-if="!isLogin">注册</el-button>
        </nav>

        <button class="mobile-menu-btn" @click="mobileMenuOpen = !mobileMenuOpen">
          <span></span>
          <span></span>
          <span></span>
        </button>
      </div>

      <nav class="mobile-nav" v-if="mobileMenuOpen">
        <router-link to="/" class="mobile-nav-link" @click="mobileMenuOpen = false">首页</router-link>
        <router-link to="/consulation" class="mobile-nav-link" v-if="isLogin" @click="mobileMenuOpen = false">AI咨询</router-link>
        <router-link to="/emotional-diary" class="mobile-nav-link" v-if="isLogin" @click="mobileMenuOpen = false">情绪日记</router-link>
        <router-link to="/knowledge" class="mobile-nav-link" @click="mobileMenuOpen = false">知识库</router-link>
        <div class="mobile-nav-buttons">
          <el-button size="small" @click="handleLogin; mobileMenuOpen = false">
            {{ isLogin ? '退出登录' : '登录' }}
          </el-button>
          <el-button size="small" @click="handleRegister; mobileMenuOpen = false" v-if="!isLogin">注册</el-button>
        </div>
      </nav>
    </header>

    <main class="main-container">
      <router-view />
    </main>

    <footer class="footer-container">
      <div class="footer-bottom">&copy; 2026 心理健康AI助手. All rights reserved.</div>
    </footer>
  </div>
</template>

<script setup>
import { onMounted, ref } from 'vue';
import { useRouter } from 'vue-router';
import robotFill from '../assets/images/logo.png';

const router = useRouter();
const isLogin = ref(false);
const mobileMenuOpen = ref(false);

onMounted(() => {
  const token = localStorage.getItem('token');
  isLogin.value = !!token;
});

const handleLogin = () => {
  if (isLogin.value) {
    localStorage.removeItem('token');
    localStorage.removeItem('userInfo');
    isLogin.value = false;
    router.push('/auth/login');
  } else {
    router.push('/auth/login');
  }
};

const handleRegister = () => {
  router.push('/auth/register');
};
</script>

<style lang="scss" scoped>
.frontend-layout {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  background-color: #fff;
}

.navbar-wrapper {
  border-bottom: 1px solid #e5e7eb;
  position: relative;
}

.navbar-container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 10px 15px;
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.brand-section {
  display: flex;
  align-items: center;
  justify-content: flex-start;
}

.brand-logo {
  width: 40px;
  height: 40px;
  display: block;
}

.brand-name {
  margin: 0 0 0 8px;
  font-size: 18px;
  font-weight: 600;
  color: #333;
}

.nav-section {
  display: flex;
  align-items: center;
  gap: 16px;
}

.nav-link {
  color: #4b5563;
  font-size: 14px;
  font-weight: 500;
  text-decoration: none;
}

.nav-link:hover {
  color: #4a90e2;
}

.mobile-menu-btn {
  display: none;
  flex-direction: column;
  justify-content: space-between;
  width: 28px;
  height: 24px;
  background: none;
  border: none;
  cursor: pointer;
  padding: 0;
  
  span {
    width: 100%;
    height: 2px;
    background-color: #333;
    border-radius: 2px;
    transition: all 0.3s;
  }
}

.mobile-nav {
  display: none;
  position: absolute;
  top: 100%;
  left: 0;
  right: 0;
  background: #fff;
  border-bottom: 1px solid #e5e7eb;
  padding: 15px;
  z-index: 100;
}

.mobile-nav-link {
  display: block;
  color: #4b5563;
  font-size: 16px;
  padding: 12px 0;
  text-decoration: none;
  border-bottom: 1px solid #f3f4f6;
  
  &:last-child {
    border-bottom: none;
  }
  
  &:hover {
    color: #4a90e2;
  }
}

.mobile-nav-buttons {
  display: flex;
  gap: 10px;
  margin-top: 15px;
  padding-top: 15px;
  border-top: 1px solid #f3f4f6;
}

.main-container {
  flex: 1;
}

.footer-container {
  background: #1f2937;
  color: #fff;
  padding: 15px 0;
}

.footer-bottom {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 15px;
  text-align: center;
  font-size: 14px;
}

@media (max-width: 768px) {
  .nav-section {
    display: none;
  }
  
  .mobile-menu-btn {
    display: flex;
  }
  
  .mobile-nav {
    display: block;
  }
  
  .brand-name {
    font-size: 16px;
  }
  
  .brand-logo {
    width: 35px;
    height: 35px;
  }
}

@media (max-width: 480px) {
  .navbar-container {
    padding: 8px 12px;
  }
  
  .brand-name {
    font-size: 14px;
  }
  
  .brand-logo {
    width: 30px;
    height: 30px;
  }
}
</style>
