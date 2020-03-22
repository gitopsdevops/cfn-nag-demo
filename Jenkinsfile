pipeline {
   agent any

   stages {
      stage('Hello') {
         steps {
            echo 'Hello World'
            cd /root/cfn_nag_examples/cfn
            docker run --tty --interactive --rm --name cfn-nag --volume $(pwd):/work  christiangda/cfn-nag --input-path volume.yml
         }
      }
   }
}
