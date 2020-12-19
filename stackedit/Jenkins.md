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
Alert the current Rally-Ops Incident Commander ([https://audaxhealth.pagerduty.com/schedules#P4TWQ2T](https://audaxhealth.pagerduty.com/schedules#P4TWQ2T "Follow link")) that a drill is happening and any relevant alerts can be ignored.–

1. Wake up firedrill [Jenkins Master](https://ci.rally-dev.com/cjoc/job/Teams/job/fire-drill/)
2. Run build for firedrill
   * [Disk full](https://ci.rally-dev.com/teams-fire-drill/job/fire-drill/job/fill_disk/)
   * [Max out inodes] NEED LINK

## Datadog / Runbooks
* [Disk full](https://app.datadoghq.com/notebook/126080/)
* [Max out inodes](https://app.datadoghq.com/notebook/126235/)
```
AWS_PROFILE=rally-dev aws --region us-east-1 eks update-kubeconfig --name eks-cje-k8s --role-arn arn:aws:iam::144137586169:role/k8s-ops-access

# Find fire drill controller to monitor restore
kubectl get pods --namespace cje | grep -FiI fire

# Exec into controller
kubectl exec -it $(kubectl get pods --namespace cje | grep -FiI fire | cut -f1 -d' ') --namespace=cje -- /bin/bash

# See size of builds for "Fill Disk"
du -hd0 /var/jenkins_home/jobs/fire-drill/jobs/fill_disk/builds/* | sort -hr

rm -rf -- /var/jenkins_home/jobs/fire-drill/jobs/fill_disk/builds/
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTQ1MTM5MDU3MSwxNDc4MDk2NjI2LDEwMT
kwOTA3NzQsLTIwMzI5OTQzMTQsLTE3NjM2NDI1MTEsMTMwNTIy
MTgxMSwxMjg0NzA2ODYzLC03MzA1MjE5MjYsMTAwODA0OTMwOC
w0MTAyMzU3NDMsNDA1NjM4MzI2LDIxNDI0NTE2MDksMTkzODM2
MDc4MiwxODkxMjE0NjQ5LC0xNjYyMDg4NzcyLC0xNDU4OTA2Mj
g1XX0=
-->