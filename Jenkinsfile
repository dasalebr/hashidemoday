Pipeline {
      agent any
      environment {
           CHKP_CLOUDGUARD_ID = credentials("CHKP_CLOUDGUARD_ID")
           CHKP_CLOUDGUARD_SECRET = credentials("CHKP_CLOUDGUARD_SECRET")
        }
        
  stages {
          
         stage('Clone Github repository') {
            
    
           steps {
                 
              echo "checking the file"
              
             checkout scm
           
             }
  
          }
          
    stage('ShiftLeft Code Scan') {   
       steps {   
                   
         script {      
              try {

             
                
            
                sh 'chmod +x shiftleft' 

             
           
               } catch (Exception e) {
    
                 echo "Request for Approval"  
                  }
              }
            }
      
        
      stage('Terraform config policy Scan') {    
           
            steps {
         
                    sh './shiftleft iac-assessment -p terraform/ -r -64'
                    
              }
            }
  } 
}

}
