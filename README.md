# devops-upskill
Final project - [Upskill DevOps](https://www.telerikacademy.com/upskill/devops)

This repo introduces CI in the [Gitflow workflow](https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow) branching strategy. 
The aim is to guarantee the delivered software's quality and make the deployment to the test and production environment easier by:
- automation of the unit testing
- automation of the static code analysis
- automation of the dependency vulnerability check
- automation of the artifact's building and deployment
- automation of the container's building and deployment

## Feature delivery - VSM

Automate the processes in green:

![vsm](./src/main/resources/static/vsm.png)

## Workflows

### Open a pull request towards `develop` or `main`
Cases:
* implement a feature
* resolve a bug
* prepare a release

![test-and-verify](./src/main/resources/static/test-and-verify-workflow.png)

### Push to `main`or `develop`
Cases:
* release a new version
* merge a feature/bug

![build-and-push](./src/main/resources/static/build-and-push-workflow.png)

## End-to-end tests
https://github.com/ivailozd/devops-upskill-test/

## Bring in SCA (Software composition analysis)
### Why SCA?
* keep track of all third-party dependencies' licenses and vulnerabilities
* fix any issues early in the SDLC

### How to choose?
An open [guide](https://www.linuxfoundation.org/tools/an-open-guide-to-evaluating-software-composition-analysis-tools/) to evaluating software composition analysis tools.
#### Evaluation metrics
1. Knowledge base (size, source languages, package level detection and binary scanners, frequency of update)
2. Detection capabilities (vulnerabilities ranking, analysis type support - Dependency scanners, Binary scanners, Snippet scanners, License scanners)
3. Ease of use (Intuitive design and user interface, Requires minimal to no training)
4. Operational capabilities (Speed of source code scans, Support for different audit models, Build system (CD/CI) agnostic)
5. Integration capabilities (Provides APIs for easy integration, Support UI integration capabilities)
6. Security vulnerabilities database (Size and frequency of update, Number of sources, Precision)
7. Advanced vulnerabilities discovery method - when vulnerable code was copied into a new component
8. Associated costs (Infrastructure cost, Operational cost, Yearly licensing cost)
9. Support for deployment models (What information about your code and projects leave your networks?)
10. Reporting capabilities (Generated or pulled from the knowledge base?, Standard formats?)

### Why Snyk
* supports `Java` and `Maven`
* free and easy for a start - just create an account and configure the project
* easy integration with Git and the developer's IDE
* automated fix pull requests
* "industry-leading security intelligence database" - frequently updated
* test and automated PR periodically

### Comparison to others?
#### WhiteSource ([link](https://www.whitesourcesoftware.com/))
pros:
* highly scalable
* easy to use developer tools

cons:
* no trial period

#### Synopsys/Black Duck ([link](https://www.blackducksoftware.com/))
pros:
* the best governance solution (audit and risk reporting)
* variety of databases, including the National Vulnerability Database

cons:
* no trial period
* the most expensive

#### Snyk ([link](https://snyk.io/))
pros:
* straightforward integration into the SDLC

cons:
* poor governance solution (audit and risk reporting)

### What configuration do we need?
* Configure the project to Snyk
* Configure a job in [testAndVerify.yml](./.github/workflows/testAndVerify.yml)

## Bring in SAST (Static application security testing)
// TODO

## Things to do
* deploy the artifacts to an artifactory
* scan the containers for vulnerabilities

## Next goals
* automate QE testing
* follow a more straightforward branching strategy for simplifying CI
* automate test and staging environments deployment
* bring in DAST (Dynamic application security testing)

## Further goals
* implement CD
