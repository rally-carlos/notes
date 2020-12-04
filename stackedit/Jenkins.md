Cloudbees Cloud
* https://ci.rally-dev.com/
* https://ci-staging.werally.in/

# Decrypt Jenkins Secret

## Get Key
```
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
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTU2MzUzMjQ4NV19
-->