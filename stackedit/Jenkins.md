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

## Firedrill

```
AWS_PROFILE=rally-dev aws eks update-kubeconfig --region us-east-1 --name eks-cje-k8s --role-arn arn:aws:iam::144137586169:role/k8s-ops-access
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbMjE0MjQ1MTYwOSwxOTM4MzYwNzgyLDE4OT
EyMTQ2NDksLTE2NjIwODg3NzIsLTE0NTg5MDYyODVdfQ==
-->