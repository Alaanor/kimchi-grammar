# Create a fork of Kimchi Reader

1. Make a Github account if you don't have one already.
2. Click on the fork button at top right of [Kimchi-grammar repo](https://github.com/Alaanor/kimchi-grammar).
3. Git clone the fork you made (will need a console with git install) and the command is git clone [your repo url]
    - Install something like [Git Bash](https://git-scm.com/downloads) or any other tool you prefer using.
    - Make sure you git clone to a folder you want the files to be in on your own computer.

# Start creating grammar pages with Visual Studio Code

1. Install [Visual Studio Code](https://code.visualstudio.com/download).
2. After installing, in Visual Studio Code (VSC) go to File > Open Folder and select the repo you cloned ealier.
3. Create a branch from main for the new grammar you want to add, or file(s) you want to change.
    - On the left side in VSC you have "Source Control", click on that.
    - From there on the line "Source Control" click the three dots > branch > create branch from > then select "Main" from the top right.
    - Once you created the new branch an option called 'Publish Branch' is available, click on that.
4. Now you can create a new file with your grammar point or change existing files.
5. Once you have created a new grammar point or editted existing files at the same place in "Source Control" you should see a blue '1'.
    - Enter a message for your commit (e.g. "Created V+아어야 되다" or "Updated files with extra description").
    - Then you press commit and it will commit the specific change to the branch you created.
6. If you are happy with the grammar point you created or the changes you made, you can open a pull request.
    - Open Github on your own repo (the one that was forked earlier), you should see an option to create a new pull request.
    - In case you don't see the option, you can always select the specific branch by clicking on 'Main' and going to the specific branch you created.
    - Then within that branch you can select the option 'Contribute' to make the pull request against [Kimchi-grammar repo](https://github.com/Alaanor/kimchi-grammar).
7. Now you have to wait for Alaanor to merge the pull request and implement the changes you requested. 
    - While it hasn't been merged yet you can keep adding or fixing things to the files you made.

# Cleaning up your branches through Visual Studio Code and/or Github

1. After Alaanor has merged your pull request into main, you can just delete your branch through VSC and/or Github.
2. In VSC press CTRL+SHIFT+P and select "Git: Delete Branch" and select the branch you want to delete.
3. In Git click on 'Main' and select 'View all branches' then click on the recycle bin icon for the ones you want to remove.