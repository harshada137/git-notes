## Level 1: Basic Git Practical Questions

1. **Initialize a Git repository in a new project folder**  
   **Commands to use:**  
   ```
   git init
   git status


2. **Create a file `hello.txt`, add some content, and commit it**
   **Commands:**

   ```bash
   git add hello.txt
   git commit -m "Initial commit"
   ```

3. **Check the commit history in a simple repository**
   **Commands:**

   ```bash
   git log
   git log --oneline
   ```

4. **Rename the branch `master` to `main`**
   **Commands:**

   ```bash
   git branch -m master main
   ```

5. **Configure your Git username and email globally**
   **Commands:**

   ```bash
   git config --global user.name "Your Name"
   git config --global user.email "you@example.com"
   ```

6. **Check the difference between staged and unstaged changes**
   **Commands:**

   ```bash
   git status
   git diff
   git diff --staged
   ```

7. **Remove a file from tracking but keep it locally**
   **Command:**

   ```bash
   git rm --cached filename.txt
   ```


