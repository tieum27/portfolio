<script>
import ExperienceCard from "../cards/Experience.vue";
import SkillsCard from "../cards/Skills.vue";
import TechStackCard from "../cards/TechStack.vue";
import PageHeader from "../PageHeader.vue";

const railsLogo = require("@/assets/img/svg/rails.svg");
const rubyLogo  = require("@/assets/img/svg/ruby.svg");
const cssLogo = require("@/assets/img/svg/css.svg");
const htmlLogo = require("@/assets/img/svg/html.svg");
const nodejsLogo = require("@/assets/img/svg/nodejs.svg");
const vueLogo = require("@/assets/img/svg/vue.svg");
const jsLogo = require("@/assets/img/svg/js.svg");

export default {
  name: "AboutPage",
  props: ["isActive"],
  components: { ExperienceCard, TechStackCard, SkillsCard, PageHeader },
  data() {
    return {
      skills: [
        "Time Management and Organization",
        "Eagerness to Learn New Technologies",
        "Software Components and Libraries",
        "Agile/Scrum Methodology",
        "Object-Oriented Programming",
        "Software Components and Libraries",
        "Teamwork and Collaboration",
        "Source and Version Control: Git, Github",
      ],
      techStack: [
        {
          name: "ruby logo",
          logo: rubyLogo,
        },
        {
          name: "rails logo",
          logo: railsLogo,
        },
        {
          name: "vue logo",
          logo: vueLogo,
        },
        {
          name: "javascript logo",
          logo: jsLogo,
        },
        {
          name: "node log",
          logo: nodejsLogo,
        },
        {
          name: "html 5 logo",
          logo: htmlLogo,
        },
        {
          name: "css 3 logo",
          logo: cssLogo,
        },
      ],
    };
  },
};
</script>

<template>
  <div
    class="page aboutpage"
    :class="{
      'active-page': isActive,
      'animate__animated animate__zoomIn': isActive,
    }"
  >
    <div class="page-wrapper">
      <PageHeader :title="'About me'" :secondaryTitle="'resume'" />
      <section>
        <!-- personal info -->
        <div class="row">
          <div class="col-12 col-lg-5 pers-info">
            <div class="section-title">
              <h3>Personal Info</h3>
            </div>
            <img
              class="img-mobile"
              :src="require('@/assets/img/my-portrait.jpg')"
            />
            <div class="personal-info">
              <ul>
                <li>
                  <span class="label">First Name</span>
                  <span class="label-value">Matthieu</span>
                </li>

                <li>
                  <span class="label">last name</span>
                  <span class="label-value">Tripoli</span>
                </li>

                <li>
                  <span class="label">email</span>
                  <span>
                    <a href="mailto:mail@matthieutripoli.com">
                      mail@matthieutripoli.com
                    </a>
                  </span>
                </li>

                <li>
                  <span class="label">phone</span>
                  <span class="label-value">+33652229126</span>
                </li>

                <li>
                  <span class="label">github</span>
                  <span class="label-value">
                    <a href="https://github.com/tieum27" target="_blank">
                      <font-awesome-icon :icon="['fas', 'link']" />
                      View GitHUB
                    </a
                    >
                  </span>
                </li>
              </ul>
            </div>
            <div>
              <a class="button" :href="require('@/assets/resume.pdf')" download>
                <span class="btn-text">Download Resume</span>
                <font-awesome-icon
                  :icon="['fas', 'download']"
                  class="btn-icon"
                />
              </a>
            </div>
          </div>
          <!-- Skills -->
  
          <div class="col-12 col-lg-5 skill-section">
            <div class="section-title">
                <h3>Skills</h3>
            </div>
            <ul>
              <li v-for="skill in skills" :key="skill">
                <SkillsCard
                  :skill="skill"
                />
              </li>
            </ul>
          </div>
        </div>


        <!-- TechStack -->

        <div class="techStack-section">
          <div class="flex">
            <div class="section-title">
              <h3 class="text-center">TOOLS</h3>
              <div class="techStack-wrapper">
                <ul class="techStack-list">
                  <li v-for="el in techStack" :key="el.name">
                    <TechStackCard
                      :text="el.name"
                      :logo="el.logo"
                    />
                  </li>
                </ul>
              </div>
            </div>
          </div>
        </div>
      </section>
    </div>
  </div>
</template>

<style lang="scss">
.aboutpage {
  section {
    & > .flex:not(:first-child) {
      margin-bottom: 20px;
      margin-top: 40px;
    }
    .personal-info ul {
      display: flex;
      flex-direction: column;
      align-items: flex-start;
      padding: 0 0.3rem;
      li {
        flex: 0 0 50%;
        padding-bottom: 20px;
      }
    }
    .label {
      opacity: 0.8;
    }
    .label::after {
      content: ":";
    }

    .label-value {
      font-weight: 600;
    }
    .label,
    .label-value {
      padding: 4px 6px;
      text-transform: capitalize;
    }

    .techStack-section {
      display: flex;
      width: 100%;
      justify-content: center;
    }
  }
  .techStack-wrapper {
    display: flex;
    justify-content: center;
    align-items: center;
    width: 100%;
  }
  .techStack-list {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
  }
  .skill-section {
    ul {
      list-style: disc;
    }
  }
}

@media (min-width: 1201px) {
  .about.modal-dialog {
    max-width: 1140px;
  }
}
</style>