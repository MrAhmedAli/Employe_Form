<template>
  <div
    class="box type-btn d-flex justify-content-between align-items-center pe-3 ps-3"
    v-show="show" :class="['box type-btn d-flex justify-content-between align-items-center pe-3 ps-3', {'box-sm type-btn d-flex justify-content-between align-items-center pe-3 ps-3': options.type == 'phone' }]"
    @click="show = !show"
  >
    <p class="m-0 d-flex align-items-center">{{ typeSelected }}</p>
    <div v-if="options.type=='phone'">
      <img class="img" :src="arrowDown1"/>
</div>
<div v-else>
  <img class="img-fluid" :src="arrowDown"/>
</div>
    
  </div>
  <div v-show="show" :class="['dropdown-content mt-1', {'dropdown-content-sm mt-1': options.type == 'phone'}]">
    <div
      class="dropdown-item pb-3"
      v-for="(dropdownOption, index) in options.optionArray"
      :key="index"
      :class="{active: typeSelected === options.optionArray[index]  && options.type !== 'branch' }"
    >

    <div v-if="options.type!=='branch'">
      <button class="btn mt-2 ps-0 type-option" @click="onOptionClick(dropdownOption)">{{ dropdownOption }} </button>
    </div>
    
    <div v-else>
       <input class="checkbox_location form-check-input" type="checkbox" id="flexCheckDefault"   @click="onOptionClick(dropdownOption)">
       <label  class="btn mt-2 ps-0 type-option" for="">{{ dropdownOption }}</label>
    </div>
  
    </div>
  </div>
</template>

<script>
import arrowDown from "/src/assets/images/arrow-down.svg";
import arrowDown1 from "/src/assets/images/arrow1.svg";

export default {
  props: {
    options: {
      type: Array,
      required: true,
      cusotmOptionsWidth: {
        type: String,
      },
    },
  },
  data() {
    return {
      arrowDown: arrowDown,
      arrowDown1: arrowDown1,
      show: false,
      typeSelected: this.options.optionArray[0],
    };
  },
  methods: {
    showDropdown() {
      this.show = !this.show;
    },
    onOptionClick(option) {
      if (this.options.type=='branch'){
      this.typeSelected = option 
      this.show = true; // don't Hide the dropdown after selecting an option
      this.$emit('update:typeSelected', option); // Emit the updated value to the parent
                                      }
      else{
      this.typeSelected = option;
      this.show = false; // Hide the dropdown after selecting an option
      this.$emit('update:typeSelected', option); // Emit the updated value to the parent
          }
                           },
          },
};
</script>

<style scoped>
.type-btn { cursor: pointer; }

.dropdown-content {
  position: absolute; /* to make appears above other elements on the page. */
  width: 100%;
  max-width: 500px;
  height: fit-content;
  border-radius: 10px;}

.dropdown-content-sm {
  color: #36415C;
  position: absolute; /* to make appears above other elements on the page. */
  width: fit-content;
  height: fit-content;
  border-radius: 10px;
  padding-top: 75px;}

.dropdown-item {
  border: 1px solid rgba(164, 180, 203, 0.50);
  background: var(--middle-blue-color);
  border-radius: 5px;
  display: flex;
  padding-left: 18px;}

.dropdown-item:hover { border: 2px solid #3AC2CB; }
.dropdown-item:first-child {
  border-top-left-radius: 10px;
  border-top-right-radius: 10px;
  margin-top: -18px;}

.dropdown-item:last-child {
  border-bottom-left-radius: 10px;
  border-bottom-right-radius: 10px;}

.type-option {
  color: var(--fafafa, #FAFAFA);
  border: none;
  outline: none;
  width: 100%;
  font-weight: 400px;
  font-size: 16px;
  font-style: normal;
  line-height: normal;
  text-transform: capitalize;}

.active { background-color: var(--second-blue-color); }

.box {
  width: 500px;
  height: 60px;
  border-radius: 10px;
  background: var(--middle-blue-color);
  color: var(--white-color);
  margin-bottom: 15px;}

.box-sm {
  width: 100px;
  height: 60px;
  border-radius: 10px;
  background: var(--middle-blue-color);}

  .form-check-input{
    margin: 20px 20px 0px 0px;
    background-color: #36415C;
    border-color: #3AC2CB;
    border-radius: 5px;
    width: 18px;
    height: 18px;}

.form-check-input:checked{ background-color: #3AC2CB; }

</style>
