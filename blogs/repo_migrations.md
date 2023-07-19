# Outline (initial concepts)

- The end goal is to have each repo migrated to a core `shipwright` repo where each repo is located within a specific subfolder.
- Additionally, the commit history for each repo should be retained.
- The basic idea is
    - clone each repo locally.
    - clone or create the monorepo.
    - Manipulate the local repo history to move the files into the folder structure they should be in for the monorepo.
    - In the monorepo, add the source repos as remote, making sure to reference the local repo
    - call `git fetch` to retrieve the remote repo and verify the folder structure is correct.
    - `git merge` the remote repo into the monorepo. Use the `--allow-unrelated-histories` option to pull in the remote repo.
    - repeat for each additional repo

# Key Elements

- `git clone https://github.com/headwayio/shipwright`
- `git clone https://github.com/headwayio/shipwright-mui-react`
- `git clone` https://github.com/headwayio/shipwright-figma-plugin
- `git clone` https://github.com/headwayio/shipwright-tokens
- `cd shipwright-tokens`
- `git filter-repo --to-subdirectory-filter packages/tokens --force`
- `cd ../shipwright`
- `git remote add -f tokens ../shipwright-tokens`
- `git fetch`
- `git merge tokens/main --allow-unrelated-histories`
- `git push -f`
- repeat for figma-plugin and mui-react when ready.

# Drafts

- AI Draft
    
    Title: Migrating Different Git Repositories into a Single Monorepo: Your Step-by-Step Guide
    
    Introduction:
    Are you tired of managing multiple Git repositories scattered across your projects? Consolidating them into a single monorepo can greatly simplify your development workflow. In this blog post, I'll guide you through the step-by-step process of migrating different Git repositories into a centralized monorepo while retaining commit history. By the end of this guide, you'll have a unified "code hub" where all your projects reside. Let's dive in!
    
    Summary of Steps:
    
    1. **Cloning the Repositories**: Begin by cloning each repository locally to prepare for migration.
    2. **Creating the Monorepo**: Set up the monorepo, which will act as the central repository for all projects.
    3. **Manipulating Local Repo History**: Use the powerful `git filter-repo` command to move files into the desired subfolder structure within the monorepo.
    4. **Integrating Repositories into the Monorepo**: Add each repository as a remote in the monorepo and fetch its contents.
    5. **Merging the Remote Repositories**: Merge each remote repository into the monorepo, using the `git merge` command with the `-allow-unrelated-histories` option.
    6. **Pushing the Changes**: Finally, push the changes to the remote monorepo and complete the migration.
    
    By following these steps, you'll successfully merge your repositories into a monorepo, benefiting from improved code organization, simplified collaboration, and streamlined development processes. Now, let's proceed with the detailed instructions to make your migration a smooth and hassle-free experience.
    
    Step 1: Cloning the Repositories
    To get started, let's clone each repository locally. Open your terminal and execute the following commands, replacing `<repository-url>` with the URLs of your repositories:
    
    ```
    git clone <repository-1-url>
    git clone <repository-2-url>
    git clone <repository-3-url>
    git clone <repository-4-url>
    
    ```
    
    Step 2: Creating the Monorepo
    Now, let's set up the monorepo where we'll consolidate all the repositories. If you haven't created it yet, go ahead and clone the core monorepo using the following command:
    
    ```
    git clone <monorepo-url>
    
    ```
    
    Step 3: Manipulating Local Repo History
    Next, let's navigate to the local repository you wish to move into the monorepo. For example, let's consider the first repository:
    
    ```
    cd <repository-1>
    
    ```
    
    During the migration, we need to reorganize the files within the monorepo's desired subfolder structure. To achieve this, we'll use the powerful `git filter-repo` command. It allows us to manipulate the repository's history and move the files into the appropriate subfolder.
    
    Execute the following command to move the files into the desired subfolder structure, replacing `<subfolder-path>` with the path you want within the monorepo:
    
    ```
    git filter-repo --to-subdirectory-filter <subfolder-path> --force
    
    ```
    
    For instance, if you want to move the files into a subfolder called `packages/repository-1`, use:
    
    ```
    git filter-repo --to-subdirectory-filter packages/repository-1 --force
    
    ```
    
    This command will rewrite the repository's commit history, ensuring that all files and folders are correctly organized within the monorepo's folder structure.
    
    After running the `git filter-repo` command, proceed to the next step.
    
    Step 4: Integrating Repositories into the Monorepo
    Now, let's go back to the root of the monorepo:
    
    ```
    cd <monorepo>
    
    ```
    
    To integrate the local repository into the monorepo, add it as a remote using the following command, making sure to reference the local repository:
    
    ```
    git remote add -f <remote-name> ../<repository-1>
    
    ```
    
    Once added, fetch the remote repository to retrieve its contents and verify that the folder structure is correct:
    
    ```
    git fetch
    
    ```
    
    Step 5: Merging the Remote Repository
    It's time to merge the remote repository into the monorepo. Use the `git merge` command with the `--allow-unrelated-histories` option, allowing the merging of unrelated histories:
    
    ```
    git merge <remote-name>/main --allow-unrelated-histories
    
    ```
    
    Step 6: Pushing the Changes
    Finally, push the changes to the remote monorepo:
    
    ```
    git push -f
    
    ```
    
    Conclusion:
    Congratulations! You have successfully migrated different Git repositories into a single monorepo. By following this step-by-step guide, you've streamlined your development processes and improved code organization. Embrace the benefits of a monorepo architecture and enjoy the enhanced collaboration and simplified workflow it brings. Happy
    
- Draft 01
