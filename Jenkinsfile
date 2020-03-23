pipeline {
   agent any

   stages {
      stage('CFN-NAG Scan Example') {
         steps {
            sh '''
            git clone https://github.com/stelligent/cfn_nag_examples
            cd cfn_nag_examples/cfn/
            pwd
            #sudo docker run --rm --name cfn-nag --volume $(pwd):/work  christiangda/cfn-nag --input-path volume.yml

            echo "========"
            echo "An example of unapproved volume creation"
            echo "========"

            cat volume.yml

            echo "========"
            echo "Here is an example of Approved volume creation"
            echo "========"


            cat volume-encrypted.yml

            sudo docker run --rm --name cfn-nag --volume $(pwd):/work  christiangda/cfn-nag --input-path volume-encrypted.yml

            '''
         }
      }

   }

    post {
        always {
            cleanWs()
        }

    }


}
