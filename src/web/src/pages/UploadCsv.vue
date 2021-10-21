<template>
  <b-modal id="csvModal" size="xl">
    <div slot="modal-header" class="header">
      <div />
      Upload CSV
      </div>
    <b-container>
      <section id="import-data">
        <form @submit.prevent="onSubmit" id="upload-form" class="form-group">
          <div class="input-group">
            <label>
              <input type="file" name="file" class="form-control-file" />
            </label>
            <br />
          </div>
          <div class="input-group" id="options">
            <label>
              <input type="checkbox" name="isPubliclyVisible" checked />
              Make Public
            </label>
          </div>
        </form>
      </section>
      <b-spinner v-show="loading" />
    </b-container>  
    <div slot="modal-footer" class="footer">
      <button class="btn btn-success" @click="$bvModal.hide('csvModal')">Cancel</button>
      <button form="upload-form" class="btn btn-success">Submit</button>
    </div>
  </b-modal>
</template>

<script>
import { uploadCsv } from "@/services/AdminService";

export default {
  name: "UploadCsv",
  components: {},
  props: {},
  data() {
    return {
      loading: false,
      isPublic: false,
    };
  },
  methods: {
    onSubmit(event) {
      if (!this.loading) {
        let formData = new FormData(event.target);
        this.loading = true;
        this.$emit("loading");
        if (formData.get("file") && formData.get("file").name) {
          let filename = formData.get("file").name;
          uploadCsv(formData)
            .then((response) => {
              console.log(response);
              // Axios will only enter this block if the status code is 2xx,
              // so handle errors for catch block. https://stackoverflow.com/questions/49967779/axios-handling-errors
              this.$bvToast.toast(
                `${filename} has been successfully uploaded!`,
                {
                  title: "Upload Result",
                  variant: "info",
                  noAutoHide: false,
                }
              );
              this.loading = false;
              this.$emit("loadfinish");
            })
            .catch((error) => {
              console.log(error.response);
              this.loading = false;
              this.$emit("loadfinish");
              this.$bvToast.toast(
                `HTTP ${error.response.status}: ${error.response.data}`,
                {
                  title: "Upload Result",
                  variant: "danger",
                  noAutoHide: true,
                }
              );
            });
        } else {
          this.$bvToast.toast(`Must upload a CSV file`, {
            title: "Validation Error",
            variant: "danger",
            noAutoHide: false,
          });
          this.loading = false;
          this.$emit("loadfinish");
        }
      }
    },
    back() {
      window.history.back();
    },
  },
};
</script>

<style lang="scss" scoped>
  #csvModal {
    text-align: center;
  }

  .form-group {
    display: flex;
    flex-direction: column;
  }

  #options {
    display: flex;
    justify-content: flex-start;
  }

  .header {
    display: flex;
    justify-content: center;
    width: 100%;
  }

  .footer {
    display: flex;
    justify-content: space-between;
    width: 100%;
  }
</style>
