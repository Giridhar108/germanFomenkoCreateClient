<template>
  <form class="sign-up" @submit.prevent="checkForm">
    <div class="main-inf">
      <div class="form">
        <label class="form__label" for="main-inf">Лечащий врач</label>
        <select class="form__control form__select">
          <option>Apples</option>
          <option>Apples</option>
          <option>Apples</option>
        </select>

        <div class="form__main">
          <div class="form__top">
            <label class="form__label" for="">Фамилия*</label>
            <input id="login" class="form__control" placeholder="Фамилия" />
          </div>
          <div class="form__top">
            <label class="form__label" for="">Имя*</label>
            <input id="login" class="form__control" placeholder="Имя" />
          </div>
          <div class="form__top">
            <label class="form__label" for="">Отчество</label>
            <input id="login" class="form__control" placeholder="Отчество" />
          </div>
          <div class="form__top">
            <label class="form__label" for="">Дата рождения*</label>
            <input
              id="login"
              class="form__control"
              placeholder="Дата рождения"
            />
          </div>
          <div class="form__top">
            <label class="form__label" for="">Пол</label>
            <input id="login" class="form__control" placeholder="Пол" />
          </div>
        </div>
      </div>
    </div>

    <div class="main-passport">
      <div class="form-group">
        <label for="">Паспорт</label>

        <div class="form__main">
          <div class="form__top">
            <label class="form__label" for="">Тип документа*</label>
            <input
              id="login"
              class="form__control"
              placeholder="Тип документа"
            />
          </div>
          <div class="form__top">
            <label class="form__label" for="">Серия</label>
            <input id="login" class="form__control" placeholder="Серия" />
          </div>
          <div class="form__top">
            <label class="form__label" for="">Номер</label>
            <input id="login" class="form__control" placeholder="Номер" />
          </div>
          <div class="form__top">
            <label class="form__label" for="">Кем выдан*</label>
            <input id="login" class="form__control" placeholder="Кем выдан" />
          </div>
          <div class="form__top">
            <label class="form__label" for="">Дата выдачи*</label>
            <input id="login" class="form__control" placeholder="Дата выдачи" />
          </div>
        </div>
      </div>
    </div>

    <div class="main-adress">
      <div class="form-group">
        <label for="">Адрес</label>

        <div class="form__main">
          <div class="form__top">
            <label class="form__label" for="">Страна</label>
            <input id="login" class="form__control" placeholder="Страна" />
          </div>
          <div class="form__top">
            <label class="form__label" for="">Область</label>
            <input id="login" class="form__control" placeholder="Область" />
          </div>
          <div class="form__top">
            <label class="form__label" for="">Город</label>
            <input id="login" class="form__control" placeholder="Город" />
          </div>
          <div class="form__top">
            <label class="form__label" for="">Улица</label>
            <input id="login" class="form__control" placeholder="Улица" />
          </div>

          <div class="form__top form__top-index">
            <div>
              <label class="form__label-index" for="">Индекс</label>
              <input
                id="login"
                class="form__control index"
                placeholder="Индекс"
              />
            </div>
            <div>
              <label class="form__label-index" for="">Дом</label>
              <input id="login" class="form__control index" placeholder="Дом" />
            </div>
          </div>
        </div>
      </div>
    </div>

    <div class="main-create">
      <div class="form-group">
        <div class="form__main">
          <div class="form__top">
            <label class="form__label" for="">Номер телефона*</label>
            <input
              id="login"
              class="form__control"
              placeholder="+7 (___) __ __ ___"
            />
          </div>

          <div class="form__top">
            <label class="form__label" for="">Группа клиентов*</label>
            <select
              id="groups"
              class="form__control form__select-group"
              multiple
            >
              <option>VIP</option>
              <option>Проблемные</option>
              <option>ОМС</option>
            </select>
          </div>

          <div class="form__btn-bottom">
            <div class="form__top">
              <label class="form__label" for="notification">
                Не отправлять СМС
              </label>
              <input
                class="form__checkbox"
                type="checkbox"
                value="male"
                name="checkbox"
                id="notification"
              />
            </div>
            <button type="submit" class="btn btn-primary">
              Создать клиента
            </button>
          </div>

        </div>
      </div>
    </div>
  </form>
</template>

<script>
// import { validationMixin } from 'vuelidate';
// import { required, minLength, email } from 'vuelidate/lib/validators';

export default {
  // mixins: [validationMixin],
  data() {},
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
:focus {
  outline-color: #00d2c5;
}
.sign-up {
  display: flex;
  justify-content: space-around;
}
.main-passport,
.main-adress {
  margin-top: 60px;
}
.main-create {
  margin-top: 85px;
}
.form {
  display: flex;
  flex-direction: column;
  &__label {
    font-size: 16px;
  }
  &__control {
    margin-top: 8px;
    width: 200px;
    height: 35px;
    padding: 0 10px;
    background: #e9d2c5;
    box-shadow: inset 2px 4px 2px rgba(0, 0, 0, 0.25);
    border-radius: 8px;
    border: none;
    font-family: Roboto;
    font-style: normal;
    font-weight: bold;
    font-size: 18px;
    line-height: 21px;
    display: flex;
    align-items: center;
    color: #414141;
    transition: border-color 0.15s ease-in-out, box-shadow 0.15s ease-in-out;
    &:focus {
      border-color: #00d2c5;
      outline: 0;
      box-shadow: 0 0 0 2px #00d2c5, inset 2px 4px 2px rgba(0, 0, 0, 0.25);
    }
  }
  &__select {
    width: 200px;
  }
  &__main {
    margin-top: 40px;
  }
  &__top {
    margin-top: 16px;
  }
  &__top-index {
    display: flex;
    justify-content: space-between;
  }
  &__select-group {
    height: auto;
    padding-top: 10px;
  }
  &__btn-bottom {
    margin-top: 120px;
  }
}

.btn {
  margin-top: 10px;
  font-style: normal;
  font-weight: bold;
  font-size: 20px;
  line-height: 29px;
  width: 200px;
  height: 40px;
  color: #ffffff;
  background: #00d2c5;
  border-radius: 8px;
  border: none;
  &:hover {
    background: #029288;
  }
}

.index {
  width: 79px;
  height: 35px;
}
</style>
