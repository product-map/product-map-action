# product-map-action
Github action for managing and processing files via ProductMap CLI

## Inputs
The following inputs are required for the action to run.
Inside your workflow file, you can specify the following inputs:

In the push / path section, you can specify the path to the file(s) 
you want to process whenever a push event occurs that matches the 
specified path.


```yaml
...
on:
  push:
    paths:
      - 'README.md'
      - 'app/main.cpp'
...
```

Furthermore, in the first step of your workflow, you have to specify 
in the `EXPECTED_FILES` input the path to the file(s) that you expect 
to be processed by the action. This is necessary for the action to 
know which files to process.

```yaml
  - name: Add expected files path
    run: |
      EXPECTED_FILES=("<file-path>")  # Update this list with the desired file paths
      echo "EXPECTED_FILES=${EXPECTED_FILES}" >> $GITHUB_ENV
      echo "File paths to be analyzed: ${EXPECTED_FILES}"
```

Finally, in the last step of your workflow, specify the email address to link the files to your ProductMap account.
This parameter has to be added as secret in your repository settings with the name `PM_USER_EMAIL`.

## Outputs

The action will output the following:

- file URLs: The ProductMap URLs of the files that were processed by the action.
- public URLs: The ProductMap public URLs of the files that were processed by the action.

These outputs are attached at the end of the README.md file once the action is executed. 
The action will also create a new branch with the updated README.md file and open a 
pull request to merge the changes into the main branch.
