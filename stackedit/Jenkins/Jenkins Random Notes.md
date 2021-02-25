# Jenkins Infra
* [Live/Prod](https://ci.rally-dev.com/cjoc/)
* [Staging](https://ci-staging.werally.in/cjoc/)
* [Legacy Prod](https://jenkins.werally.in/)
* [Legacy Non-Prod](https://rally-jenkins.werally.in/) [Deprecated]

Repos:
* [jenkins-infra](https://github.com/AudaxHealthInc/jenkins-infra/)
* [cje-k8s-configs](https://github.com/AudaxHealthInc/cje-k8s-configs) - Kubernetes configuration for the Cloudbees Core Jenkins cluster
* [Configuration as Code (CasC)](https://github.com/AudaxHealthInc/cje-jenkins-configs)

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

# Fire Drills

1. Wake up firedrill [Jenkins Master](https://ci.rally-dev.com/cjoc/job/Teams/job/fire-drill/)
	Can take several minutes, <10min.
2. Alert the current [Rally-Ops Incident Commander](https://audaxhealth.pagerduty.com/schedules#P4TWQ2T), in Slack channel #ops-internal, that a drill is happening and any relevant alerts can be ignored.
3. Run build for [Fire drill](https://ci.rally-dev.com/teams-fire-drill/job/fire-drill/)
   * [Fill disk](https://ci.rally-dev.com/teams-fire-drill/job/fire-drill/job/fill_disk/)
   * [Max out inodes](https://ci.rally-dev.com/teams-fire-drill/job/fire-drill/job/fill_inodes/)
4. Monitor via Datadog
   * [Disk full](https://app.datadoghq.com/notebook/126080/)
   * [Max out inodes](https://app.datadoghq.com/notebook/126235/)

## Fill Disk Runbook
```
# Alert incident commander!

# Set context
aws --profile rally-dev --region us-east-1 eks update-kubeconfig --name eks-cje-k8s --role-arn arn:aws:iam::144137586169:role/k8s-ops-access

# Find fire drill controller to monitor restore
kubectl get pods --namespace cje | grep -FiI fire

# TODO: Find API call
# Once controller is online, run build job https://ci.rally-dev.com/teams-fire-drill/job/fire-drill/job/fill_disk/

# Exec into controller
kubectl exec -it $(kubectl get pods --namespace cje | grep -FiI fire | cut -f1 -d' ') --namespace=cje -- /bin/bash

# See size of builds for "Fill Disk"
du -hd0 /var/jenkins_home/jobs/fire-drill/jobs/fill_disk/builds/* | sort -hr

# Monitor via Datadog, https://app.datadoghq.com/notebook/126080/

# Acknowledge PagerDuty alert

# Cleanup
rm -rf -- /var/jenkins_home/jobs/fire-drill/jobs/fill_disk/builds/
```

# Check if we do this
* https://support.cloudbees.com/hc/en-us/articles/215549798-Best-Strategy-for-Disk-Space-Management-Clean-Up-Old-Builds?page=4
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTMyMTQ5OTg3Ml19
-->