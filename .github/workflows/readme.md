#### github actions
- **Runners:**
  - A “runner” = the computer that actually executes your CI/CD steps. 
  - GitHub creates a temporary machine (Linux, Windows, or Mac) where your pipeline commands run.
  - A runner is basically is A machine (VM or physical) that executes your GitHub Actions workflow steps.
  - Github provides multiple sources for runners:
    - **GitHub-Hosted Runners:**
      - These are machines provided by GitHub.(ubuntu-latest, windows-latest, macos-latest)
      - These are: Fresh VMs created per job, Auto-configured, Auto-destroyed & Free (within limits)
    - **Self-Hosted Runners:**
      - These are machines you provide.
      - Example: Your laptop, An EC2 instance, A Linux server & A company VM
- In GitHub Actions, the `name:` field in the steps is always optional. FOr example, check the uses.yaml file and there we used checkout action without name
- **uses:**
  - The `uses` keyword is typically found within a step inside a job in the workflow YAML.
  - It lets you call an action either by referencing its repository (e.g., `actions/checkout@v4`) or a Docker image.
  - Actions referenced with uses can come from the same repository, any public repository(actions/checkout@v4), or Docker images.
  - This helps you leverage community-maintained or custom actions for tasks such as setting up environments, checking out code, uploading artifacts, or deploying applications without writing repetitive scripts

- **Authentication to aws:**
  - Store AWS_ACCESS_KEY_ID and AWS_SECRET_ACCESS_KEY in your GitHub repository secrets.
  - To use them in the pipeline we need to declare as
    - ```
      with:
        aws-region: us-east-2
        aws-access-key-id: ${{ steps.creds.outputs.aws-access-key-id }}
        aws-secret-access-key: ${{ steps.creds.outputs.aws-secret-access-key }}
      ```
