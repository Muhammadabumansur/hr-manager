<template>
  <div id="app" class="container">
    {{pagesQuantity}}
    <ApplicantsFilterPanel
      :countries="countries"
      :skillsObject="skillsObject">
    </ApplicantsFilterPanel>
    <ApplicantsList
      :applicants="slicedApplicants"
      :cols="applicants.cols">
    </ApplicantsList>
    <ApplicantsPagination
      :showNumber="showNumber"
      :pagesQuantity="pagesQuantity"
      @changeNumber="changeShowNumber"
      @changePage="setInitialIndex">
    </ApplicantsPagination>
  </div>
</template>

<script>
import ApplicantsList from './components/ApplicantsList';
import ApplicantsFilterPanel from './components/ApplicantsFilterPanel';
import ApplicantsPagination from './components/ApplicantsPagination';
import applicants from './data/applicants.json';

export default {
  name: 'App',
  components: { ApplicantsList, ApplicantsFilterPanel, ApplicantsPagination },
  data: function() {
    return {
      applicants,
      skillsObject: {
        "Vue": true,
        "React": true,
        "Angular": true
      },
      showNumber: 10,
      countries: [],
      initialIndex: 0
    };
  },
  created: function() {
    this.makeCountries()
  },
  methods: {
    setInitialIndex(num) {
      this.initialIndex = num * this.showNumber;
    },
    changeShowNumber(num) {
      this.showNumber = num;
    },
    makeCountries() {
      var applicants = this.applicants.data;
      for (let i = 0; i < applicants.length; i++) {
        let country = applicants[i][4];
        if (this.countries.indexOf(country) === -1) {
          this.countries.push(country);
        }
      }
    }
  },
  computed: {
    filteredApplicants() {
      return applicants.data
    },
    slicedApplicants() {
      return this.filteredApplicants.slice(this.initialIndex, this.initialIndex + this.showNumber)
    },
    pagesQuantity() {
      return Math.ceil(this.filteredApplicants.length / this.showNumber)
    }
  }
};
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
