<template>
  <b-container> 
    <h1>Admin Panel</h1>
    <hr />
    <br />
    <div class="options">
      <a v-b-modal.csvModal class="d-block" style="cursor: pointer;">
        Import Courses via CSV
      </a>
      <a
        v-b-modal.editSemestersModal
        class="d-block"
        style="cursor: pointer;"
      >
        Edit Semesters
      </a>
      <a
        v-b-modal.defaultModal
        class="d-block"
        style="cursor: pointer;"
      >
        Set Default Semester
      </a>
    </div>

    <UploadCsv />
    <b-modal id="editSemestersModal" title="Edit Semesters" size="xl">
      <EditSemesters />
    </b-modal>
    <b-modal id="defaultModal" title="Set Default Semester" size="xl">
      <SetDefault />
    </b-modal>

    <!-- Footer of Admin Panel -->
    <br />
    <hr />
    <br />

    <div id="button__container">
      <b-button id="home" href="/">Go back home</b-button>
    </div>
  </b-container>
</template>

<script>
import UploadCsv from "@/pages/UploadCsv";
import EditSemesters from "@/pages/EditSemesters";
import SetDefault from "@/pages/SetDefault";

export default {
  name: "AdminPage",
  components: {
    UploadCsv,
    EditSemesters,
    SetDefault,
    // ManageAccounts,
  },
  data() {
    return {};
  },
};
</script>

<style lang="scss" scoped>
  h1 {
    text-align: center;
  }

  .options {
    display: flex;
    justify-content: space-around;

    & a {
      display: flex;
      text-align: center;
      padding: 1rem;
      margin: 1rem;
      border-radius: .25rem;
      background-color: #6c757d;
      color: white;
      text-decoration: none;
    }
  }

  #button__container {
    display: flex;
    justify-content: center;
    
    & a {
      width: 100%;
      text-align: center;
    }
  }
</style>
