# A header

Read this stuff

## A section

# Linking RStudio package development to github

## Preliminaries
These steps are done once and then work for all projects:

1. Follow the steps in github.R, basically
 - install *git*
 - create a *github* account
 - use `devtools` to configure git for your github account [instructions provided in `github.R`]
 - Obtain a "personal access token" (PAT) for the github account [instructions provided again]
 - Add the PAT to the `.Renviron` file [instructions provided again]
 
2. Tell RStudio the location of git (`where git`) in Preferences --> Git/SVN --> Git executable
	
3. Go ahead and follow [Wickham's suggestion](https://r-pkgs.org/setup.html#personal-startup-configuration) to add `devtools` to `.Rprofile`:
  - `devtools::use_devtools()`
    - .Rprofile appears for editing, code to load devtools in interactive sessions is added
    - Accept those changes by saving .Rprofile

## For each package project:
Be sure `devtools` is always loaded (it will be if you follow step 3 above)

**Create a blank project for the new package:**

  1. Create a new folder for the package project: *`pathto/packagename`*

  2. In RStudio, `create_package('pathto/packagename')`
    - Loads of stuff happens while the structure for *a new package project is built*
    - The R session restarts
    - On restart, you will now be in the *packagename* folder
	- Stay in this folder for the next steps
	
**Attach git to this project:** 

1. `use_git()`
 - The "git" tab now appears in the upper right panel.
 - use\_git will offer the chance to commit some basic files for you, but I preferred seeing what was happening, so I decline this offer
 - When you open the "git" tab, you see all the different files in your new package project
 
2. In the git pane, select the files, and **Commit**
  - **NOTE!** The commit won't happen **unless** you add a commit message! There's no feedback to suggest this is necessary rather than just a good idea :( Standard practice for this first commit seems to be to use the message "Initial commit"
  - The commit creates a *new local repository*
    - Nothing has been uploaded to github at this point.

**Push the new local repository to github:**  

1. Go to github and create a new repository for this project.
  - I made the repository public, but did not ask github to create any files (I'll do that from RStudio)
2. github will provide code to "...push an existing repository from the command line". 
  - Copy this code to the clipboard
  - (Remember, the "exiting repository" was created within RStudio in the above steps)
3. Execute the copied code in a terminal window within RStudio: Tools --> Terminal --> New Terminal
  - That should do it! If you refresh the github browser window, it should now have the committed code.
  
**Adding new or modified files:**

1. RStudio seems to keep track of this for each project.
  - As changes are made, the "git" tab in the upper right will show the new and modified files.
2. When ready to commit, go to the git pane and select the files to be added to the repository
3. "Commit" and be sure to add a message, as before during the first commit. This window can then be closed
4. The git pane contains an up and down arrow. Now that the local and github repositories are linked, you can keep the public github version in sync just by hitting the up arrow.


  
 
