<template>
  <v-table>
    <thead>
    <tr>
      <th class="text-left">
        Patient Email
      </th>
      <th class="text-left">
       Prescription Name
      </th>
      <th class="text-left">
        Prescription Dose
      </th>
    </tr>
    </thead>
    <tbody>
    <tr
      v-for="prescription in prescriptions"
      :key="prescription._id"
    >
      <td>{{ prescription.patientEmail }}</td>
      <td>{{ prescription.Medicine }}</td>
      <td>{{ prescription.Dosage }}</td>
<!--     -->
    </tr>
    </tbody>
  </v-table>
</template>

<script>
import AddPrescriptions from "@/views/AddPrescriptions.vue";
import axios from "axios";

export default {
  name: "patientPrescriptions",
  data() {
    return {
      prescriptions: []
    }
  },
  computed: {
    AddPrescriptions() {
      return AddPrescriptions
    }
  },
  mounted() {
    const patientEmail = localStorage.getItem("email")
    axios.get('http://localhost:4000/prescription/get?email=' + "", {

    })
      .then( async (response) => {
        console.log(response.data);
        this.prescriptions = await response.data
      })
  }
}
</script>

<style scoped>

</style>
