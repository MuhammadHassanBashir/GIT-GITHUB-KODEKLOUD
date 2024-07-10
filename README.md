# GIT-GITHUB-KODEKLOUD

GIT
---

GIT COMMIT and other commands
-----------------------------

-   mkdir <folder> and switch to the folder....
-   then initailized git with command. **git init**. its create **.git** folder in that directory.
-   then create any file and make changes on it.. **touch story.txt**. **echo "This is a beautiful story" >> story.txt**
-   Till now git untracks the files changes... because we have not told to git. You can check untracks files status of git with command **git status**

-   there are 3 areas in local git repositary **working area, staging area, committed files**

-   **Working area** where you are making changes on files or source code. It is a **untracked state**
-   **Staging area** where you prepared the files to be commit with command **git add . or git add <file-name>**.
-   **Committed file** now it time to commit(store) the changed that was made in source code with newer version. **A commit records the change of a repository compared to its previous state** with command **git commit -m "with usefull message"**  , m flage is for messages.. it is a **tracked state**


-   Storing changes in local git repositary is called commiting..  it basically save the copy of entire file within the **.git** folder. our work is now save. even if your current currpted and you can restore it from **.git**.

-   let say story.txt file is firstly committed and after you made changes in it. or ap samjty hn k mujy y changes ni chahye(unintentionally cheezy khrab hogi hn) or file ki last commit wali file change tu **working area** ma hi **git restore <file-name>** sa last commit wali file ko restore kr sakhty hn... or agr ap na changes ko intentionally kr rhy hn or phir isko untrack b krna chahty hn tu ap previous step ko follow kry gye. mean file ko working area sa stage area or phir waha sa committed files ma move krgye gye... jis sa latest changes tracked hojye gi with new version.. so previous version of commit and current version lives in gits commit history forever(.git)

- ab sir khty hn k ap na same folder ma aik already committed file ma changes ki or aik new file create ker k changes ki. jb ap **git status** kry gye tu wo apko already created file ma changes ka status **modified** btye gya or new file k status **untracked** dekhy ga.. agr ap samjty hn k dono files ko apna track krna ha tu ap dono ko working sa staging area ma move kro gye asy **git add .**. or phir **git commit -m " "** sa commit dono files k lye hoga... mean new version jo save hoga us ma in dono ki inforamation hogi..    or agr aik file ko move krna ha tu staging area ma aik file working area sa lao **git add <file-name>** sa... mean dono file aik dosary sa link ni krti kam ka lahaz sa so apisko saparate commit do gye (store) kr rhy ho.. tky dono different files ki same history na bnye...  

isi lye hmry pass **staging area** hota ha jaha humm apni marzi sa files ko before commit laty same working area sa or phir isko saparately commit krty hn..



**so best practics y ha k hr new feature or problem solve k lye new commit ho...** . multiple cheezo k lye aik commmit ni hona chahye..

agr file commit hogi ha or bug fix ni howa tu ap sahi commit wali file ko restore k sakthy hn...

important
---------

agr file commit hogi ha or bug fix ni howa tu ap sahi commit wali file ko restore k sakthy hn...

mean let sa **committed file(stored)** per ap kam kr rhy hn or let sa k apki file corrupt hogi y file sa pora data hi urrr gya... or apna file ko staging area ma move ni kya is sa **(git add . or git add <filename>)** tb tk **ap save hn**. jb ap **git status** kro gye tu wo same file 2 br dekha rhi hogi. **changes to be commit or changes not to be commited.**  

**change to be commit same file k lye is lye** because last commit sa phily jb apna file ko stage kya tha tu is na copy of file stored or preserverd thi caches ma... wo ap file ko last stage tk restore kr sakhty hn with **git restore <filename>** 

but agr ap currupted file ko again stage kr dya ha tu file override hojye gi..

-   ap **staged files** ko **unstage kr sakhty hn mean staging area sa working area ma wapis la sakhty** hn with **git restore --staged <filename>** . 

-   or apki different files hn jo aik dosary sa link ni krtyi(kam ka lahz sa) or aik sath stage hogi hn. or ap inko aik sath commit ni krna chahty, bilky stage sa **remove** krna chahty hn.. tu ap **git rm <file-name> --cached** or **git rm <file-name> -f** isko use kr k ker sakhty hn. **--cached** flage file ko unstage kr dy gi but directory ma save rakhy gi but **-f** flag sa file hi remove hojye gi...

ab file different ha or directory ma b save ha wo y again kbi stag hosakhti ha wo best practices k jin files ko ap stage ni krna chahty or wo same directory ma b hn tu ap isko **gitignore** sa ignore kr dye... basically ap files ko git ki ignorefiles ma dal rhy hogi. like **echo "<file-name>" >> .gitignore**. again **git status** krny sa file apko **untrack and .gitignore** ma mily gi..

-   you can see the **commits** that were made on source code project with **git log** command , it shows the information that you need to know about all the commits,

such as:

    -   commit hash..
    -   Author name
    -   Date
    -   commit message..

same thing do with **git log --oneline**

Git Branches
--------------

default branch is master...


we creates the branches so we can saparetly work on new features of the same task(so our work or changes on code amy not effect main code.) and make commit the branch accordingly. once our new feature task completed and tested and it look ok and ready to merge with production(main code) then we merge branch with master branch..

create and checkout(switch) new branch with same command..
---------------------------------

-   git checkout -b <branch-name>


- **To see the list of all branches and branch you are currently working on** use command **git branch**


mostly new hiring or new feature task per new branches create hoti hn thy main code per koi changes without testing reflect ni ho...

-   **Create a new branch**                  - **git branch <branch-name>**
-   **Switch to an existing branch**         - **git checkout <branch-name>**
-   **Create a new branch and switch to it** - **git branch -b <branch-name>**
-   **Delete a branch**                      - **git branch -d <branch-name>**
-   **List all branches**                    - **git branch**

**HEAD** is where, where you are right now in git repositary.. When you switch branches the head moves with you.. mean when you switch to the branch head will also switch with you..

GIT Merge
--------------

Once the feature finished and has been tested. Now we want to get all those changes of new branch into the master branch. For this we can merge branch with **git merge** command.

**The git merge command receives the name of the branch that you want to merge into our current branch..**

**mean apna agr branch to main branch k sath merge krna ha. tu phily apko main branch ma switch hona ha with command *git checkout main/master* then apko is command sa branch ko main/master k sath merge krna ha "git merge <branch-name>"**

There are 2 types of merges that git can perform, **fast-forward**, **no-fast-forward** 

**fast-forward** merge is happens when the current branch(in my case main because we are merge branch with main branch and i am standing on main branch to do this..) has no **extra commits** compared to the branch that we are merging. 

git is first try to perform **fast-forward**. this type of **merge does not create a new commit**. bilky merge krti ha us branch k commits ko branch k sath jis k sath ap branch ko merge krna chahty hn. hmy case ma hum branch ko master k sath merge krna chahty hn.. so branch apnny commits master k sath merge kry gi..  

is k bd all new change master branch ma available hojye gye..


-   what if k jis branch*(main) k sath ap new feature wali branch merge krna chahty hn us branch per **extra commits hn** jo k most cases ma hota ha. or wo branch exist ni krti so.  tu git **no-fast-forward** merge perform krta ha.. **is ma git new merging commit create krta ha active branch(main) per. or y commit **parent commit* dono branches(main or jisko main sa merge krna ha) usk lye...**

is k bd all new change master branch ma available hojye gye..

Intialized remote repository
----------------------------

We push the code to the remote repositary and pull the code back on local machine when needs. and sharing to other, and storing or many more...

most commonly use plateform **github, gitlab, bitbucket**. once the repo initailized and code pushed. we get access to connection string. 

A connection string is a URL that we can use in order to let GIT know where the remote repository is located.

-   we can add the remote repository to our local project with **git remote add origin <connection string>** command. here origin is the alais name...

is k bd hrmy ps remote repository ki access hogi... hum repository sa data **fetch** or **push** ker sakhty hn

you can list all remote repository with **git remote -v**
 
Pushing data to remote repositary
---------------------------------

We can push data(source code) from local repo to remote repo with **git push origin master**. here we use 2 argument **origin** use as alais. And **master** is use as **branch** where you wanted to push code.  In a way you can push newly commits to remote repositary... And other develops can also fetch the latest changes...

if you want to send code to same repo in other branch so you should give the other branch name with command.. like **git push origin samreen**

Cloning
-------

If you get access of all the data that currently hosted on the remote repositary... then you can **clone** the repositary. 

command **git clone [ssh link]**

let see how to get **ssh link**. Each plateform have different UI to get ssh link. 

On repo you see a big button name **clone**. in this we see **clone with ssh** here you get ssh link. 

it will gives you the same folder as git repo created. In the folder when you use **git log** you will see that we have entire gits history of the project.

Pull Request
------------

ab sir bta rhy hn k ap na jb branch ko main k sath merge krna tha tu ap y kam **git merge <branch-name>** sa kr rhy thy. ap y kam **GITHUB** plateform sa b kr sakhty hn. 

jb ap remote repo ma branch ma push krty hn. like pushed at sumreen branch. **git push origin samreen**. tu apko pop up show hota ha...  **This branch(main/master) is 1 commit behind the sumreen**

**so in order to merge sumreen branch to master through github plateform.** You have to open something called a **Pull request** 

**we can do that by clicking the pull request button show by pop up button.**

isky bd ap dekho gye sumreen branch k changes. so onces done click on **create pull request** also called **PR**. 

isky bd ap additional information add kr sakhty hn changes ko apny ki hn is sa related..

*such as title, description, labels, reviewers.*

now pull request is opened so other team members can commit on this.. once every thing approve. click on **Merge pull request** button.

the sumreen branch merge with master branch..

Fetching and Pulling
--------------------

hum abi github plateform ma pull request k through sumreen branch ko master k sath merge kya tha..

but local repository jo local machine per hoti ha.. is github plate per hoi changes sa aware ni hoti... 

like sumreen or hassan dono k pas main code tha. sumreen na kam kr k github ma apni branch ma code push kya or test ker k code ko. phir PR k through master ma merge kr dya..

ab hassan ki local repo ma y changes automatically update tu ni hosakhti... so hassan **git fetch origin master** k through github repo ki latest changes ko local repo ma fetch kry ga..

ab hum na fetch kya ha github sa origin master tu hum local repo ma master branch ko update kry gye by point latest changes made on origin master. y kam hum **merge** k through kr rhy hogy. is k lye switch to local master repo and use **git merge <fetch branch>**

we know have all the latest changes avaialbe on local repo..


-   **Instead** of individualy **fetching and merging**, We can also **pull** the **origin master branch** with command **git pull origin master**

git pull is actually **two commands in one**, **git fetch and git merge**.  

**it can fetch and merge remote changes directly into a local branch..** 

when i am using **git pull origin master**. **it can fetch and merge remote changes directly into a local master branch..** 

Git Merge Conflict
-------------------

jb tab hota ha jb 2 bndy same task per kam start kr dye.. aik bnda kam krny k bd apni branch ko phily master k sath merge kr dye or jb dosra bnda same kam lye kr apni branch ko master k sath merge kry gye tu merging conflict aye ga.. master kh rha hoga k y kam falha bnye ga ha or or branch kha rhi hogi k y is bndy ka..




there are serverl ways to resolve merge conflicts.. For example in **Git guis or simply in the code editor**

during a conflict, Git adds some extra characters to the file that conflicting.

git apko current contents or wo content dekhy ga jo ap na merge krna ha.. jis ma conflict arha ha..

**hum na simply krna y ha k wo lines ko rakhna ha jo hum rakhna chahty hn or baki conflicts line ko remove krna ha** and save the file..

isky bd isko **add** krna ha **git add <filename>** and then merge it to master **git merge <branchname>**

Fork
-----------

ab sir khty hn k thousand of project market ma chal rhy hn jis ma directly contribution k lye permission ni hoti. tu ap hum project ko pull ni kr sakhty na hi koi branches commit create kr sakhty hn.. so ap **fork** kr sakhty hn jis k bd apky ps **main project ki copy hogi** and you can add changes to a branch. Once done testing,  you send a pull request to the original project.

tky wo is changes ko apny main project ma merge ker lye...

fork krny s original project ki copy mil jati ha ap is per experiments or changes ker sakhty hn without effecting main project.

once you thing you have something to contribute to original project, then you can safely create a pull request.

origin project owner apky code ko review krta ha. or sahi hony per apki PR approve krta ha or apky code ko main project k sath merge ker deta ha..

Rebasing
-------------   y kam github ma horha hota ha..

let sa **sarah or hassan** dono kam kr rhy thy.. hassan na kam complete kya or testing krny k bd apni branch ko main k sath merge kr dya.. ab sara latest changes chahti ha tu wo 2 kam kr sakhti ha.

1- k master ko sarah ki branch sa merge kr dye.. or latest changes lye lye..
2- rebase kr k master per apni new copy rakh dye or master k changes khud b lye lye..


- one way to merge master branch to sarah branch **git branch master**. mean sarah branch per khary ho or master ko apni branch ma add kr rha ho..

- other way to do this is **rebasing branches**. jb ap rebasing ker rhy hoty hn. basically ap aik branch per dosari branch rakh rhy hoty hn..

let rebase master on top or sarah's branch.. **git rebase master** mean sarah branch master k upper agi.. ab sarah branch k ps sab changes available hogye jo master k pas thy..

although rebasing is effective way of getting changes of one branch into another.. but there are some more differences compared to merging.. 

git ma hr commit k against unique identifare hota in **hash**. it contain information about the commit. **So when we merge branches this unique identifiar would not modify.. in other words we are not modifying the history of our git commits, when we are merging..**

**when we rebase branches, we actually copy one branch to other, since we are creating new copy it hashes updates..**

Interactive rebase
--------------------

The rebase command also allows us to modify the **git history...on a certain branch before rebasing it..**

let say k hum sarah branch per kam kr rhy hn or is branch per kafi commit hn jo similar kam k lye hn so inka aik hi commit hona chahye... so. 4 commit should have been add to 1,2,3 commit..

we can change history of branch with interactive rebase..

command **git rebase -i HEAD~<no fo commits(let say 4)>** is k bd wo apko information dye ga k jis tarha sa ap y kam kr skahty hn... we can do this with **squash(to melt 3 commits into 1st)** 

information like: 

**pick <commit id> <commit mesg>**
**pick <commit id> <commit mesg>**
**pick <commit id> <commit mesg>**
**pick <commit id> <commit mesg>**

so ap jb squash use kry gy tu change 3 pick(from 2nd to last) to squash. so 3 commit combine to 1 commit...
**pick <commit id> <commit mesg>**
**squash <commit id> <commit mesg>**
**squash <commit id> <commit mesg>**
**squash <commit id> <commit mesg>**

after this save and exit.. with this.. all 3 commit successully rebase and create a new commit having all changes..

Cherry Picking
----------------

y hota ha k aik branch k ps commit ha with certain changes..  jo ap other branch per apply krna chahty hn..

but you donot want all the changes that were made to that branch

**In this case, we can cherry-pick that certain commit**. In order to create copy of that commit onto our own branch..

let say hum master branch per , sarah branch sa changes lana chahty hn... so hum phily master branch per switch hona hoga.. with use this command **git cherry-pick <hash-value-of-sarah-branch-specfic-certain-changes-commit>** tu y sarah branch ki specfic commit ki copy main per new commit k sath create kr dye ga...

Resetting and Reverting
----------------------------


With this in case of mistakes. We can **undo the commit**. mean hum na commit ker dya ha but hum sa mistakenly hogya y humy isky commit ni krna chahye tha.. so hum isko revert ker sakhty hn..

-   The first option is to **revert** the changes.. with command **git revert <hash-value of commit(jis ko revert krna ha)>** y new commit create kry ga or is per changes apply kry ga.. pichly commit sa changes ko revert kr dye ga...   

useful to undo changes and keep those changes in commit history..

-   Another way of undoing changes with **git reset** command. it is done with 2 way...

1- with --soft flag    ---> command--> **git reset --soft HEAD~1**   ---> HEAD~1 represent no of commits..
2- with --hard flag    ---> command--> **git reset --hard HEAD~1**


is sa latest commit reset hojye ga or us sa phily wali changes per ajao gye..

soft k through commit reset krny k bd hum isko access kr sakhty hn. or again commit ker sakhty hn. but hard sa reset krny k bd hmy access ni hogi us reset commit ki changes ki..

Stashing
-----------

let say ap code per kam ker rhy thy, suddently apko kisi or kam krny k kha gya like bug fix. or apka already assign task b complete ni hoga. so ap incomplete work ki changes ko **commit** b krna ni chahty or **lose(without commit)** b ni chorna chahty tu ap isko **stash** move kr dety ho. jis sa apka task commit b ni hoga or lose b ni hoga... 


commands:

-   **git stash** -- it stash all changes in working area. the modification of working area get added to the stash..
-   **git stash pop** -- with this command you can get back changes to the working area.
-   **git stash list** -- with this command you can list the stash.
-   **git stash show stash@{1}** -- with this command you can the content of stash files..
-   **git stash pop stash@{1}**  -- pop specfic stash
 

git stash simply krny sa wo staging area sa stash ma file ko move kr deta ha..


Reflog
----------

Everyone makes mistakes... sometimes it may feel like you have screwed up your git repo so badly. 


like let sa sarah apni branch per kam kr rhi ha.. or usa mistakenly commit hoga jo wo ni krna chahti thi... so wo **git reset --hard HEAD~1** sa commit to remove kr deti ha. but later on she realized k commit sahi tha. but wo **-hard** use ker k hard reset ker bethi ha.. so sara data lose hogya...

**but asa ni ha..** The git **reflog** command shows us all the actions that have been taken on our repo.

it includes , merger, reset, reverts and any alternates...


**you can easily undo this by resetting HEAD based on the information that reflog gives us**

sarah apna hard reset undo kerna chahti ha..

reflog ki output ma sarah na dekha k reset sa pichy wala commit per us na jana. wo is tarha sa ja sakhi ha..

git reset --hard <reflog k through dekh howa commit in hash values..>

is tarha sa hard reset k bd b wo apny commit ki changes ko wapis hasil kr leti ha..

git log sirf apko commits or mesg dekhta ha but git reflog isky sath state of repo b dekhta ha...


other commands:
---------------
-   git hash-object <filename>
-   git ls-files
-   git rev-parse
-   git ls-remote
-   git cat-file -p <commitname>
