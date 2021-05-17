
# [An article to understand the whole process of CI/CD pipeline](https://my.oschina.net/candou/blog/5019786)


Starting from the CI/CD process, a series of steps that encompass all stages and are responsible for creating automated and seamless software delivery is called the CI/CD pipeline workflow. Using the CI/CD pipeline, software release artifacts can move and advance in the pipeline from the code submission phase to the testing, construction, deployment, and production phases. This concept is very powerful, because once a pipeline is specified, part or all of it can be automated, thereby speeding up the process and reducing errors. In other words, the CI/CD pipeline makes it easier for companies to automatically deliver software multiple times a day.  
  
DevOps engineers are often confused with CI/CD pipelines due to the automation of various stages in CI/CD. Although different tools can automate various complex stages in CI/CD, the entire software supply chain of CI/CD may still be broken due to manual intervention. So, first understand the various stages of the CI/CD process, and why the CI/CD pipeline is essential for organizations to deliver code quickly and on a large scale.  

### CI/CD stage: understand people, process and technology

The enterprise application development team usually consists of developers, testers/QA engineers, operations engineers, and SRE (site reliability engineers) or IT operations teams. They work closely together to deliver high-quality software to customers. CI/CD is a combination of two independent processes: continuous integration and continuous deployment. The main steps are listed below.

![](https://blog.easycorp.cn/file.php?f=easycorp/202103/f_7f5e31e79ad660314059c98538d9c914&t=png&o=&s=&v=1616495836)

### CI continuous integration

Continuous integration (CI) is the process of building software and completing initial testing. Continuous deployment (CD) is the process of combining code and infrastructure, ensuring that all tests are completed and policies are followed, and then the code is deployed to the expected environment. Of course, many companies have their own processes, but the main steps are as follows.

#### CI: Code submission

![](https://blog.easycorp.cn/file.php?f=easycorp/202103/f_7f4066071c8651616e6f23481fe63cb3&t=png&o=&s=&v=1617000283)

Staff: Developers and engineers, database administrators (DBA), infrastructure team  
Technology: GitHub, Gitlab, BitBucket  
Process: The code submission phase is also called version control. Commit is the operation of sending the latest changes written by the developer to the repository. Each version of the code written by the developer is stored indefinitely. After discussing and reviewing changes with partners, developers will write code and submit it after the software requirements, feature enhancements, bug fixes, or change requests are completed. The repository that manages edits and commits changes is called source code management (SCM tool). After the developer submits the code (code push request), the code changes are merged into the basic code branch stored in a central repository (such as GitHub).

#### CI: Static code analysis

Staff: Developers and engineers, database administrators (DBA), infrastructure team, testers  
Technology: GitHub, Gitlab, BitBucket  
Process: Once the developer writes the code and pushes it to the repository, the system will automatically trigger and start The next code analysis process. Imagine such a step: the submitted code is directly built, but it fails during the build or deployment process. In terms of resource utilization, whether it is machine or manpower, this is a slow and expensive process. The static strategy of the code must be checked. SAST (Static Application Security Test): SAST is a white-box testing method that uses SAST tools such as SonarQube, Veracode, and Appscan to check code internally to find software defects, vulnerabilities and weaknesses (such as SQL injection, etc.). This is a quick check process to check the code for syntax errors. Although this stage lacks the function of checking runtime errors, this will be performed in a later stage.  
  
Putting additional policy checks into the automated pipeline can significantly reduce the number of errors found later in the process.

#### CI: build

![](https://blog.easycorp.cn/file.php?f=easycorp/202103/f_396f171180f4bb185baf106248ba8736&t=png&o=&s=&v=1617000299)

Staff: Developers and Engineers  
Technology: Jenkins, Bamboo CI, Circle CI, Travis CI, Maven, Azure DevOps  
Process: The goal of the continuous integration process is to accept regular code submissions and continue to build binary artifacts. The continuous integration process helps to find bugs faster by checking whether the new modules added and the existing modules work well. This helps reduce the time to verify new code changes. The build tool helps to compile and create executable files or packages (.exe, .dll, .jar, etc.) depending on the programming language used to write the source code. During the build process, SQL scripts are also generated and then tested together with the infrastructure configuration files. In short, the build phase is the phase of compiling the application. Other sub-activities of the build process include artifact storage, build verification, and unit testing.

#### CI: testing phase

![](https://blog.easycorp.cn/file.php?f=easycorp/202103/f_112674c3bbef3a786c80a207744945c8&t=png&o=&s=&v=1617000501)

Personnel: Testers and QA Engineers  
Technology: Selenium, Appium, Jmeter, SOAP UI, Tarantula  
Process: Publish a series of automated tests for the build process to verify the accuracy of the code. This stage helps prevent errors from reaching the product. Depending on the size of the build, this check can last from a few seconds to a few hours. For large organizations where multiple teams submit and build code, these checks will run in a parallel environment to save valuable time and notify developers of bugs as early as possible.  
  
These automated tests are established by testers (or QA engineers) who have established test cases and scenarios based on user stories. They perform regression analysis and stress testing to check for deviations from expected output. The activities involved in testing include soundness testing, integration testing and stress testing. This is a very advanced level of testing. Here you will find problems that may not be known to the developers who develop the code.  
  
**Integration testing:**  
Integration testing is performed using tools such as Cucumber and Selenium, in which application modules are combined and tested as a group, and at the same time, whether they meet the specified functional requirements is evaluated. After the integration test, someone needs to approve the move of the update set in the group to the next stage, which is usually a performance test. This verification process may be troublesome, but it is an important part of the whole process. Some new solutions emerged during the verification process.  
  
**Load and stress testing:**  
Load balancing and stress testing are also performed using automated testing tools (such as Selenium, JMeter, etc.) to check whether the application is stable and performs well in a high-traffic environment. This test is usually not run on every update, because the full stress test is long-running. When major new features are released, multiple updates will be grouped and a complete performance test will be completed. In cases where a single update is moved to the next stage, the pipeline may include canary testing as an alternative.

### Continuous deployment: bake and deployment

![](https://blog.easycorp.cn/file.php?f=easycorp/202103/f_118610f1c3ffd0f94b1d148bd183824a&t=png&o=&s=&v=1617000523)

Personnel: Infrastructure Engineer, Field Reliability Engineer (SRE), Operation and Maintenance Engineer  
Technology: Spinnaker, Argo CD, Tekton CD  
Process: After the test phase is completed, the standard code can be deployed to the server, where they will interact with Main application integration. Before being deployed to the production environment, they will be deployed to the test/staging or beta environment used internally by the product team. Before moving the build to these environments, the build must go through two sub-phases, Bake and Deploy. Both stages are inherent to Spinnaker.

#### CD: Bake

Bake refers to the creation of an immutable image instance from the source code that has the current configuration in the production environment. These configurations may be things like database changes and other infrastructure updates. Spinnaker can trigger Jenkins to perform this task, and some organizations prefer to use Packer.

#### CD: Deployment

Spinnaker will automatically pass the baked image to the deployment phase. This is where the server group is set to deploy to the cluster. Similar to the above test process, the same process is performed in the deployment phase. The deployment is first transferred to the test, stage, and finally to the production environment, and then approved and inspected. The whole process is handled by tools like Spinnaker.

#### CD: Verification

This is also the key to the team's optimization of the entire CI/CD process. Since many tests have been conducted now, there should be very few failures. However, any failures at this time need to be resolved as soon as possible in order to minimize the impact on the end customer. The team should also consider automating this part of the process.  
  
Deployment to the production environment is performed using deployment strategies (such as blue-green deployment, canary analysis, rolling updates, etc.). During the deployment phase, the running application will be monitored to verify whether the current deployment is correct or whether it needs to be rolled back.

#### CD: Monitoring

Personnel: SRE, operation and maintenance team  
Technology: Zabbix, Nagios, Prometheus, Elastic Search, Splunk, Appdynamics, Tivoli  
Process: To make a software release fail-safe and robust, it is necessary to track the running status of the release in the production environment Critical. Application monitoring tools will track performance indicators such as CPU utilization and release delays. The log analyzer will scan the log stream generated by the underlying middleware and operating system to identify behavior and track the source of the problem. When any problems occur in the production process, relevant personnel will be notified to ensure the safety and reliability of the production environment. In addition, the monitoring phase helps companies collect information about how new software changes contribute to revenue, and helps infrastructure teams track system behavior trends and capacity planning.

### Continuous deployment: feedback and collaboration tools

![](https://blog.easycorp.cn/file.php?f=easycorp/202103/f_062d7b1dbdfceb37b3038758a1bfc1b8&t=png&o=&s=&v=1617000786)

Personnel: SRE, Ops and maintenance team  
Technology: ZenTao, ServiceNow, Slack, Email, Hipchat  
DevOps team aims to release more quickly and continuously, and then continuously reduce errors and performance issues. This is achieved by frequently reporting the quality and performance of the new version to developers and project managers through slack or e-mail, and increasing the ticket price in the ITSM tool in a timely manner. Usually, the feedback system is part of the entire software delivery process; therefore, any changes during the delivery process are frequently recorded in the system so that the delivery team can take action on it.  
  
Companies must evaluate an overall continuous delivery solution that can automate or promote the automation of the above-mentioned stages.
