<template>
  <!-- Add Employee Popup Template -->
  <div>
    <!-- "Add Employee" Button -->
    <button class="button_forward mt-5 ms-5" @click="openPopup">Add Employee</button>

    <!-- Popup Container -->
    <div class="popup-container" v-if="showPopup">
      <div class="pop_up">
        <!-- Popup Title and Close Button -->
        <div class="same_line d-flex">
          <p class="title_text">Add Employee</p>
          <button type="button" class="btn-close btn-close-white" aria-label="Close" @click="closePopup"></button>
        </div>

        <!-- Employee Name Input -->
        <label class="form-label">Employee Name <label style="color: #CD1717;">*</label></label>
        <input type="text" class="form-control mb-2" placeholder="Dima" required>

        <!-- Email Address Input -->
        <label class="form-label">Email Address <label style="color: #CD1717;">*</label></label>
        <input type="email" class="form-control mb-2" placeholder="name@yourcompany.com" required>

        <!-- Phone Number Input -->
        <label class="form-label">Phone Number</label>
        <div class="same_line d-flex">
          <DropdownOptions :options="options[0]" /><input type="text" class="phone_text form-control" placeholder="">
        </div>

        <!-- Branch Name Dropdown -->
        <label class="form-label">Branch Name <label style="color: #CD1717;">*</label></label>
        <DropdownOptions :options="options[1]" />

        <!-- Job Role Dropdown -->
        <label class="form-label">Job Role <label style="color: #CD1717;">*</label></label>
        <DropdownOptions :options="options[2]" />

        <!-- Password Input -->
        <label class="form-label">Password <label style="color: #CD1717;">*</label></label>
        <div class="input-with-icon">
          <input type="password" placeholder="" class="password-input" id="Password" v-model="password">
          <button id="eye-icon" @click.prevent="togglePasswordVisibility">
            <!-- SVG Eye Icon -->
            <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none">
              <path d="M15.5799 11.9999C15.5799 13.9799 13.9799 15.5799 11.9999 15.5799C10.0199 15.5799 8.41992 13.9799 8.41992 11.9999C8.41992 10.0199 10.0199 8.41992 11.9999 8.41992C13.9799 8.41992 15.5799 10.0199 15.5799 11.9999Z" stroke="#3AC2CB" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/>
              <path d="M12.0001 20.2697C15.5301 20.2697 18.8201 18.1897 21.1101 14.5897C22.0101 13.1797 22.0101 10.8097 21.1101 9.39973C18.8201 5.79973 15.5301 3.71973 12.0001 3.71973C8.47009 3.71973 5.18009 5.79973 2.89009 9.39973C1.99009 10.8097 1.99009 13.1797 2.89009 14.5897C5.18009 18.1897 8.47009 20.2697 12.0001 20.2697Z" stroke="#3AC2CB" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/>
            </svg>
          </button>
        </div>

        <!-- "Create and Send Email" Button -->
        <button class="button_forward mt-3">Create and Send Email</button>
      </div>
    </div>
  </div>
</template>

<script>
// Import the DropdownOptions component
import DropdownOptions from './DropdownOptions.vue';

// Define and export the component
export default {
  components: {
    DropdownOptions,
  },
  data() {
    return {
      // Data properties
      showPopup: false, // Controls whether the popup is displayed
      
      // Dropdown options data
      options: [
        { type: 'phone', optionArray: ['+966', '+973', '+86'] },
        { type: 'branch', optionArray: ['all', 'mazaj', "McDonald's", 'Extra'] },
        { type: 'position', optionArray: ['ux designer', 'software engineering', 'accountant'] },
      ],
    };
  },
  methods: {
    // Method to toggle password visibility
    togglePasswordVisibility() {
      const passwordInput = document.getElementById('Password');
      const eyeButton = document.getElementById('eye-icon');
      if (passwordInput.type === 'password') {
        // Show password
        passwordInput.type = 'text';
        eyeButton.innerHTML = '<svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 25 24" fill="none"><path d="M16.5799 11.9999C16.5799 13.9799 14.9799 15.5799 12.9999 15.5799C11.0199 15.5799 9.41992 13.9799 9.41992 11.9999C9.41992 10.0199 11.0199 8.41992 12.9999 8.41992C14.9799 8.41992 16.5799 10.0199 16.5799 11.9999Z" stroke="#3AC2CB" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/><path d="M12.9998 20.2697C16.5298 20.2697 19.8198 18.1897 22.1098 14.5897C23.0098 13.1797 23.0098 10.8097 22.1098 9.39973C19.8198 5.79973 16.5298 3.71973 12.9998 3.71973C9.46984 3.71973 6.17984 5.79973 3.88984 9.39973C2.98984 10.8097 2.98984 13.1797 3.88984 14.5897C6.17984 18.1897 9.46984 20.2697 12.9998 20.2697Z" stroke="#3AC2CB" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/><path d="M0.722656 19.584L24.7227 4.58398" stroke="#3AC2CB"/></svg>';
      } else {
        // Hide password
        passwordInput.type = 'password';
        eyeButton.innerHTML = '<svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none"><path d="M15.5799 11.9999C15.5799 13.9799 13.9799 15.5799 11.9999 15.5799C10.0199 15.5799 8.41992 13.9799 8.41992 11.9999C8.41992 10.0199 10.0199 8.41992 11.9999 8.41992C13.9799 8.41992 15.5799 10.0199 15.5799 11.9999Z" stroke="#3AC2CB" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/><path d="M12.0001 20.2697C15.5301 20.2697 18.8201 18.1897 21.1101 14.5897C22.0101 13.1797 22.0101 10.8097 21.1101 9.39973C18.8201 5.79973 15.5301 3.71973 12.0001 3.71973C8.47009 3.71973 5.18009 5.79973 2.89009 9.39973C1.99009 10.8097 1.99009 13.1797 2.89009 14.5897C5.18009 18.1897 8.47009 20.2697 12.0001 20.2697Z" stroke="#3AC2CB" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/></svg>';
      }
    },

    // Method to open the popup
    openPopup() {
      this.showPopup = true;
    },

    // Method to close the popup
    closePopup() {
      this.showPopup = false;
    },
  },
};
</script>


<style scoped>
/* Scoped styles for the component */

/* Import Google Fonts for the page */
@import url("https://fonts.googleapis.com/css2?family=Poppins:wght@400;500;700&display=swap");

/* Form label styling */
.form-label {
  color: var(--fafafa, #FAFAFA);
  font-size: 16px;
  margin-top: 10px;
}

/* Form control styling */
.form-control {
  background-color: var(--36415-c, #36415C);
  color: var(--fafafa, #FAFAFA);
  width: 500px;
  height: 60px;
  border-radius: 10px;
  border: none;
  box-shadow: none;
  margin-bottom: 20px;
}

/* Styling for focused input fields */
.phone_text:focus,
.form-control:focus {
  border: 1px solid #3AC2CB;
}

/* Title text styling */
.title_text {
  margin-left: 177px;
  color: var(--fafafa, #FAFAFA);
  font-size: 20px;
}

/* Styling for the popup container */
.pop_up {
  line-height: normal;
  font-style: normal;
  font-family: Poppins;
  font-weight: 500;
  text-transform: capitalize;
  width: 560px;
  height: 884px;
  border-radius: 20px;
  background-color: #040D21;
  padding: 30px 0px 0px 30px;
  margin-left: 100px;
}

/* Styling for the popup container overlay */
.popup-container {
  display: flex;
  justify-content: center;
  align-items: center;
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  z-index: 1000;
}

/* Styling for close button */
.btn-close {
  margin-left: 161px;
}

/* Styling for the forward button */
.button_forward {
  border: none;
  width: 500px;
  height: 60px;
  border-radius: 10px;
  background: var(--3-ac-2-cb, #3AC2CB);
  color: var(--fafafa, #FAFAFA);
  font-size: 20px;
  text-transform: capitalize;
}

/* Styling for phone text input */
.phone_text {
  box-shadow: none;
  width: 415px;
  height: 60px;
  margin-left: 85px;
  position: absolute;
}

/* Placeholder text styling */
::placeholder {
  color: var(--fafafa, #FAFAFA);
  font-size: 16px;
  font-weight: 400;
}

/* Styling for password input */
.password-input {
  width: 500px;
  height: 60px;
  flex-shrink: 0;
  border-radius: 10px;
  background: var(--36415-c, #36415C);
  border: 1px solid var(--3-ac-2-cb, #36415C);
  padding-left: 20px;
  outline: none;
  color: var(--fafafa, #FAFAFA);
  font-size: 16px;
  font-weight: 400;
  border: var(--36415-c, #36415C);
  margin-bottom: 20px;
}

/* Styling for focused password input */
.password-input:focus {
  border: 1px solid var(--3-ac-2-cb, #3AC2CB);
  background: rgba(58, 194, 203, 0.10);
}

/* Styling for eye icon button */
#eye-icon {
  background: none;
  color: inherit;
  border: none;
  padding: 0;
  font: inherit;
  cursor: pointer;
  outline: inherit;
  position: absolute;
  margin: 17px 0px 0px -47px;
}

</style>

  