pipeline {
   agent any

   stages {
      stage('CFN-NAG Scan Example') {
         steps {
            sh '''
            #git clone https://github.com/stelligent/cfn_nag_examples
            cd cfn_nag_examples/cfn/
            pwd
            #sudo docker run --rm --name cfn-nag --volume $(pwd):/work  christiangda/cfn-nag --input-path volume.yml
            
            sudo docker run --rm --name cfn-nag --volume $(pwd):/work  christiangda/cfn-nag --input-path volume-encrypted.yml
            '''
         }
      }
   }
}
