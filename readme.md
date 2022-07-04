wget https://raw.githubusercontent.com/SetonJay/trivy_report/main/trivy_html.tpl

trivy i -f template --template "@html.tpl" -o {OUTPUT_FILE_NAME} --exit-code 0 --severity HIGH,MEDIUM,LOW,CRITICAL {IMAGE}
