<template>
  <v-container>
    <v-form ref="form" v-model="valid" lazy-validation>
      <v-row>
        <!--  -->

        <v-col cols="4"
          ><v-text-field
            v-model="no_p"
            :rules="no_pRules"
            :counter="10"
            label="รหัสสินค้า"
            required
          ></v-text-field
        ></v-col>

        <v-col cols="4">
          <v-text-field
            v-model="name_p"
            :counter="30"
            :rules="name_pRules"
            label="ชื่อสินค้า"
            required
          ></v-text-field
        ></v-col>
 
        <v-col cols="4"
          ><v-text-field
            v-model="n"
            :rules="nRules"
            :counter="10"
            label="จำนวนสินค้า"
            required
          ></v-text-field
        ></v-col>
        
         <v-col cols="4"
          ><v-text-field
            v-model="color"
            :rules="colorRules"
            :counter="10"
            label="สีสินค้า"
            required
          ></v-text-field
        ></v-col>

        <v-col cols="4"
          ><v-text-field
            v-model="weight"
            :rules="weightRules"
            :counter="10"
            label="น้ำหนักสินค้า"
            required
          ></v-text-field
        ></v-col>
        <v-col cols="4"
          ><v-text-field
            v-model="Product "
            :rules="ProductRules"
            :counter="10"
            label="ประเภทสินค้า"
            required
          ></v-text-field
        ></v-col>
      </v-row>
      <v-row>
        <v-col cols="6"
          ><v-text-field
            v-model="coin"
            :rules="coinRules"
            :counter="10"
            label="ราคา"
            required
          ></v-text-field
        ></v-col>
      </v-row>



      <v-checkbox
        v-model="checkbox"
        :rules="checkboxRules"
        label="ตรวจสอบแล้ว"
        required
      ></v-checkbox>

      <v-btn :disabled="!valid" color="success" class="mr-4" @click="validate">
        เพิ่มสินค้า
      </v-btn>

      <v-btn color="error" class="mr-4" @click="reset">
        เคลียร์
      </v-btn>

      <v-row>
        <v-col cols="12">
          <!-- ตารางแสดงข้อมูล -->
          <v-card>
            <v-card-title>
              ข้อมูลลูกค้า
              <v-spacer></v-spacer>
              <v-text-field
                v-model="search"
                append-icon="mdi-magnify"
                label="Search"
                single-line
                hide-details
              ></v-text-field>
            </v-card-title>
            <v-data-table
              :headers="headers"
              :items="desserts"
              :search="search"
            ></v-data-table>
          </v-card>
        </v-col>
      </v-row>

      <!-- <v-btn
      color="warning"
      @click="resetValidation"
    >
      เคลียร์การตรวจสอบ
    </v-btn> -->
    </v-form>
  </v-container>
</template>

<script>
export default {
  data: () => ({
    valid: false,
    name_p: "",
    name_pRules: [
      v => !!v || "กรุณากรอกชื่อสินค้า",
      v => (v && v.length <= 30) || "ชื่อต้องมีขนาดไม่เกิน 30 ตัวอักษร"
    ],
    Product: "",
    ProductpRules: [
      v => !!v || "กรุณากรอกประเภทสินค้า",
      v => (v && v.length <= 30) || "ชื่อต้องมีขนาดไม่เกิน 30 ตัวอักษร"
    ],
   weight: "",
   weightRules: [
      v => !!v || "กรุณากรอกน้ำหนักสินค้า",
      v => (v && v.length <= 30) || "ชื่อต้องมีขนาดไม่เกิน 30 ตัวอักษร"
    ],
    color: "",
    colorRules: [
      v => !!v || "กรุณากรอกสีสินค้า",
      v => (v && v.length <= 30) || "ชื่อต้องมีขนาดไม่เกิน 30 ตัวอักษร"
    ],
    n: "",
    nRules: [
      v => !!v || "กรุณากรอกจำนวน",
      v => (v && v.length <= 10) || "ต้องมีความยาวไม่เกิน 10 หลัก"
    ],
    coin: "",
    coinRules: [
      v => !!v || "กรุณากรอกราคา",
      v => (v && v.length <= 10) || "ต้องมีความยาวไม่เกิน 10 หลัก"
    ],
    no_p: "",
    no_pRules: [
      v => !!v || "กรุณากรอกรหัสสินค้า",
      v => (v && v.length <= 10) || "ต้องมีความยาวไม่เกิน 10 หลัก"
    ],
    checkboxRules: [v => !!v || "คุณต้องตรวจสอบสินค้าก่อน"],
    select: null,
    items: ["Item 1", "Item 2", "Item 3", "Item 4"],
    sex: ["ชาย", "หญิง"],
    checkbox: false,
 
    search: "",
    headers: [ 
      {text:"รหัสสินค้า",value:"no_p"},
      {
        text: "ชื่อสินค้า",
        value: "name_p"},
      { text: "จำนวนสินค้า", value: "n" },
       { text: "สีสินค้า", value: "color" },
        { text: "น้ำหนักสินค้า", value: "weight" },
        { text: "ประเภทสินค้า", value: "Product" },
      { text: "ราคาสินค้า", value: "coin" },
    ],
    desserts: []
  }),
  methods: {
    validate() {
      if (this.$refs.form.validate()) {
        //   console.log(this.name);
        //   console.log(this.lastname);
        //   console.log(this.email);
        //   console.log(this.tel);
        //   console.log(this.select);
        //   console.log(this.a_number);
        //   console.log(this.a_group);
        //   console.log(this.a_lane);
        //   console.log(this.a_road);
        //   console.log(this.a_subdis);
        //   console.log(this.a_dis);
        //   console.log(this.a_province);
        this.desserts.push({
            name_p:`${this.name_p}`,
            color:`${this.color}`,
           weight:`${this.weight}`,
           Product:`${this.weight}`,
            no_p:`${this.no_p}`,
            n:`${this.n}`,
            coin:`${this.coin}`,
            email:`${this.email}`,
            sex:`${this.select}`,
            address:`${this.a_number}ม.${this.a_group}ถ.${this.a_road}ซ.${this.a_lane}ต.${this.a_subdis}อ.${this.a_dis}จ.${this.a_province}`,
        });
      }
    },
    reset() {
      this.$refs.form.reset();
    },
    resetValidation() {
      this.$refs.form.resetValidation();
    }
  }
};
</script>

<style></style>