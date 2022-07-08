## BuildSpec and Jenkins examples inscuding simple Post-Build Trivy or Grype Container Image Scan stages
See below:

## Install Trivy, download HTML template, and Scan Image and output results to file
- ArtifactPath=$(pwd)
- curl -sfL https://raw.githubusercontent.com/aquasecurity/trivy/main/contrib/install.sh | sh -s -- -b /usr/local/bin

- cd $ArtifactPath
- wget https://raw.githubusercontent.com/aquasecurity/trivy/main/contrib/html.tpl 
- trivy i -f template --template "@html.tpl" -o {scan-results} --exit-code 0 --severity HIGH,MEDIUM,LOW,CRITICAL $REPOSITORY_URI/repository:tag

## Install Grype, Scan Image, and output results to file
 - ArtifactPath=$(pwd)
 - wget https://github.com/anchore/grype/releases/download/v0.40.1/grype_0.40.1_linux_amd64.deb
 - sudo dpkg -i grype_0.40.1_linux_amd64.deb
 
 - cd $ArtifactPath
 - grype $REPOSITORY_URI/repository:tag | tee {scan-results}
 
 
## Build spec Artifact pull from $CODEBUILD_SRC_DIR
ArtifactPath=$(pwd)
cd $ArtifactPath
