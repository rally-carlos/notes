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

1. wake up firedrill jenkins master
2. Run build for firedrill
   * https://ci.rally-dev.com/teams-fire-drill/job/fire-drill/job/fill_disk/

## Runbooks
* https://app.datadoghq.com/notebook/126235/-runbook-jenkins-masters-home-directory-inode-monitor
* 
```
AWS_PROFILE=rally-dev aws eks update-kubeconfig --region us-east-1 --name eks-cje-k8s --role-arn arn:aws:iam::144137586169:role/k8s-ops-access
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTAwODA0OTMwOCw0MTAyMzU3NDMsNDA1Nj
M4MzI2LDIxNDI0NTE2MDksMTkzODM2MDc4MiwxODkxMjE0NjQ5
LC0xNjYyMDg4NzcyLC0xNDU4OTA2Mjg1XX0=
-->