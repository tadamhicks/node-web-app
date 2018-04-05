import groovy.json.JsonOutput 
@Library('morpheusApp@1.1') _



node ('docker-slave') {

    def app

    stage('Clone repository') {
        /* Let's make sure we have the repository cloned to our workspace */

        checkout scm
    }




    stage('Provision Dev App') {
        /*
         *
         *  */

        withCredentials([string(credentialsId: 'morphauthdemo', variable: 'bearer')]) {
            String morpheusUrl = 'https://demo.morpheusdata.com/api/apps'

            Map<?, ?> postBody = ["name": "Tcook01","image": "/assets/apps/template.png"]

           MorpheusApp.buildApp(morpheusUrl, postBody, "${bearer}")
        }
    }


    }

