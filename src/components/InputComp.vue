<template>
  <div>
    <input
      type="file"
      :accept="isIncomeCert ? null : acceptedTypes"
      @change="handleFileChange"
    />
    <p>{{ text1 }}</p>
  </div>
</template>

<script>
export default {
  name: "InputComp",
  props: {
isIncomeCert: {
  type: Boolean,
  default: false
}
  },
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

      // Добавленная валидация
      if (!this.acceptedFiles.includes(file.type)) {
        this.text1 = `❌ Неподдерживаемый формат: ${file.name} (${file.type})`;
      } else {
        this.text1 = `✅ Выбран файл: ${file.name} (${file.type})`;
      }

      // Сброс input для повторного выбора того же файла
      event.target.value = "";
    },
  },
};
</script>
