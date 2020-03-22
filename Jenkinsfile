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
      stage('Describe EC2 Instances') {
         steps {
            sh '''

            aws ec2 describe-instances --query 'Reservations[*].Instances[*].[Placement.AvailabilityZone, State.Name, InstanceId]' --output text

            '''
         }
      }
      stage('Create an EC2 Instance') {
         steps {
            sh '''
            aws ec2 run-instances --image-id ami-08bc77a2c7eb2b1da --count 1 --instance-type t2.micro --key-name gitopsdevops-key --security-group-ids sg-023eabb9bf1834f38 --subnet-id subnet-40c42f1f
            sleep 30s
            aws ec2 describe-instances --query 'Reservations[*].Instances[*].[Placement.AvailabilityZone, State.Name, InstanceId]' --output text
            '''
         }
      }
   }
}
