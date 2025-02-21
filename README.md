# **product-map-action**
**ProductMap Action** is a GitHub Actions extension designed to automate file processing and analysis using 
[ProductMap](https://product-map.ai). This action seamlessly integrates into your GitHub workflow to analyze a specified set of files and 
generate corresponding **analysis result URLs**.

Once processed, these URLs are automatically appended to the end of the **README.md** file, ensuring that results 
are accessible directly from the repository.

## **How It Works**
1. Detects changes in specified files within the public repository.
2. Processes the modified files using **ProductMap**.
3. Generates **public URLs** for the analysis results.
4. Appends the generated URLs to the **README.md** file.
5. Creates a new branch with the updated **README.md** and submits a **pull request** to merge the changes.

The following inputs must be provided for the action to function correctly within a GitHub workflow:

Input	Description
github_token	Required. The GitHub token to access the repository.
expected_files	Required. A list of file paths that the action should monitor and process when modified.
user_email	Optional. The email address associated with your ProductMap account, used to link the files to your profile.

## **Pre-requisites**

Before using this action, ensure that your **GitHub Actions permissions** are properly configured.

### **1. Enable File Read & Write Permissions**
This action needs permission to **read and write files** in your repository when running the workflow. To enable this:

1. Navigate to your **GitHub repository**.
2. Go to **Settings** → **Actions** → **General**.
3. Scroll down to **Workflow permissions**.
4. Select **Read and write permissions**.

### **2. Allow GitHub Actions to Create Pull Requests**
This action automatically creates a **new branch** with the updated `README.md` file and opens a **pull request**. To allow this:

1. Ensure that **GitHub Actions can create pull requests** by granting it access.
2. Add the following permissions to your workflow file:

```yaml
permissions:
  contents: write
  pull-requests: write
```

## **Inputs**

The following inputs must be provided for the action to function correctly within a GitHub workflow:

| Input           | Required | Description |
|----------------|----------|-------------|
| `github_token`  | ✅ Yes  | The GitHub token to access the repository. |
| `expected_files` | ✅ Yes  | A list of file paths that the action should monitor and process when modified. |
| `user_email`    | ✅ Yes | The email address associated with your **ProductMap** account, used to link the files to your profile. |
| `target_branch`    | ✅ Yes | The target branch to send the pull request. |


Below is an example of how to use the action in your workflow file:
```yaml
...
steps:
  - name: ProductMap Map Generation
    # uses: product-map/product-map-action@main
    uses: product-map/product-map-action@<latest-version>
    with:
      github_token: ${{ secrets.GITHUB_TOKEN }}
      expected_files: ("<your-file-path>", "<another/file-path>")
      user_email: <your@email.com>
      target_branch: <target_branch_name>
...
```

## **Outputs**

Upon execution, the action generates the following outputs:

| Output         | Description |
|---------------|-------------|
| **Public URLs** | A list of **ProductMap** public URLs for the processed files. These URLs allow you to access the analysis results. |

## **Where Are These Outputs Stored?**
- The public URLs are appended to the end of the repository's README.md file.
- The action automatically creates a new branch with the updated README.md.
- A pull request is opened to merge the changes into the main branch.

## **Why Use ProductMap Action?**
| ✅ Benefit | 🌟 Description |
|------------|--------------|
| 🚀 **Automates File Analysis** | No need to manually process files; everything runs within your workflow. |
| 📈 **Tracks Changes Efficiently** | Only modified files are analyzed, optimizing performance. |
| 🌍 **Enhances Collaboration** | Analysis results are publicly available via URLs, making it easy to share insights. |
| 🔄 **Seamless GitHub Integration** | Works natively within GitHub Actions with minimal setup. |


## **Need Help?**
If you encounter any issues or have feature requests, feel free to open an issue in the discord channel!

🔗 Discord channel: [ProductMap Discord](https://discord.gg/zr8wgaaMEK)

