Cloudbees Cloud
* https://ci.rally-dev.com/ - live
* https://ci-staging.werally.in/

# Retrieve Secrets from Jenkins

## Get Decryption Key
```groovy
import com.cloudbees.plugins.credentials.*;  
    import com.cloudbees.plugins.credentials.domains.Domain;  
    import org.jenkinsci.plugins.plaincredentials.impl.FileCredentialsImpl;    println "Jenkins credentials config file location=" + SystemCredentialsProvider.getConfigFile();  
    println ""	println "cat /var/jenkins_home/credentials.xml".execute().text    // only works with files, no un/pw  
    SystemCredentialsProvider.getInstance().getCredentials().stream().  
    filter { cred -> cred instanceof FileCredentialsImpl }.  
    map { fileCred -> (FileCredentialsImpl) fileCred }.  
    forEach { fileCred ->   
        String s = new String( fileCred.getSecretBytes().getPlainData() )  
        println "XXXXXX BEGIN a secret file with fileName=" + fileCred.getFileName() + " XXXXXXXXXXXX"  
        println s  
        println "XXXXXX END a secret file with fileName=" + fileCred.getFileName() + " XXXXXXXXXXXX"  
        println ""  
    }
```

## Decrypt Secret

Source:
* https://devops.stackexchange.com/a/2192
* https://gist.github.com/tuxfight3r/eca9442ff76649b057ab

```groovy
println(hudson.util.Secret.fromString("{XXX=}")
```

# Firedrills

!!!!
Alert the current Rally-Ops Incident Commander ([https://audaxhealth.pagerduty.com/schedules#P4TWQ2T](https://audaxhealth.pagerduty.com/schedules#P4TWQ2T "Follow link")) that a drill is happening and any relevant alerts can be ignored.

Datadog / Runbooks
* https://app.datadoghq.com/notebook/126080/-runbook-jenkins-masters-home-directory-disk-monitor

1. Wake up firedrill [Jenkins Master](https://ci.rally-dev.com/cjoc/job/Teams/job/fire-drill/)
2. Run build for firedrill
   * https://ci.rally-dev.com/teams-fire-drill/job/fire-drill/job/fill_disk/

## Runbooks
* https://app.datadoghq.com/notebook/126235/-runbook-jenkins-masters-home-directory-inode-monitor
* 
```
AWS_PROFILE=rally-dev aws eks update-kubeconfig --region us-east-1 --name eks-cje-k8s --role-arn arn:aws:iam::144137586169:role/k8s-ops-access

# Find fire drill controller
kubectl get pods --namespace cje | grep -FiI fire
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbMzU2NDY5NjA2LDEyODQ3MDY4NjMsLTczMD
UyMTkyNiwxMDA4MDQ5MzA4LDQxMDIzNTc0Myw0MDU2MzgzMjYs
MjE0MjQ1MTYwOSwxOTM4MzYwNzgyLDE4OTEyMTQ2NDksLTE2Nj
IwODg3NzIsLTE0NTg5MDYyODVdfQ==
-->