node {
   
    stage('Preparation') { 
       
        git 'https://github.com/Jaibw/FrozenYogurtShop.git'
       
    }
    
    stage('Apply Changes') {
        sh("sed -i 's/username/${env.JOB_BASE_NAME}/g' k8s-deploy.yaml")
    }
   
    stage('Deployment') {
        sh("kubectl --kubeconfig ~/auth/k8s-devconfig apply -f k8s-deploy.yaml")
        sh("kubectl --kubeconfig ~/auth/k8s-devconfig get pods | grep ${env.JOB_BASE_NAME}")
        sh("kubectl --kubeconfig ~/auth/k8s-devconfig get svc | grep ${env.JOB_BASE_NAME}")
    }
    
}
