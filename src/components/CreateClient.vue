<template>
  <form v-if="!registrationPassed" class="sign-up" @submit.prevent="checkForm">
    <div class="main main-inf">
      <div class="form">
        <label class="form__label" for="healers">Лечащий врач</label>
        <select
          id="healers"
          class="form__control form__select"
          v-model="form.healers"
        >
          <option
            v-for="(healer, index) in healers"
            :value="healer.value"
            :key="index"
          >
            {{ healer.label }}
          </option>
        </select>

        <div class="form__main">
          <div class="form__top form__top-margin">
            <label class="form__label" for="surname">Фамилия*</label>
            <input
              id="surname"
              class="form__control"
              :class="$v.form.surname.$error ? 'is-invalid' : ''"
              v-model.trim="form.surname"
              placeholder="Фамилия"
            />
            <p
              v-if="$v.form.surname.$dirty && !$v.form.surname.required"
              class="invalid-feedback"
            >
              Обязательное поле
            </p>
          </div>
          <div class="form__top">
            <label class="form__label" for="name">Имя*</label>
            <input
              id="name"
              class="form__control"
              :class="$v.form.name.$error ? 'is-invalid' : ''"
              v-model.trim="form.name"
              placeholder="Имя"
            />
            <p
              v-if="$v.form.name.$dirty && !$v.form.name.required"
              class="invalid-feedback"
            >
              Обязательное поле
            </p>
          </div>
          <div class="form__top">
            <label class="form__label" for="patronymic">Отчество</label>
            <input
              id="patronymic"
              class="form__control"
              v-model.trim="form.patronymic"
              placeholder="Отчество"
            />
          </div>
          <div class="form__top">
            <label class="form__label" for="">Дата рождения*</label>
            <input
              id="birthday"
              type="date"
              class="form__control"
              :class="$v.form.birthday.$error ? 'is-invalid' : ''"
              v-model.trim="form.birthday"
              placeholder="Дата рождения"
            />
            <p
              v-if="$v.form.birthday.$dirty && !$v.form.birthday.required"
              class="invalid-feedback"
            >
              Обязательное поле
            </p>
          </div>
          <div class="form__top">
            <label class="form__label" for="sex">Пол</label>
            <input
              id="sex"
              class="form__control"
              v-model.trim="form.sex"
              placeholder="Пол"
            />
          </div>
        </div>
      </div>
    </div>

    <div class="main main-passport">
      <div class="form-group">
        <h3>Паспорт</h3>
        <div class="form__main">
          <div class="form__top">
            <label class="form__label" for="typeDoc">Тип документа*</label>
            <select
              id="typeDoc"
              v-model="form.typeDoc"
              class="form__control"
              :class="$v.form.typeDoc.$error ? 'is-invalid' : ''"
            >
              <option
                v-for="(type, index) in typeDoc"
                :value="type.value"
                :key="index"
              >
                {{ type.label }}
              </option>
            </select>
            <p
              v-if="$v.form.typeDoc.$dirty && !$v.form.typeDoc.required"
              class="invalid-feedback"
            >
              Обязательное поле
            </p>
          </div>

          <div class="form__top">
            <label class="form__label" for="seriesPass">Серия</label>
            <input
              id="seriesPass"
              class="form__control"
              :class="$v.form.seriesPass.$error ? 'is-invalid' : ''"
              v-model.trim="form.seriesPass"
              placeholder="Серия"
            />
            <p
              v-if="$v.form.seriesPass.$dirty && !$v.form.seriesPass.minLength"
              class="invalid-feedback"
            >
              Здесь должно быть больше 4-х цифр
            </p>
            <p
              v-if="
                $v.form.seriesPass.$dirty && !$v.form.seriesPass.onlyNumbers
              "
              class="invalid-feedback"
            >
              Только цифры
            </p>
          </div>

          <div class="form__top">
            <label class="form__label" for="numberPass">Номер</label>
            <input
              id="numberPass"
              class="form__control"
              :class="$v.form.numberPass.$error ? 'is-invalid' : ''"
              v-model.trim="form.numberPass"
              placeholder="Номер"
            />
            <p
              v-if="$v.form.numberPass.$dirty && !$v.form.numberPass.minLength"
              class="invalid-feedback"
            >
              Здесь должно быть больше 6-и цифр
            </p>
            <p
              v-if="
                $v.form.numberPass.$dirty &&
                !$v.form.numberPass.onlyNumbers &&
                $v.form.numberPass.minLength
              "
              class="invalid-feedback"
            >
              Только цифры
            </p>
          </div>

          <div class="form__top">
            <label class="form__label" for="whoGet">Кем выдан*</label>
            <input
              id="whoGet"
              class="form__control"
              :class="$v.form.whoGet.$error ? 'is-invalid' : ''"
              v-model.trim="form.whoGet"
              placeholder="Кем выдан"
            />
            <p
              v-if="$v.form.whoGet.$dirty && !$v.form.whoGet.required"
              class="invalid-feedback"
            >
              Обязательное поле
            </p>
          </div>
          <div class="form__top">
            <label class="form__label" for="dateGet">Дата выдачи*</label>
            <input
              id="dateGet"
              type="date"
              class="form__control"
              :class="$v.form.dateGet.$error ? 'is-invalid' : ''"
              v-model.trim="form.dateGet"
              placeholder="Дата выдачи"
            />
            <p
              v-if="$v.form.dateGet.$dirty && !$v.form.dateGet.required"
              class="invalid-feedback"
            >
              Обязательное поле
            </p>
          </div>
        </div>
      </div>
    </div>

    <div class="main main-adress">
      <div class="form-group">
        <h3>Адрес</h3>

        <div class="form__main">
          <div class="form__top">
            <label class="form__label" for="country">Страна</label>
            <input
              id="country"
              class="form__control"
              v-model.trim="form.country"
              placeholder="Страна"
            />
          </div>
          <div class="form__top">
            <label class="form__label" for="region">Область</label>
            <input
              id="region"
              class="form__control"
              v-model.trim="form.region"
              placeholder="Область"
            />
          </div>
          <div class="form__top">
            <label class="form__label" for="city">Город</label>
            <input
              id="city"
              class="form__control"
              v-model.trim="form.city"
              placeholder="Город"
            />
          </div>
          <div class="form__top">
            <label class="form__label" for="street">Улица</label>
            <input
              id="street"
              class="form__control"
              v-model.trim="form.street"
              placeholder="Улица"
            />
          </div>

          <div class="form__top form__top-index">
            <div>
              <label class="form__label-index" for="index">Индекс</label>
              <input
                id="index"
                class="form__control index"
                :class="$v.form.index.$error ? 'is-invalid' : ''"
                v-model.trim="form.index"
                placeholder="Индекс"
              />
              <p
                v-if="$v.form.index.$dirty && !$v.form.index.onlyNumbers"
                class="invalid-feedback"
              >
                Только цифры
              </p>
            </div>
            <div>
              <label class="form__label-index" for="homeNumber">Дом</label>
              <input
                id="homeNumber"
                class="form__control index"
                v-model.trim="form.homeNumber"
                placeholder="Дом"
              />
            </div>
          </div>
        </div>
      </div>
    </div>

    <div class="main main-create">
      <div class="form-group">
        <div class="form__main">
          <div class="form__top">
            <label class="form__label" for="phoneNumber">Номер телефона*</label>
            <input
              id="phoneNumber"
              class="form__control"
              :class="$v.form.phoneNumber.$error ? 'is-invalid' : ''"
              v-model.trim="form.phoneNumber"
              placeholder="+7"
            />
            <p
              v-if="$v.form.phoneNumber.$dirty && !$v.form.phoneNumber.required"
              class="invalid-feedback"
            >
              Обязательное поле
            </p>
            <p
              v-if="
                $v.form.phoneNumber.$dirty &&
                !$v.form.phoneNumber.valid &&
                $v.form.phoneNumber.required
              "
              class="invalid-feedback"
            >
              Не правильный номер
            </p>
          </div>

          <div class="form__top">
            <label class="form__label" for="groupClient"
              >Группа клиентов*</label
            >
            <select
              id="groupClient"
              class="form__control form__select-group"
              :class="$v.form.groupClient.$error ? 'is-invalid' : ''"
              v-model.trim="form.groupClient"
              multiple
            >
              <option>VIP</option>
              <option>Проблемные</option>
              <option>ОМС</option>
            </select>
            <p
              v-if="$v.form.groupClient.$dirty && !$v.form.groupClient.required"
              class="invalid-feedback"
            >
              Обязательное поле
            </p>
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
                v-model="form.sms"
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
  <div v-else class="success">
    <p>Поздравляем!</p>
    <p>{{ `Клиент ${form.name} ${form.surname}` }}</p>
    <p>успешно зарегистрирован!</p>
  </div>
</template>

<script>
import { validationMixin } from 'vuelidate';
import { required, minLength } from 'vuelidate/lib/validators';
import onlyNumbers from '../utils/onlyNumbers';
import validPhone from '../utils/validPhone';

export default {
  mixins: [validationMixin],
  data() {
    return {
      registrationPassed: false,
      form: {
        surname: '',
        name: '',
        patronymic: '',
        birthday: '',
        sex: '',
        typeDoc: '',
        seriesPass: '',
        numberPass: '',
        whoGet: '',
        dateGet: '',
        country: '',
        region: '',
        city: '',
        street: '',
        index: '',
        homeNumber: '',
        phoneNumber: '',
        groupClient: [],
        sms: false,
      },
      healers: [
        {
          label: '',
          value: '',
        },
        {
          label: 'Иванов',
          value: 'Ivanov',
        },
        {
          label: 'Захаров',
          value: 'Zaharov',
        },
        {
          label: 'Чернышева',
          value: 'Chernishova',
        },
      ],
      typeDoc: [
        {
          label: 'Паспорт',
          value: 'The passport',
        },
        {
          label: 'Свидетельство о рождении',
          value: 'Birth certificate',
        },
        {
          label: 'Вод. удостоверение',
          value: "Driver's license",
        },
      ],
    };
  },
  validations: {
    form: {
      surname: { required },
      name: { required },
      birthday: { required },
      typeDoc: { required },
      seriesPass: { onlyNumbers, minLength: minLength(4) },
      numberPass: { onlyNumbers, minLength: minLength(6) },
      whoGet: { required },
      dateGet: { required },
      phoneNumber: { validPhone, required },
      groupClient: { required },
      index: { onlyNumbers },
    },
  },
  methods: {
    checkForm() {
      this.$v.form.$touch();
      if (!this.$v.form.$error) {
        this.registrationPassed = true;
      }
    },
  },
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
.main {
  margin: 0 15px;
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
    display: flex;
    align-items: center;
    margin-top: 8px;
    width: 200px;
    height: 35px;
    padding: 0 10px;
    background: #f8e3d7;
    box-shadow: inset 2px 4px 2px rgba(0, 0, 0, 0.25);
    border-radius: 8px;
    border: none;
    font-family: Roboto;
    font-style: normal;
    font-weight: bold;
    font-size: 18px;
    line-height: 21px;
    color: #414141;
    &:focus {
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
    margin-top: 26px;
  }
  &__top-margin {
    margin-top: 16px;
  }
  &__top-index {
    display: flex;
    justify-content: space-between;
  }
  &__select-group {
    height: auto;
    padding-top: 10px;
    & option:checked {
      background-color: #029288 !important;
    }
  }
  &__btn-bottom {
    margin-top: 150px;
  }
  &__checkbox {
    box-shadow: inset 2px 2px 2px rgba(0, 0, 0, 0.25);
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
  box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1),
    0 2px 4px -1px rgba(0, 0, 0, 0.06);
  &:hover {
    background: #029288;
  }
  &:focus {
    outline: 0;
    box-shadow: 0 0 0 2px #00625c;
  }
}

.index {
  width: 79px;
  height: 35px;
}
.is-invalid {
  box-shadow: 0 0 0 2px #d20000, inset 2px 4px 2px rgba(0, 0, 0, 0.25);
}
.invalid-feedback {
  position: absolute;
  font-size: 12px;
  color: #d20000;
}
.success {
  text-align: center;
  line-height: 2;
  font-weight: bold;
  font-size: 24px;
}
@media (max-width: 950px) {
  .sign-up {
    flex-wrap: wrap;
    margin-bottom: 40px;
  }
  .form__btn-bottom {
    margin-top: 0;
  }
}
</style>
