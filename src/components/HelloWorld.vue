<template>
 <div class="container">
  
    <form  style="border:1px solid #ccc" @submit.prevent="submit">
        
          <h1>Регистрация</h1>
          <p>Пожалуйста заполните форму чтобы создать аккаунт.</p>
          <hr>
          
            <label><b>Фамилия *</b></label>
            <input 
            type="text" 
            placeholder="Ваша фамилия" 
            v-model.trim="lastName"
            :class="{invalid: ($v.lastName.$dirty && !$v.lastName.required) || ($v.lastName.$dirty && $v.lastName.alpha)}">
            <small 
          class="invalid-text"
          v-if="$v.lastName.$dirty && !$v.lastName.required"
          >Поле не должно быть пустым</small>
          <small
          class="invalid-text"
          v-if="$v.lastName.$dirty && !$v.lastName.alpha"
          >Поле не должно содержать цифры</small>
            <br>
          


          <label><b>Имя *</b></label>
          <input 
          type="text" 
          placeholder="Ваше имя" 
          v-model.trim="firstName"
          :class="{invalid: ($v.firstName.$dirty  && !$v.firstName.required ) || ($v.firstName.$dirty && !$v.firstName.alpha)}">
          <small 
          class="invalid-text"
          v-if="$v.firstName.$dirty && !$v.firstName.required"
          >Поле не должно быть пустым</small>
          <small
          class="invalid-text"
          v-if="$v.firstName.$dirty && !$v.firstName.alpha"
          >Поле не должно содержать цифры</small>
          <br>

          
          

          <label><b>Отчество</b></label>
          <input 
          type="text" 
          placeholder="Ваше отчество"
          v-model.trim="patronymic"
          :class="{invalid: ($v.patronymic.$dirty && !$v.patronymic.alpha)}" >

          <small
          class="invalid-text"
          v-if="$v.patronymic.$dirty && !$v.patronymic.alpha"
          >Поле не должно содержать цифры</small>
          <br>

          <label><b>Дата рождения *</b></label>
          <br>
          <input 
          type="date"
          v-model.trim="date"
          :class="{invalid: ($v.date.$dirty && !$v.date.required)}" >

          <small
          class="invalid-text"
          v-if="$v.date.$dirty && !$v.date.required"
          >Поле не должно быть пустым</small>
          <br>
          

          <label><b>Номер телефона*</b></label>
          <input 
          type="tel" 
          placeholder="7(XXX)-XX-XX-XXX"
          v-model.trim="phone" 
          :class="{invalid: ($v.phone.$dirty && !$v.phone.rusNumber)}" >

          

          <small
          class="invalid-text"
          v-if="$v.phone.$dirty && !$v.phone.required  || !$v.phone.rusNumber  "
          >Неверный формат</small>

          <br>

          <label><b>Пол</b></label>
          <br>

          <div class="form_radio_btn">
          <input type="radio" name="sex" id="radioMale" value="male" >
          <label for="radioMale">M</label>
          </div>

          <div class="form_radio_btn">
          <input type="radio"  name="sex" id="radioFemale" value="female" >
          <label for="radioFemale">Ж</label>
          </div>
          <br>

           <label><b>Группа клиентов*</b></label>
          <div class="__select">
           <div class="__select__content">

             <input type="checkbox" id="m-1" class="__select__input">
             <label class="__select__label" for="m-1">VIP</label>

             <input type="checkbox" id="m-2" class="__select__input">
             <label class="__select__label" for="m-2">Проблемные</label>

             <input type="checkbox" id="m-3" class="__select__input">
             <label class="__select__label" for="m-3">ОМС</label>

           </div>
          </div>

          <label><b>Лечащий врач *</b></label>
          <br>
          <select 
          class="select-css"
         >
            <option>Иванов</option>
            <option>Захаров</option>
            <option>Чернышева</option>
            
          </select>

          

          <br>
          <input type="checkbox">

          <label><b>Не отправлять смс</b></label>
          

          <h1>Адрес</h1>
      
          <label><b>Индекс </b></label>
          <input
           type="number"
           placeholder="XXX-XXX"
          v-model.trim="index" 
          :class="{invalid: ($v.index.$dirty && !$v.index.minLength || !$v.index.maxLength)}">

          <small
          class="invalid-text"
          v-if="$v.index.$dirty && !$v.index.minLength || !$v.index.maxLength "
          >Неверный формат</small>
          <br>

          <label ><b>Страна </b></label>
          <input type="text"  >
      
          <label ><b>Область</b></label>
          <input type="text">
          
          <label><b>Город *</b></label>
          <input 
          type="text" 
          v-model.trim="city" 
          :class="{invalid: ($v.city.$dirty && !$v.city.required || !$v.city.alpha)}" >

          <small
          class="invalid-text"
          v-if="$v.city.$dirty && !$v.city.required "
          >Поле не должно быть пустым</small>

           <small
          class="invalid-text"
          v-if="$v.city.$dirty &&  !$v.city.alpha"
          >Поле не должно содержать цифры</small>

          <br>

          <label><b>Улица</b></label>
          <input 
          type="text" >

          <label><b>Дом</b></label>
          <input type="number">

          <h1>Паспорт</h1>
          <br>

          <label><b>Тип документа*</b></label>
          <select class="select-css">
            <option>Паспорт</option>
            <option>Свидетельство о рождении</option>
            <option>Вод. удостоверение</option>
          </select>
          <br>

          <label><b>Серия</b></label>
          <input 
          type="number"
          v-model.trim="series" 
          :class="{invalid: ($v.series.$dirty && !$v.series.minLength && !$v.series.maxLength)}">

          <small
          class="invalid-text"
          v-if="$v.series.$dirty && !$v.series.maxLength  "
          >Неверный формат</small>

          <small
          class="invalid-text"
          v-if="$v.series.$dirty &&  !$v.series.minLength "
          >Неверный формат</small> 
          <br>

          <label><b>Номер</b></label>
          <input 
          type="number"
          v-model.trim="number" 
          :class="{invalid: ($v.number.$dirty && !$v.number.minLength && !$v.number.maxLength)}">

          <small
          class="invalid-text"
          v-if="$v.number.$dirty && !$v.number.maxLength  "
          >Неверный формат</small>

          <small
          class="invalid-text"
          v-if="$v.number.$dirty &&  !$v.number.minLength "
          >Неверный формат</small> 

          <br>

          <label><b>Кем выдан</b></label>
          <input 
          type="text" 
          v-model.trim="who"
          :class="{invalid: ($v.who.$dirty && !$v.who.alpha)}" >

          <small
          class="invalid-text"
          v-if="$v.who.$dirty && !$v.who.alpha"
          >Поле не должно содержать цифры</small>
          <br>

          <label><b>Дата выдачи *</b></label>
          <input type="date"
          v-model.trim="dateDoc"
          :class="{invalid: ($v.dateDoc.$dirty && !$v.dateDoc.required)}" >

          <small
          class="invalid-text"
          v-if="$v.dateDoc.$dirty && !$v.dateDoc.required"
          >Поле не должно быть пустым</small>

          <h2
          v-if="!$v.$invalid"
          >Ваша форма верна</h2>
       
          <div class="clearfix">
            <button type="button" class="cancelbtn">Отмена</button>
            <button type="submit" class="signupbtn">Зарегистрироваться</button>
          </div>
        
      </form>
  
    </div>
</template>

<script>
import {required , maxLength, minLength, } from 'vuelidate/lib/validators'



const rusNumber = function(value){
  return(/^((\+7|7|8)+([0-9]){10})$/gm.test(value))? true : false
}

// rusNumber : val => /^((\+7|7|8)+([0-9]){10})$/gm.test(val)

export default {
  name: 'HelloWorld',
  data: () => ({
    firstName: '',
    lastName: '',
    patronymic: '',
    date: null,
    phone: null,
    city:'',
    dateDoc:null,
    index:null,   
    series:null,
    number:null,
    who:''
    
  }),
  validations : {
    firstName:{alpha: val => /^[а-яё]*$/i.test(val), required  ,},
    lastName:{alpha: val => /^[а-яё]*$/i.test(val), required , },
    patronymic:{alpha: val => /^[а-яё]*$/i.test(val),},
    date:{required},
    phone:{required,  rusNumber ,},
    city:{required, alpha: val => /^[а-яё]*$/i.test(val),},
    dateDoc:{required},
    index:{ minLength:minLength(6), maxLength:maxLength(6)},
    series:{minLength:minLength(4), maxLength:maxLength(4)},
    number:{minLength:minLength(6), maxLength:maxLength(6)},
    who:{alpha: val => /^[а-яё]*$/i.test(val)}

  },
  methods: {
    submit(){
      if(this.$v.$invalid){
        this.$v.$touch()
        
        return
      }else{
        alert("Ваша форма отправлена")
      }
    },
  }
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss">
* {
  box-sizing: border-box;
}

/* Full-width input fields */
input[type=text], input[type=number], input[type=date], input[type=tel] {
  width: 100%;
  padding: 15px;
  margin: 5px 0 22px 0;
  display: inline-block;
  border: 1px;
  background: #f1f1f1;
}

label {
  display: inline-block;
  padding: 5px 5px;
  margin: 5px 5px;
}

input[type=text]:focus {
  background-color: #ddd;
  outline: none;
}

hr {
  border: 1px solid #f1f1f1;
  margin-bottom: 25px;
}

/* Set a style for all buttons */
button {
  background-color: #4CAF50;
  color: white;
  padding: 14px 20px;
  margin: 8px 0;
  border: none;
  cursor: pointer;
  width: 100%;
  opacity: 0.9;
}

button:hover {
  opacity: 1;
}

.invalid-text{
  color: red;
}

.__select {
  display: flex;
  margin: 0 auto;
  overflow: hidden;
  border-radius: 5px;
  border: solid 1px #4CAF50;
}

.__select__content {
  margin-right: 0;
  display: flex;
  flex-shrink: 0;
  flex-direction: column;
  width: 100%;
  overflow-y: auto;
  overflow-x: hidden;
}

.__select__input {
  display: none;
}
.__select__input:checked + label {
  background-color: #4CAF50;
}
.__select__input:disabled + label {
  opacity: 0.6;
  pointer-events: none;
}

.__select__label {
  display: flex;
  align-items: center;
  flex-shrink: 0;
  height: 40px;
  padding: 0 16px;
  transition: all 0.2s ease-out;
  cursor: pointer;
}
.__select__label + input + .__select__label {
  border-top: 1px solid #C7CCD160;
}
.__select__label:hover {
  background-color: #D8093A !important;
  color: #ffffff;
}

/* Extra styles for the cancel button */
.cancelbtn {
  padding: 14px 20px;
  background-color: #f44336;
}

/* Float cancel and signup buttons and add an equal width */
.cancelbtn, .signupbtn {
  float: left;
  width: 50%;
}

/* Add padding to container elements */
.container {
  padding: 16px;
}

/* Clear floats */
.clearfix::after {
  content: "";
  clear: both;
  display: table;
}

.form_radio_btn {
  display: inline-block;
  margin-right: 10px;
}

.form_radio_btn input[type=radio] {
  display: none;
}

.form_radio_btn label {
  display: inline-block;
  cursor: pointer;
  padding: 0px 15px;
  line-height: 34px;
  border: 1px solid #999;
  border-radius: 6px;
  user-select: none;
}

/* Checked */
.form_radio_btn input[type=radio]:checked + label {
  background: #47e747;
}

/* Hover */
.form_radio_btn label:hover {
  color: #666;
}

.select-css {
  display: block;
  font-size: 16px;
  font-family: sans-serif;
  font-weight: 700;
  color: #444;
  line-height: 1.3;
  padding: 0.6em 1.4em 0.5em 0.8em;
  width: 100%;
  max-width: 100%;
  box-sizing: border-box;
  margin: 0;
  border: 1px solid #aaa;
  box-shadow: 0 1px 0 1px rgba(0, 0, 0, 0.04);
  border-radius: 0.5em;
  -moz-appearance: none;
  -webkit-appearance: none;
  appearance: none;
  background-color: #fff;
  background-image: url("data:image/svg+xml;charset=US-ASCII,%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%22292.4%22%20height%3D%22292.4%22%3E%3Cpath%20fill%3D%22%23007CB2%22%20d%3D%22M287%2069.4a17.6%2017.6%200%200%200-13-5.4H18.4c-5%200-9.3%201.8-12.9%205.4A17.6%2017.6%200%200%200%200%2082.2c0%205%201.8%209.3%205.4%2012.9l128%20127.9c3.6%203.6%207.8%205.4%2012.8%205.4s9.2-1.8%2012.8-5.4L287%2095c3.5-3.5%205.4-7.8%205.4-12.8%200-5-1.9-9.2-5.5-12.8z%22%2F%3E%3C%2Fsvg%3E"), linear-gradient(to bottom, #ffffff 0%, #e5e5e5 100%);
  background-repeat: no-repeat, repeat;
  background-position: right 0.7em top 50%, 0 0;
  background-size: 0.65em auto, 100%;
}

.select-css::-ms-expand {
  display: none;
}

.select-css:hover {
  border-color: #888;
}

.select-css:focus {
  border-color: #aaa;
  box-shadow: 0 0 1px 3px rgba(59, 153, 252, 0.7);
  box-shadow: 0 0 0 3px -moz-mac-focusring;
  color: #222;
  outline: none;
}

.select-css option {
  font-weight: normal;
}

*[dir=rtl] .select-css, :root:lang(ar) .select-css, :root:lang(iw) .select-css {
  background-position: left 0.7em top 50%, 0 0;
  padding: 0.6em 0.8em 0.5em 1.4em;
}

.custom-select {
  position: relative;
}

/* Change styles for cancel button and signup button on extra small screens */
@media screen and (max-width: 300px) {
  .cancelbtn, .signupbtn {
    width: 100%;
  }
}
</style>
