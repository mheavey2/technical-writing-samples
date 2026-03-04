## Summary

When working with open-source projects on GitHub, it is common practice to **fork**, or create a copy of, the original repository. This allows you to make changes without affecting the original repository. However, you need to make sure that your fork is up-to-date with the original repository to avoid any conflicts when you want to merge your changes back into the original repository. Below are the best practices to keep your fork synchronised with the original repository using Git on the command line.

## Prerequisites

- A GitHub account
- A forked repository cloned to your computer
- Command line

## Steps

1. On the command line, verify that you are in your project repository.

   `pwd`

2. Check your current remote repository configuration

   `git remote -v`

   To synchronise your fork with the original repository you must configure the original as an upstream repository of your fork. If you do not have an upstream configured, the output from `git remote -v` will be:

   ```
   origin <fork-repo-url> (fetch)
   origin <fork-repo-url> (push)
   ```

   `origin` is the name given to the remote repository from which your local repository was cloned.

   `fork-repo-url` is the URL of your forked repository.

3. In your web browser, open the original repository on GitHub, click on the green **Code** button and copy the repository URL from the HTTPS tab.

![GitHub docs repository with Code button and repository URL visible](../technical-writing-samples/assets/images/github-docs-clone-url.png "Example using the GitHub docs repository")

4. On the command line, add the remote upstream repository

   `git remote add upstream https://github.com/original-repo-owner/original-repo.git`

5. Verify the new `upstream` has been added

   `git remote -v`

   The output will now be:

   ```
   origin <fork-repo-url> (fetch)
   origin <fork-repo-url> (push)
   upstream <original-repo-url> (fetch)
   upstream <original-repo-url> (push)
   ```

6. Fetch the latest changes from the remote upstream repository

   `git fetch upstream`

7. Checkout the main branch.

   `git checkout main`

8. Rebase the changes

   `git rebase upstream/main`

9. Push the updated branch to your repository fork

   `git push origin main`

## Conclusion

Your forked repository is now up-to-date with the original repository.
