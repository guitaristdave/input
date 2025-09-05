<template>
  <div>
    <h2>IMG + PDF TEST INPUT</h2>

    <!-- инпут с accept -->
    <input type="file" :accept="acceptedTypes" @change="handleFileChange" />
    <p>{{ text1 }}</p>

    <h2>ANY FILE TEST INPUT</h2>
    <!-- инпут без accept -->
    <input type="file" @change="handleAnyFileChange" />
    <p>{{ text2 }}</p>
  </div>
</template>

<script>
export default {
  name: "InputComp",
  data() {
    return {
      acceptedFiles: [
        "image/png",
        "image/jpeg",
        "image/heic",
        "image/heif",
        "application/pdf",
      ],
      text1: null,
      text2: null,
    };
  },
  computed: {
    acceptedTypes() {
      return this.acceptedFiles.join(",");
    },
  },
  methods: {
    handleFileChange(event) {
      const file = event.target.files[0];
      if (!file) {
        this.text1 = "Файл не выбран";
        return;
      }
      this.text1 = `Выбран файл: ${file.name} (${file.type})`;
      event.target.value = ""; // сброс
    },
    handleAnyFileChange(event) {
      const file = event.target.files[0];
      if (!file) {
        this.text2 = "Файл не выбран";
        return;
      }
      if (this.acceptedFiles.includes(file.type)) {
        this.text2 = `✅ Поддерживаемый файл: ${file.name} (${file.type})`;
      } else {
        this.text2 = `❌ Неподдерживаемый формат: ${file.name} (${file.type})`;
      }
      event.target.value = ""; // сброс
    },
  },
};
</script>
