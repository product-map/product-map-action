# product-map-action
Extension for managing and processing files via ProductMap. 
The extension is designed to be used in GitHub workflows.
The extension works by processing a collection of files that are expected to be analyzed via ProductMap and
generating a link which contains the analysis result for each file. 
The generated URLs are then attached to the end of the README.md file.

## Inputs
The following inputs are required for the action to run.
Inside your workflow file, you can specify the following inputs:

- `github_token`: The GitHub token to access the repository.
- `expected_files`: The list of files that you expect to analyze to be processed by the action. 
    This is necessary for the action to know which files to process when a modification on those files is detected.
- `user_email`: The email address to link the files to your ProductMap account.

Below is an example of how to use the action in your workflow file:
```yaml
...
steps:
  - name: ProductMap Map Generation
    # You may pin to the exact commit or the version.
    # uses: JuanQuGo/product-map-action@e11422d93a9f689161850adb3efb220a04b12026
    uses: JuanQuGo/product-map-action@v1.0.10
    with:
      github_token: ${{ secrets.GITHUB_TOKEN }}
      expected_files: ("<your-file-path>", "<another/file-path>")
      user_email: <your@email.com>
...
```

## Outputs

The action will output the following:

- public URLs: The ProductMap public URLs of the files that were processed by the action.

These outputs are attached at the end of the README.md file once the action is executed. 
The action will also create a new branch with the updated README.md file and open a 
pull request to merge the changes into the main branch.
