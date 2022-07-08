## BuildSpec and Jenkins examples with stages for Post-build container image scans, using open source container vulnerability scanners (Trivy / Grype) 
See below:

## Install Trivy, download HTML template, and Scan Image and output results to file
- ArtifactPath=$(pwd)
- curl -sfL https://raw.githubusercontent.com/aquasecurity/trivy/main/contrib/install.sh | sh -s -- -b /usr/local/bin


- cd $ArtifactPath
- wget https://raw.githubusercontent.com/aquasecurity/trivy/main/contrib/html.tpl 
- trivy i -f template --template "@html.tpl" -o {scan-results} --exit-code 0 --severity HIGH,MEDIUM,LOW,CRITICAL $REPOSITORY_URI/repository:tag

## Install Grype, Scan Image, and output results to file
 - ArtifactPath=$(pwd)
 - curl -sSfL https://raw.githubusercontent.com/anchore/grype/main/install.sh | sh -s -- -b /usr/local/bin
 
 - cd $ArtifactPath
 - grype $REPOSITORY_URI/repository:tag | tee {scan-results}
 
 
## Build spec Artifact pull from $CODEBUILD_SRC_DIR
ArtifactPath=$(pwd)
cd $ArtifactPath
