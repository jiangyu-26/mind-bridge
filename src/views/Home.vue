<template>
    <div class="home-container">
        
        <div class="content">
            <div class="text">
                <h1 class="title">
                    一次温暖的对话<br/><span class="highlight-text">化孤独为慰藉</span>
                </h1>
                <p>我们致力于为您提供最专业的心理咨询服务。</p>
                <div class="hero-actions">
                    <el-button type="primary" size="large" @click="handleGetStarted">开始诉说，获得陪伴</el-button>
                    <el-button type="success" size="large" @click="handleGetStarted">记录心情，释放情感</el-button>
                </div>
            </div>
            <div class="robot">
                <img :src="robotFill" alt="AI助手" />
            </div>
        </div>
    </div>
</template>

<script setup>
import { ref } from 'vue';
import robotFill from '../assets/images/robot-fill.png';

const handleGetStarted = () => {
  // Handle the "Get Started" button click
};
</script>

<style lang="scss">

.home-container {
    background: linear-gradient(90deg, rgb(74, 156, 140) 0%, rgb(61, 138, 122) 100%) rgba(74, 156, 140, 0.95);
    color: white;
    padding: 3rem 15px;
    min-height: calc(100vh - 285px);
    display: flex;
    align-items: center;
    justify-content: center;

    .content {
      display: flex;
      justify-content: center;
      align-items: center;
      gap: 30px;
      max-width: 1200px;
      width: 100%;

      .text {
          width: 500px;
          max-width: 100%;

          .title {
              font-size: 45px;
              font-weight: bold;
              margin-bottom: 15px;
              line-height: 1.2;

              .highlight-text {
                  color: #ffd700;
              }
          }

          p {
              font-size: 18px;
              line-height: 1.6;
          }

          .hero-actions {
              margin-top: 30px;
              display: flex;
              gap: 15px;
              flex-wrap: wrap;
          }
      }

      .robot {
          display: flex;
          justify-content: center;
          align-items: center;
          width: 260px;
          height: 260px;
          border-radius: 50%;
          border: 2px solid rgba(255, 255, 255, 0.2);
          background: linear-gradient(135deg, rgba(255, 255, 255, 0.15) 0%, rgba(255, 255, 255, 0.05) 100%);
          box-shadow: 0 15px 35px rgba(0, 0, 0, 0.1),inset 0 1px 0 rgba(255, 255, 255, 0.3);

          img {
              width: 180px;
              height: 180px;
          }
      }
    }
}

@media (max-width: 768px) {
    .home-container {
        padding: 2rem 15px;
        text-align: center;

        .content {
            flex-direction: column;
            gap: 25px;

            .text {
                .title {
                    font-size: 32px;
                }

                p {
                    font-size: 16px;
                }

                .hero-actions {
                    justify-content: center;
                }
            }

            .robot {
                width: 200px;
                height: 200px;

                img {
                    width: 140px;
                    height: 140px;
                }
            }
        }
    }
}

@media (max-width: 480px) {
    .home-container {
        padding: 1.5rem 10px;

        .content {
            .text {
                .title {
                    font-size: 26px;
                }

                .hero-actions {
                    flex-direction: column;
                    align-items: center;
                }
            }

            .robot {
                width: 160px;
                height: 160px;

                img {
                    width: 110px;
                    height: 110px;
                }
            }
        }
    }
}
</style>