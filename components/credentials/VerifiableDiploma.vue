<template>
  <div class="p-4">
    <div class="col-12 py-3">
                            <span>
                                <h5>{{$t('CREDENTIAL.TITLE')}}</h5>
                                <p>{{$t('CREDENTIAL.TYPE.' + credential.type[credential.type.length-1])}}</p>
                            </span>
    </div>
    <div class="d-flex py-3">
                            <span class="col-4">
                                <h5>{{$t('CREDENTIAL.ISSUER')}}</h5>
                                <p class="text-truncate" style="max-width: 12em">{{credential.issuerName ? credential.issuerName : credential.issuer}}</p>
                            </span>
      <span class="col-4">
                            </span>
      <span class="col-4">
                                <h5>{{$t('CREDENTIAL.STATUS')}}</h5>
                                <p>Valid</p>
                            </span>
    </div>
    <div class="d-flex py-3 border-bottom mb-3 border-secondary">
                            <span class="col-4">
                                <h5>{{$t('CREDENTIAL.ISSUED_ON')}}</h5>
                                <p>{{moment(credential.issuanceDate).format("MMM Do YYYY")}}</p>
                            </span>
      <span class="col-4">
                                <h5>{{$t('CREDENTIAL.EXPIRE')}}</h5>
                                <p>{{credential.expirationDate ? moment(credential.expirationDate).format("MMM Do YYYY") : "Never"}}</p>
                            </span>
      <span class="col-4">
                                <h5>{{$t('CREDENTIAL.VALID_FROM')}}</h5>
                                <p>{{moment(credential.validFrom).format("MMM Do YYYY")}}</p>
                            </span>
    </div>
    <div class="col-12 py-3">
      <div class="_image" style="background-image: url('https://www.urbanpedaltours.com/wp-content/uploads/2019/04/team.png');"></div>
    </div>
    <div class="text-left">
                            <span class="col-12 pb-3">
                                <h5>{{$t('CREDENTIAL.FIRST_NAME')}}</h5>
                                <p>{{credential.credentialSubject.givenNames}}</p>
                            </span>
      <span class="col-12 px-3">
                                <h5>{{$t('CREDENTIAL.LAST_NAME')}}</h5>
                                <p>{{credential.credentialSubject.familyName}}</p>
                            </span>
      <span class="col-12 px-3">
                                <h5>{{$t('CREDENTIAL.DATE_OF_BIRTH')}}</h5>
                                <p>{{credential.credentialSubject.dateOfBirth}}</p>
                            </span>
      <!-- TODO: add more properties for VerifiableDiploma -->
      <span class="col-12 px-3">
                                <h5>{{$t('CREDENTIAL.DID')}}</h5>
                                <p>{{credential.credentialSubject.id}}</p>
                            </span>

      <br><br>
      <span class="col-12 px-10">
                                <h7>Grading info:</h7>
                                
                            </span>
      
      <span class="col-12 px-3">
                                <h5>Title</h5>
                                <p>{{credential.credentialSubject.gradingScheme.title}}</p>
                            </span>
      <span class="col-12 px-3">
                                <h5>Grade</h5>
                                <p>{{credential.credentialSubject.gradingScheme.description}}</p>
                            </span>

      <span class="col-12 px-10">
                                <h7>Learning achievement:</h7>
                                
                            </span>
      <span class="col-12 px-3">
                                <h5>Title</h5>
                                <p>{{credential.credentialSubject.learningAchievement.title}}</p>
                            </span>
      <span class="col-12 px-3">
                                <h5>Description</h5>
                                <p>{{credential.credentialSubject.learningAchievement.description}}</p>
                            </span>
      <span class="col-12 px-3">
                                <h5>Additional Notes</h5>
                                
                                  <p v-for="note in credential.credentialSubject.learningAchievement.additionalNote" v-bind:key="note">{{note}}</p> 
                                  
                                
                            </span>
      <span class="col-14 px-10">
                                <h7>Awarding opportunity info:</h7>
                                
                            </span>
      <span class="col-12 px-3">
                                <h5>Form code</h5>
                                
                                  <p>{{credential.credentialSubject.awardingOpportunity.id}}</p>
                                  
                                
                            </span>
      <span class="col-12 px-3">
                                <h5>Title</h5>
                                
                                  <p>{{credential.credentialSubject.awardingOpportunity.identifier}}</p>
                                  
                                
                            </span>
      <span class="col-12 px-3">
                                <h5>Issuer code</h5>
                                
                                  <p>{{credential.credentialSubject.awardingOpportunity.awardingBody.registration}}</p>
                                  
                                
                            </span>
      <span class="col-12 px-3">
                                <h5>Issued companies manager</h5>
                                
                                  <p>{{credential.credentialSubject.awardingOpportunity.awardingBody.preferredName}}</p>
                                  
                                
                            </span>                                                                  
                                                 
    </div>
  </div>
</template>

<script>
import moment from "moment";

export default {
  name: "VerifiableDiploma",
  props: {
    credential: {}
  },
  data() {
    return {
      moment: moment
    }
  },
  computed: {
    additionalNotes () {
      console.log("locales", this.$i18n.locales)
      return this.$i18n.locales.filter(i => i.code !== this.$i18n.locale)
    }

  }
}
</script>

<style scoped>

</style>
