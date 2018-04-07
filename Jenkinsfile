import groovy.json.JsonOutput 

node {

    def app

    stage('Clone repository') {
        /* Let's make sure we have the repository cloned to our workspace */

        checkout scm
    }




    stage('Provision Dev App') {
        /*
         *
         *  */

           withCredentials([string(credentialsId: 'newtoken', variable: 'bearer')]) {
            String morpheusUrl = 'https://demo.morpheusdata.com/api/apps'

	    Map<?, ?> postBody = [ "image": "/assets/apps/template.png", "tiers": [ "App": [ "linkedTiers": [ "Cache", "Database" ], "tier": [ "bootOrder": 1, "lockedFields": [ "bootOrder" ] ], "instances": [ [ "instance": [ "type": "docker", "cloud": "Labs UCS", "layout": [ "code": "docker-1.7-single", "id": 206 ], "expireDays": "1", "name": "frontend-${env.BUILD_NUMBER}", "allowExisting": true ], "backup": [ "createBackup": true ], "evars": [ [ "name": "DB_NAME", "value": "demo_app" ], [ "name": "WORDNIK_API_KEY", "value": "5455816781cb799cf994f0b58cc027cb0dd2633addcdd2025" ], [ "name": "ENVIRONMENT", "value": "dev" ] ], "layoutSize": 3, "volumes": [ [ "size": 5, "name": "root", "rootVolume": true ] ], "ports": [ [ "port": "9090", "lb": "", "name": "web" ] ], "config": [ "configVolume": "", "dockerImage": "tadamhicks/demo_app", "dataVolume": "", "dockerImageVersion": "${env.BUILD_NUMBER}", "logVolume": "", "expose": 8080, "dockerRegistryId": "" ], "plan": [ "code": "container-512", "id": 70 ], "metadata": [ [ "name": "", "value": "" ] ] ] ] ], "Database": [ "linkedTiers": [], "instances": [ [ "instance": [ "type": "mysql", "cloud": "Labs UCS", "layout": [ "code": "mysql-5.7-single", "id": 87 ], "expireDays": "1", "name": "db-${env.BUILD_NUMBER}", "allowExisting": true ], "backup": [ "createBackup": true ], "volumes": [ [ "size": 5, "name": "root", "rootVolume": true ] ], "plan": [ "code": "container-512", "id": 70 ], "config": [ "password": "password", "rootPassword": "password", "username": "admin" ], "deployment": [ "versionId": 61, "id": 13 ], "metadata": [ [ "name": "", "value": "" ] ], "evars": [ [ "name": "", "value": "" ] ] ] ] ], "Cache": [ "linkedTiers": [], "instances": [ [ "instance": [ "type": "redis", "cloud": "Labs UCS", "layout": [ "code": "redis-3.2-single", "id": 666 ], "expireDays": "1", "name": "cache-${env.BUILD_NUMBER}", "allowExisting": true ], "backup": [ "createBackup": true ], "volumes": [ [ "size": 3, "name": "root", "rootVolume": true ] ], "plan": [ "code": "container-256", "id": 69 ], "config": [], "metadata": [ [ "name": "", "value": "" ] ], "evars": [ [ "name": "", "value": "" ] ] ] ] ] ], "name": "demo_app_${env.BUILD_NUMBER}", "id": 68, "templateName": "tcooktestADA", "group": [ "id": 2, "name": "All Clouds Demo" ], "environment": "Dev" ]
            echo morpheusApp.buildApp(morpheusUrl, postBody, "${bearer}")
        }
    }
  }

