<script lang="ts" setup>
import ProjectCard from "@/components/ProjectCard.vue";
import AnnouncementCard from "@/components/AnnouncementCard.vue";
import TrendingCard from "@/components/TrendingCard.vue";
</script>

<template>
  <div class="container project-box">
    <section class="dashboard">
      <div class="project">
        <h4>Your Projects</h4>
        <div class="project-grid">
          <ProjectCard
            v-for="_ in 6" :key="_"
            title="Super Cool Project"
            content="Lorem ipsum dolor sit amet, officia excepteur ex fugiat
              reprehenderit enim labore culpa sint ad nisi Lorem pariatur
              mollit ex esse exercitation amet.
              Lorem ipsum dolor sit amet, officia excepteur ex fugiat
              reprehenderit enim labore culpa sint ad nisi Lorem pariatur
              mollit ex esse exercitation amet." />
        </div>
      </div>

      <section class="side">
        <div class="announcement">
          <h4>Announcements</h4>
          <div class="background-box">
            <AnnouncementCard v-for="_ in 3" :key="_"
              title="Community Share Day"
              content="Lorem ipsum dolor sit amet, officia excepteur ex fugiat
                      reprehenderit enim labore culpa sint ad nisi Lorem pariatur
                      mollit ex esse exercitation amet. Nisi anim cupidatat
                      excepteur officia. Reprehenderit nostrud nostrud ipsum Lorem
                      est aliquip amet voluptate voluptate dolor minim nulla est
                      proident. Nostrud officia pariatur ut officia. Sit irure
                      elit esse ea nulla sunt ex occaecat reprehenderit commodo
                      officia dolor Lorem duis laboris cupidatat officia
                      voluptate.">
              <hr v-if="_ !== 3" />
            </AnnouncementCard>
          </div>
        </div>

        <div>
          <h4>Trending</h4>
          <div class="background-box trending">
            <TrendingCard v-for="_ in 5" :key="_" content="World Peace Builder" username="@tegan" image="https://robohash.org/irwi32.png?set=set4" />
          </div>
        </div>
      </section>
    </section>
  </div>
</template>

<style></style>