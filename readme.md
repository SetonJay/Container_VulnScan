wget https://github.com/SetonJay/trivy/blob/main/contrib/html.tpl
trivy i -f template --template "@html.tpl" -o {OUTPUT_FILE_NAME} --exit-code 0 --severity HIGH,MEDIUM,LOW,CRITICAL {IMAGE}
