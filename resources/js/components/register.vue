<template>
  <div class="form-overlay" @click="handleOutsideClick">
    <div class="form-container" @click.stop>
      <h2 class="form-title">Registrarse</h2>
      <form @submit.prevent="register">
        <!-- Name input field -->
        <div class="form-group">
          <label for="name">Nombres</label>
          <input
            type="text"
            id="name"
            v-model="names"
            placeholder="Nombres"
            class="form-control"
            required
          />
        </div>

        <!-- Surname input fields (paternal and maternal) -->
        <div class="form-group d-flex flex-wrap justify-content-between">
          <div class="form-group w-48 pe-2">
            <label for="paternalSurname">Apellido Paterno</label>
            <input
              type="text"
              id="paternalSurname"
              v-model="paternalSurname"
              placeholder="Apellido Paterno"
              class="form-control"
              required
            />
          </div>
          <div class="form-group w-48 ps-2">
            <label for="maternalSurname">Apellido Materno</label>
            <input
              type="text"
              id="maternalSurname"
              v-model="maternalSurname"
              placeholder="Apellido Materno"
              class="form-control"
              required
            />
          </div>
        </div>

        <!-- Email input field -->
        <div class="form-group">
          <label for="email">Correo Electrónico</label>
          <input
            type="email"
            id="email"
            v-model="email"
            placeholder="Correo Electrónico"
            class="form-control"
            required
          />
        </div>

        <!-- Password input field -->
        <div class="form-group">
          <label for="password">Contraseña</label>
          <input
            type="password"
            id="password"
            v-model="password"
            placeholder="Contraseña"
            class="form-control"
            required
          />
        </div>

        <!-- Password confirmation input field -->
        <div class="form-group">
          <label for="passwordConfirm">Confirmar Contraseña</label>
          <input
            type="password"
            id="passwordConfirm"
            v-model="passwordConfirm"
            placeholder="Confirmar Contraseña"
            class="form-control"
            required
          />
        </div>

        <!-- Submit button -->
        <div class="d-flex justify-content-center">
          <button type="submit" class="btn btn-primary">
            Registrarse
          </button>
        </div>
      </form>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      names: '',
      paternalSurname: '',
      maternalSurname: '',
      email: '',
      password: '',
      passwordConfirm: '',
    };
  },
  methods: {
    async register() {
      console.log(
        `Nombres: ${this.names}, Apellido Paterno: ${this.paternalSurname}, Apellido Materno: ${this.maternalSurname}, Email: ${this.email}, Password: ${this.password}, Password Confirm: ${this.passwordConfirm}`
      );
      // Implement registration logic here
    },
    handleOutsideClick() {
      this.$emit('close'); // Notify parent component to close the form
    },
  },
};
</script>

<style scoped>
.form-overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.5); /* Semi-transparent background */
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 1000; /* Ensure it is above other content */
}

.form-container {
  background: rgba(255, 255, 255, 0.9); /* Slightly transparent white */
  padding: 1.5rem; /* Reduced padding */
  border-radius: 8px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
  width: 100%;
  max-width: 500px; /* Reduced max width */
  position: relative;
}

.form-title {
  margin-bottom: 1rem;
  text-align: center;
}

.form-group {
  margin-bottom: 0.75rem; /* Reduced margin between fields */
}

.w-48 {
  width: 48%;
}

button {
  width: 100%;
}

@media (max-width: 460px) {
  .form-group {
    display: block !important;
  }

  .w-48 {
    width: 100% !important;
    padding: 0 !important;
  }

  button {
    width: 90%;
  }

  .form-container {
    width: 90% !important;
  }
}
</style>
