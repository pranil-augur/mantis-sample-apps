## Sample applications

### Getting started

1. Clone the repository
2. Run `brew tap pranil-augur/homebrew-mantis`
3. Run `brew install mantis`
4. Init `mantis run --init <script_name>.tf.cue`
5. Run plan `mantis run --plan <script_name>.tf.cue`
6. Run apply `mantis run --apply <script_name>.tf.cue`
7. Run destroy `mantis run --destroy <script_name>.tf.cue`

### Sample applications

1. simple-s3 - sets up an s3 bucket on aws
2. flask-dynamodb-app - sets up a cloud-native, flask app to run on kubernetes backed by dynamodb


### Codegen usage

mantis codegen --system-prompt prompts/terraform_prompt.md --code-dir databricks --prompt "create databricks job to deploy my notebook"

mantis codegen --system-prompt prompts/terraform_prompt.md --code-dir pagerduty --prompt "generate configurations to create pager duty schedules for my platform team"

mantis codegen --system-prompt prompts/kubernetes_prompt.md --code-dir flask_app  --prompt "generate configurations to deploy my flask app in AWS"
