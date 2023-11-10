<template>
  <div class="columns">
    <q-form class="form" @submit.prevent="formData">
      <q-radio v-model="entityData" val="individual" label="Физ. лицо" />
      <q-radio v-model="entityData" val="legal" label="Юр. лицо" />

      <q-input
        v-model="contractDate"
        label="Дата договора"
        type="date"
        outlined
      />
      <div class="individual" v-if="entityData === 'individual'">
        <q-input v-model="fullName" type="text" label="ФИО" outlined />
        <q-input
          v-model="documentId"
          label="Уд.личности №"
          type="number"
          outlined
        />
        <q-input
          v-model="issuedBy"
          label="Кем выдан документ"
          type="text"
          outlined
        />
        <q-input
          v-model="issuedWhen"
          label="Когда выдан документ"
          type="date"
          outlined
        />
        <q-input
          v-model="address"
          label="Адрес проживания"
          type="text"
          outlined
        />
      </div>

      <div class="legal" v-if="entityData === 'legal'">
        <q-input
          v-model="companyName"
          type="text"
          label="Название компании"
          outlined
        />
        <q-input v-model="fullName" type="text" label="ФИО" outlined />
        <q-input
          v-model="address"
          label="Адрес проживания"
          type="text"
          outlined
        />
      </div>

      <q-input
        v-model="service"
        type="text"
        label="Напиши услугу"
        outlined
      ></q-input>
      <q-input
        v-model="prepayment"
        type="number"
        label="Сумма предоплаты"
        outlined
      ></q-input>
      <div class="individual" v-if="entityData === 'individual'">
        <q-input
          v-model="iinNumber"
          type="number"
          label="ИИН"
          outlined
        ></q-input>
        <q-input
          v-model="phoneNumber"
          type="number"
          label="Номер Телефона"
          outlined
        ></q-input>
      </div>
      <div class="legal" v-if="entityData === 'legal'">
        <q-input
          v-model="binNumber"
          type="number"
          label="БИН"
          outlined
        ></q-input>
        <q-input
          v-model="postalCode"
          type="text"
          label="Почтовый индекс"
          outlined
        ></q-input>
        <q-input
          v-model="bankName"
          type="text"
          label="Название банка"
          outlined
        ></q-input>
        <q-input v-model="bik" type="number" label="БИК" outlined></q-input>
      </div>
      <q-btn type="submit" label="Сохранить" color="primary" />
    </q-form>
    <div class="pages">
      <div class="a4-sheet">
        <h3 class="header">
          Договор предоплаты купли-продажи набора кухонной мебели
        </h3>
        <div class="city-and-date">
          <p>г.Алматы</p>
          <p>
            &laquo; <input type="date" :value="contractDate" />
            &raquo;
          </p>
        </div>
        <div class="block" v-if="entityData === 'individual'">
          <p>
            ТОО «Test» в лице директора Иванов Иван, действующего на основании
            Устава, именуемое в дальнейшем «Продавец», с одной стороны, и гр.
            <input type="text" name="fullName" :value="fullName" /> уд.личности:
            № <input type="number" name="document-id" :value="documentId" />,
            выданный
            <input type="text" name="doc-issued-by" :value="issuedBy" />,
            проживающий по адресу:
            <input type="text" name="address" :value="address" />, именуемый в
            дальнейшем «Покупатель», с другой стороны, заключили настоящий
            Договор предоплаты о нижеследующем:
          </p>
        </div>
        <div class="block" v-if="entityData === 'legal'">
          <p>
            ТОО «Test» в лице директора Иванов Иван, действующего на основании
            Устава, именуемое в дальнейшем «Продавец», с одной стороны, и
            <input
              type="text"
              name="companyName"
              :value="companyName"
              placeholder="название компании"
            />
            в лице директора
            <input type="text" name="fullName" :value="fullName" />,
            действующего на основании Устава, расположенный по адресу:
            <input type="text" name="address" :value="address" />, именуемый в
            дальнейшем «Покупатель», с другой стороны, заключили настоящий
            Договор предоплаты о нижеследующем:
          </p>
        </div>
        <div class="block">
          <h3>1. ПРЕДМЕТ ДОГОВОРА.</h3>
          <p>
            1.1. Продавец обязуется передать в собственность Покупателя набор
            мебели для кухни (далее «Товар»), а Покупатель обязуется принять
            Товар и уплатить Продавцу за него денежную сумму, в порядке и
            размере, предусмотренных Договором.
          </p>
          <p>
            1.2. Предметом Договора является Товар, заказанный Покупателем и
            соответствующий описанию, предусмотренного Приложением №1 к
            Основному Договору;
          </p>
          <p>
            1.3. Покупателю могут быть предоставлены дополнительные услуги по
            <input type="text" name="services" :value="service" />
          </p>
          <p>
            1.3.1. стоимость Услуг не включается в стоимость Товара. Указанные
            услуги предоставляются Покупателю только при условии приобретения
            Товара.
          </p>
        </div>
        <div class="block">
          <h3>2. ПОРЯДОК ИСПОЛНЕНИЯ ДОГОВОРА</h3>
          <p>
            2.1. Покупатель, ознакомившись с демонстрируемыми образцами,
            потребительскими свойствами и условиями поставки, заказывает
            необходимый ему Товар и заключает Договор предоплаты. При этом,
            стороны в дальнейшем обязуются заключить Основной Договор
            купли-продажи кухонного набора (далее «Основной Договор»).
          </p>
        </div>
        <div class="block">
          <h3>3. ПОРЯДОК РАСЧЕТОВ И СУММА ДОГОВОРА</h3>
          <p>
            3.1. Цена Товара и дополнительных услуг определяется в момент
            заключения Основного Договора:
          </p>
          <p>
            3.1.1. в момент заключения Договора предоплаты Покупатель вносит
            предоплату на счет Продавца в размере
            <input type="number" id="prepayment" :value="prepayment" /> тенге;
          </p>
          <p>
            3.1.2. оставшуюся сумму Покупатель оплачивает в момент заключения
            Основного Договора.
          </p>
        </div>
        <div class="block">
          <h3>4. СРОК ДЕЙСТВИЯ ДОГОВОРА</h3>
          <p>4.1. Договор вступает в силу с момента его подписания.</p>
          <p>
            4.2. Датой окончания договора будет дата передачи Покупателю или
            лицам, его представляющим, Товара, соответствующего описанию,
            указанному в Приложениях Основного Договора. При оказании услуг,
            указанных в Договоре, Договор считается исполненным с момента
            выполнения этих услуг.
          </p>
        </div>
        <div class="block">
          <h3>5. ОТВЕТСТВЕННОСТЬ СТОРОН</h3>
          <p>
            5.1. Право собственности на Товар переходит к Покупателю в момент
            100% оплаты стоимости Товара.
          </p>
          <p>
            5.2. В случае отказа Покупателем от Товара, после его письменного
            обращения, Продавец, в течение 14 (четырнадцати) рабочих дней,
            возвращает сумму, оплаченную Покупателем за Товар, за вычетом
            фактически понесенных Продавцом расходов.
          </p>
          <p>
            5.3. Стороны освобождаются от ответственности за частичное или
            полное неисполнение обязательств по настоящему договору, если это
            неисполнение явилось следствием обстоятельств непреодолимой силы,
            возникших после заключения настоящего договора в результате событий
            чрезвычайного характера, которые сторона не могла предвидеть или
            предотвратить разумными мерами (форс-мажорные обстоятельства). К
            таким событиям относятся наводнения, пожар, землетрясения, взрыв,
            шторм, оседание почвы, эпидемия и иные явления природы, военные
            действия, технологические катастрофы.
          </p>
        </div>
        <div class="block">
          <h3>6. РАЗРЕШЕНИЕ СПОРОВ</h3>
          <p>
            6.1. Все разногласия и споры, которые могут возникнуть между
            сторонами из настоящего договора и в связи с ним, будут по
            возможности решаться путем переговоров.
          </p>
          <p>
            6.2. В случае, когда возникшие споры путем переговоров не
            урегулированы, они подлежат разрешению в судах по месту нахождения
            Продавца.
          </p>
        </div>
      </div>
      <div class="a4-sheet">
        <div class="block">
          <h3>7. ФОРС-МАЖОРНЫЕ ОБСТОЯТЕЛЬСТВА</h3>
          <p>
            7.1 В случае наступления форс-мажорных обстоятельств пострадавшая
            Сторона обязана в кратчайшие сроки предупредить другую Сторону о
            невозможности исполнения своих обязательств по настоящему Договору.
          </p>
          <p>
            7.2. При этом ни одна Сторона не может требовать возмещения
            каких-либо убытков или потерь, связанных с невыполнением Договора.
          </p>
        </div>
        <div class="block">
          <h3>8. ПРОЧИЕ УСЛОВИЯ ДОГОВОРА</h3>
          <p>
            8.1. Настоящий Договор, а также любые приложения к нему, заключается
            между двумя Сторонами в двух экземплярах, имеющих равную юридическую
            силу, и передаются по одному экземпляру каждой из сторон.
          </p>
          <p>
            8.2. Ни одна из сторон договора не вправе передавать свои права по
            Договору другому лицу без письменного согласия другой Стороны.
          </p>
        </div>
        <div class="block">
          <h3>9. АДРЕСА И РЕКВИЗИТЫ СТОРОН.</h3>
          <table>
            <thead>
              <tr>
                <th>ПРОДАВЕЦ:</th>
                <th>ПОКУПАТЕЛЬ:</th>
              </tr>
            </thead>
            <tbody>
              <tr>
                <td>ТОО «Test»</td>
                <td v-if="entityData === 'individual'">ФИО {{ fullName }}</td>
                <td v-else>Название компании: {{ companyName }}</td>
              </tr>
              <tr>
                <td>Юр. адрес: г. Алматы, ул. Дундича д. 245</td>
                <td>
                  <div class="table-row" v-if="entityData === 'individual'">
                    <span>Регистрация: {{ address }}</span>
                    <span>Место жительство: {{ address }}</span>
                    <span>Телефон: {{ phoneNumber }}</span>
                  </div>
                  <div class="table-row" v-if="entityData === 'legal'">
                    <span>Юр адрес: {{ address }}</span>
                  </div>
                </td>
              </tr>
              <tr>
                <td>Почтовый адрес:00000</td>
                <td>Почтовый адрес: {{ postalCode }}</td>
              </tr>
              <tr>
                <td>БИН: 1111111111</td>
                <td v-if="entityData === 'individual'">ИИН: {{ iinNumber }}</td>
                <td v-if="entityData === 'legal'">БИН: {{ binNumber }}</td>
              </tr>
              <tr>
                <td>АО «KaspiBank» p/c: 11111111111 БИК: CASPKZKA</td>
                <td>
                  <div class="table-row" v-if="entityData === 'individual'">
                    <span>Удост. личности №: {{ documentId }}</span>
                    <span>Выдано когда: {{ issuedWhen }}</span>
                    <span>Кем: {{ issuedBy }}</span>
                  </div>
                  <div class="table-row" v-else>
                    <span>Банк: {{ bankName }}</span>
                    <span>p/c: </span>
                    <span>БИК: {{ bik }}</span>
                  </div>
                </td>
              </tr>
            </tbody>
          </table>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";

const contractDate = ref(null);

const fullName = ref("");
const documentId = ref(null);
const issuedBy = ref("");
const address = ref("");
const entityData = ref("individual");

const companyName = ref("");

const service = ref("");
const prepayment = ref(null);

const iinNumber = ref(null);
const binNumber = ref(null);
const phoneNumber = ref(null);

const issuedWhen = ref(null);

const postalCode = ref(null);
const bankName = ref("");
const bik = ref(null);

const formData = () => {
  alert("Данные отправлены");
};
</script>

<style>
.columns {
  display: flex;
  justify-content: space-between;
  width: 1200px;
  margin: 0 auto;
}

.form {
  position: sticky;
  top: 0;
}

.pages {
  height: 1000px;
}

.a4-sheet {
  width: 21cm;
  height: 29.7cm;
  margin: 1cm auto;
  padding: 2cm 2cm;
  border: 1px solid #ccc;
}

.city-and-date {
  display: flex;
  justify-content: space-between;
  margin: 0.5cm 0;
}

.date {
  display: flex;
  width: 100px;
  border-bottom: 1px solid #000;
}

table,
th,
td {
  border: 1px solid black;
  border-collapse: collapse;
  width: 50%;
}

table {
  width: 100%;
}

.table-row {
  display: flex;
  flex-direction: column;
}

.individual {
  background-color: aqua;
}

.legal {
  background-color: rgb(98, 255, 0);
}
</style>
