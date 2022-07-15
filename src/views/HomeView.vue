<template>
  <div class="dashboard">
    <main-section></main-section>
    <header-section/>
    <sidebar-section/>
    <note-section></note-section>
  </div>
</template>

<script>
// @ is an alias to /src
import mainSection from "@/components/MainSection";
import headerSection from "@/components/HeaderSection";
import noteSection from "@/components/NoteSection";
import sidebarSection from "@/components/SidebarSection";

export default {
  name: 'HomeView',
  components: {
    mainSection,
    headerSection,
    noteSection,
    sidebarSection,

  }
}
</script>
<style>
.dashboard {
  box-sizing: border-box;
  padding: 0px;
  display: grid;
  grid-template-rows: 1fr 12fr 4fr;
  grid-template-columns: 70px 2fr 1fr;
  height: 100vh;
  grid-template-areas:
  "sidebar header note"
  "sidebar main main"
  "sidebar static static"
;
}
.sidebar {
  grid-area: sidebar;
  background: #2B2E32;
}
.main{
  grid-area: main;
  background: #ffffff;
  height: 100%;
}
.header {
  grid-area: header;
  background: #ffffff;
}
.note {
  grid-area: note;
  background: #ffffff;
}
.static {
  grid-area: static;
  background: #4a93e0;
}
</style>
