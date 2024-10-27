## Sample applications

### Getting started

1. Clone the repository
2. cd flask-rds-app/scripts 
3. Run `brew tap pranil-augur/homebrew-mantis`
4. Run `brew install mantis`
5. Init `mantis run --init <script_name>.tf.cue`
6. Run plan `mantis run --plan <script_name>.tf.cue`
7. Run apply `mantis run --apply <script_name>.tf.cue`
8. Run destroy `mantis run --destroy <script_name>.tf.cue`

### Sample applications

1. simple-s3 - sets up an s3 bucket on aws
2. flask-dynamodb-app - sets up a cloud-native, flask app to run on kubernetes backed by dynamodb
3. flask-rds-app - sets up a cloud-native, flask app to run on kubernetes backed by RDS thats installed in an AWS VPC 


### Using codegen


> [!WARNING]
> The code generation feature is still in its infancy and under active development. The code generated through this feature is not production-ready and should be used with caution. We are continuously working to improve the accuracy and reliability of the generated code. Always review, test, and validate any generated code before using it in a production environment.

```cue
default_backend: "openai"
backends: {
    openai: {
        type:          "openai"
        api_key:       "<OPENAI_API_KEY>"
        default_model: "gpt-4o"
        url:           "https://api.openai.com/v1"
    }
}
```

This is the configuration for the code generation feature of Mantis, stored in ~/.mantis/config.cue. It sets up the OpenAI backend for code generation:

- type: Set to "openai", indicating the use of OpenAI's API.
- api_key: This should be replaced with your actual OpenAI API key.
- default_model: Set to "gpt-4o", which appears to be a custom identifier for a GPT-4 model.
- url: The base URL for the OpenAI API.

To use this configuration:
- Replace <OPENAI_API_KEY> with your actual OpenAI API key.
- Ensure this file is located at ~/.mantis/config.cue.

```
mantis codegen --system-prompt prompts/terraform_prompt.md --code-dir databricks --prompt "create databricks job to deploy my notebook"
```
 
```
mantis codegen --system-prompt prompts/terraform_prompt.md --code-dir pagerduty --prompt "generate configurations to create pager duty schedules for my platform team"
```

```
mantis codegen --system-prompt prompts/kubernetes_prompt.md --code-dir flask_app  --prompt "generate configurations to deploy my flask app in AWS"
```
