# Working-with-Functions


# Mini Project – Working with Functions

In this mini project, I learned how to define and use functions in Bash scripting to improve code organization and reusability. I created and used multiple functions to handle different checks before running a script. The `check_args` function verified that one argument was passed, while `check_aws_cli` confirmed that the AWS CLI was installed on my system. I also wrote a `check_env_vars` function to ensure the required AWS environment variables (`AWS_ACCESS_KEY_ID` and `AWS_SECRET_ACCESS_KEY`) were set. Additionally, I created a `set_profile` function to set the AWS profile based on user input. Below is the script I wrote and tested:

```
#!/bin/bash

check_args() {
  if [ "$#" -ne 1 ]; then
    echo "Usage: $0 <environment>"
    exit 1
  fi
}

check_aws_cli() {
  if ! command -v aws &> /dev/null; then
    echo "AWS CLI not installed."
    exit 1
  fi
}

check_env_vars() {
  if [[ -z "$AWS_ACCESS_KEY_ID" || -z "$AWS_SECRET_ACCESS_KEY" ]]; then
    echo "AWS environment variables not set"
    exit 1
  fi
}

set_profile() {
  export AWS_PROFILE=$1
}

# Main script
check_args "$@"
ENV=$1
check_aws_cli
check_env_vars
echo "All checks passed. Ready to proceed with environment: $ENV"
```

I ran the script using `./mini_project.sh dev`, tested each function, and learned how to use conditionals, environmental variables, and commands like `command -v` to verify setups programmatically within scripts.
