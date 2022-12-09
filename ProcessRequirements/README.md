# Open source contribution requirements for developers

To pick an issue from github it has the following labels.

- Bug 

- Feature request

- Docs

- Good first issue

https://docs.vuestorefront.io/v2/contributing/


### Branching Model 

They have two primary branches.

- Main 
- Develop 

### main branch 

https://docs.vuestorefront.io/v2/contributing/branching-model.html

The main branch contains the code for the latest released version. they update this branch only to:

- fix a bug present in the current version,
- release a new minor- or patch-level version.
 
Since this branch is "production" branch it needs to be reliable, tested, and well-documented. It is also the highlight of what they provide as it is the default branch displayed in vue Storefront GitHub repositories.
 
### develop branch 
The code for the subsequent minor version is located in the develop branch. It is mandatory to merge any brand-new features, unfixable flaws, and bug fixes into this branch.
 
It might have some kinks, be unstable, lack some tests or documentation because it's a development branch. they do not, however, combine unfished work. they create a feature branch and merge it to the develop once it is complete if a given functionality requires several 
 
#### Some common scenarios are 
- Adding new feature or introducing breaking changes
- Fixing a bug present in the latest released package
- Fixing a bug present only on the develop branch 
- Adding a big feature in a few Pull Requests
 
### How to submit a Pull Request 
 

 https://docs.vuestorefront.io/v2/contributing/how-to-submit-pull-request.html


Check your tools
To check tools run both commands.

 
- Git -–version
- yarn --version
 
Pick a target branch 
Pick the target branch and fork it .
 
#### Start coding 
 
To instal all necessary dependencies run the following comand
 
- Yarn install
 
This command will install tools like eslint, husky, and a few others that will ensure that your code follows our rules and conventions.
 
#### Manually test the changes 
Once your changes are ready, manually test them in development and production modes.
If the repository contains a Vue Storefront project (often called theme), run all the build commands defined in the package.json file and start the project to test it. If everything works as expected, you can go to the next section.
If there is no Vue Storefront project, create a new project using thier Installation guide. Then, open its package.json file and look for the name of the package you modified in the dependencies or devDependencies.

#### Update documentation 
Now it's time to update the documentation. If your change is a bug fix, it likely doesn't require any updates to the documentation. However, it might be needed if you add new functionality or change the behavior of the existing one. Open the official documentation for the package and see which documents need updating. Then, look for the docs folder in the project and find the document you want to update - the path inside this folder will match the documentation URL.

#### Commit and push your changes 
We use Conventional Commits 
(opens new window)
, which requires specific commit messages and Pull Request title formats. Later these messages are used to automate the changelog generation using the Angular changelog preset 
(opens new window)
to inform the community and our partners about what changed with the given release.
A commit message consists of a header, body, and footer. The header has a type, scope, and subject:

<type>(<scope>): <subject>

<BLANK LINE>

<body>

<BLANK LINE>

<footer>

 
The header is mandatory, and the scope of the header is optional. The subject contains a short description of the change:
use the imperative, present tense: "change" not "changed" nor "changes",
don't capitalize the first letter,
no dot (.) at the end,
don't exceed 100 characters.
See the Examples 
(opens new window)
section for more details.

#### Create a Pull Request 

It's time to create a Pull Request. When doing so, try to fill in the form, including the description, related issues, etc. Refer to the Branching model document to correctly pick the target branch.
Wait to see if all GitHub Actions completed successfully. 
 
 
# REVIEW PROCESS 
If any developer wants to contribute in vue store front then the developer has to report that issue and vue storefront team do their best review in a reasonable time.
 
https://github.com/vuestorefront/vue-storefront/blob/main/CONTRIBUTING.md



# ISSUE LIFECYCLE MANAGEMENT
 
### Following are the guidelines when reporting issues:
- Provide a title in the format of
 Ex:[BUG] : when , [Issue] : When i try to , an appears. 
- Tag your issue with the tag triage-needed.
-  Provide a short summary of what you are trying to do . This includes a short description of error.
- Provide the log of the encountered error if applicable . If  mentioned, it is good.
- Provide the exact version of the framework you are using. 
- Be awesome and consider contributing a pull request.




# Version and Release Management Control
The latest version of vue storefront is 1.12.3.  

Before this version they had versions
 - 1.12.2 
 - 1.12.1 
 - 1.12.0 
 - 1.11.4 
 - 1.11.3 
 - 1.11.2 
 - 1.10.6
 - 1.11.1 
 - 1.11.0  etc.

https://github.com/vuestorefront/vue-storefront/releases

In all these visions they fix bugs , fix some navigation , fix overlapping text (https://github.com/vuestorefront/vue-storefront/issues/4024) , fix error messages (https://github.com/qiqqq),


But in the latest version they added states.json in core/i18n/resource , Added phone validation helper , Configurable enabling min & max price aggregations , Storing totals in localStorage to sync it between tabs and Support for trailing slashes in the route paths . Some issues are also resolved in latest version 1.12.3 such as Fix gallery image generation by checking if image exists , Fix getSelectedOption based on attribute_code check , add new resetUserInvalidation action to clear invalidation state before login, clear order history and refresh token after logout, Multi-tab cart-sync in multi-store environment , Incorrect load of default address in checkout and Fix Order History Pagination. Moreover , changes and improvements are made in the latest versions such as
- Moved hard coded fields from omitSelectedVariantFields.ts to config #4679. 

- Bump dependencies versions such as #4715,#4696and #4951. 
- Using days for dates in taxCalc.ts to make it work properly in Safari #5364. 
- Awaiting addItem action call inside mergeServerItem action. 
- Moved Phone Num to proper branch. 
- Development hot-reload speed webpack config - #5559 

https://github.com/vuestorefront/vue-storefront/releases

Vue storefront has 50+ releases and the latest version is 1.12.3. Vue storefront
has 274+ contributors and languages used in these releases are
TypeScript , Vue.js , javaScript , HTML and have a DockerFile.
How Vue Storefront versions are released

From version 1.9, vue storefront release each of the VSF versions in two phases:

● Release Candidate phase (RC), also called feature version. This version
contains all the new features, improvements, and additions to the API,
along with minor bug fixes. New features and additions are merged and
released only during this phase. The API of features introduced during this
phase may slightly change.

● Stabilization phase is the one that ends up with a production-ready version.
During this phase, they only do stabilization and bug fixing for previously
introduced features. No new features and API additions are merged. PRs
from the RC version are tested and their API is simplified and/or adjusted
according to feedback.
Assuming the next version is 1.x, the two-month cycle will look like the following:

● v1.x-RC.y—unstable version with cutting-edge features ready to test and
feedback.

● v1.x.y—stable version of the software ready for production use.

● How new features are merged
During the RC phase, features Pull Request with new features after feedback and
acceptance are normally merged to the Develop branch. After entering the
stabilization phase, they are tagging the current develop branch, creating a
release/x (where x is the number of the current version) branch from it and
working on stabilization there. During the stabilization phase, new features are
merged to develop the branch and will be merged in the next RC phase.

● Release cycle flow
● Development Phase

In the first phase of the cycle, they're mostly focusing on features and
improvements. Branches in this phase should be created from the actual
development, also PRs should be pointed to this branch. Changes merged to
develop are available to test on.
Here is the pictorial representation

● Release Candidate phase
At some point, when the milestone for next minor versions is completed, they are
creating a new branch from the development called release/vx.y (example:
release/v1.9). After that new branch is tagged as the first RC for version
(example v1.10.0-rc.1). Then it's ready for testing by the community. During tests,
feedback and stabilization there could be multiple Release Candidate versions on
this branch. When improvement is made on this phase, then branches should be
created from actual release/vx.y and should not contain features at this point -
only improvements for current release. After merging a set of bug fixes and
improvements into the release branch, it needs to be tagged as the next RC
version and merged into the develop branch, to update it.
Here is the pictorial representation

● Release phase
When the RC version is stable, the release branch is merged into master and
tagged as the next stable version (example v1.9.0). After that, the currently
merged release branch is deleted and starts a new development phase. If some
critical bug is discovered on the current stable version,) branch should be created
from the actual master. After merging and testing hotfixes, this branch (like the
release branch before) is merged into master.
Here is the pictorial representation.

● Summary
An important thing to note is that this releasing cycle ensures stable and reliable
Storefront releases. Phases are also not blocking new features—you can develop
new features on any phase, but it should be merged only to the develop branch
and go through the whole cycl

