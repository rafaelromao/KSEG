---
title: KSEG - Key Software Engineering Guidelines
layout: page
---

A set of key guidelines for keeping software development under control.

## Objective

This article has as objective to summarize a set of guidelines that indend to help teams organize their software development process.

Since they are guidelines, say what is necessary to accomplish but not how, the development teams will have enough freedom to tailor their development processes according to their needs and reality.

## Motivation

Software development processes, methodologies and even guidelines are abundant in our industry, yet no concensus can be made about which one should be followed to be inevitably successfull. Such thing does not exist.

In the last years, agile methodologies and devops pratices are becoming very popular and many times lead to success, but other times are abused and fail miserably.

The lack of consistency and practical references to guide the teams during the application of these methodologies and practices lead to mess and confusion, which produces delays and bad quality as result.

The motivation for this article comes from the need to stabilish a set of guidelines that allow a team to be flexible, agile as needed, and at the same time well organized, making use of the most popular and successful tools and pratices available to deliver good software.

## Format

This article presents some definitions followed by a set of key guidelines to keep the production of software and management of software projects under control.

The guideline names and reference codes will be highlighted in **bold** font.

The terms MUST, SHALL NOT and MAY, used in this article, must be interpreted according to the [RFC 2119](https://www.ietf.org/rfc/rfc2119.txt).

## Definitions

**Software Artifact**: Framework, library, component or module developed or extended and used as part of a software system. Software artifacts can be open source or proprietary, developed by the company that used them or by a software development community.

**Software Artifact Family**: Group of software artifacts that are logically related or interdependent. An example of software artifact family are the components of a software framework.

**Software System**: Set of integrated software artifacts that attend to a set of software project requirements. For every software system produced or extended, a software project must exist to manage it.

**Software System Family**: Group of software systems that are logically related or interdependent.

**Software Project**: Set of requirements, specifications and plans that define how a software system shall be developed or extended.

**Management Board**: A physical or virtual board, accessible to all stackholders, including the development team, that displays information about the project, artifact or system evolution.

## KSEG 1. Guidelines for development of Software Artifacts

**KSEG 1.1.** **Every software artifact MUST have a owner.**
The owner of the software artifact will be its maintainer, the professional responsible for its lifecycle and evolution.
Stabilish a owner for an artifact allows a centralized control of its individual evolution, at the same time that distribute tha load of responsibility throughout the development team.
A software artifact owner will be responsible for:
- Manage the evolution of the software artifact, implementing and coordinating the implementation of new features, managing its dependencies and fixing defects.
- Configure and maintain the execution of lifecycle management processes such as continuous integration and deploy, automated tests execution, code quality analysis, as well as its wiki and backlog pages.
- If necessary, the ownership of an artifact can be transfered to another team member, but that must have a valid justification of that.

**KSEG 1.2.** **Every software artifact MUST have a wiki page.**
A wiki page is used to descrebe the software artifact and give any other relevant information about it, such as its purpose, applied technologies, dependencies, external links and a short manual about how to use it.
The maintenance of the wiki will put the knowledge about the software artifact available explicitly and easily accessible by all development team.
Anyway, this page SHALL NOT be seem as an exaustive documentation of the software artifact, but instead as a first reference for fulture use.

**KSEG 1.3.** **Every software artifact MUST have its backlog maintained.**
The backlog of a software artifact is the set of work that must be done to deliver its next versions and this work must be known and managed. The use of a backlog management system, using a software or even a wall and some post-its , avoid this work to be forgot.
Every software artifact can evolve independently from the software system that use them, so it is important that its backlog be managed independently too.

**KSEG 1.4.** **Every software artifact MUST have its source code managed by a version control system.**
The registration of the source code in a version control system gives more flexibility for the developers to work on different alternatives for a problem resolution and manage which of them will be integrated to the main source code, besides it allow each developer to work isolated in a subset of the source code that will not be continuously modified by the remaining developers of the team.
The modification history provided by the version control system also allow any version of the software artifact to be recovered and modified, if necessary.
Strategies like the [Git Flow](http://nvie.com/posts/a-successful-git-branching-model/) are realy helpful when differente features and versions of a software artifact or system must be maintained.

**KSEG 1.5.** **Every software artifact MUST have its specifications verified by automated tests.**
The use of formal specifications, verified by automated tests, allow the developers to delimit their tasks and be notified when their implementations does not satisfy what is expected, as well as when something changed breaks working functionalities.
Such specifications can be implemented using methodologies like [Specification By Example](http://martinfowler.com/bliki/SpecificationByExample.html) or [Test-Driven Development](http://c2.com/cgi/wiki?TestDrivenDevelopment).

**KSEG 1.6.** **Every software artifact MUST be developed using design techniques that favor its reuse.**
By definition, a software artifact must be a reuseble piece of software, and to allow for this property, the development of the software artifact must have it in consideration the whole time.
Follow principles and patterns such as [GRASP](https://en.wikipedia.org/wiki/GRASP_%28object-oriented_design%29) and [SOLID](https://en.wikipedia.org/wiki/SOLID_(object-oriented_design)), specially the Information Expert and SRP ones, are essential for a good degree of reusability.

**KSEG 1.7.** **Every software artifact MUST be registered in a continuous integration tool.**
Continuous integration tools integrates the changes made by different developers into potentially shippable products. During this process, automated tests are automatically executed and feedback reports are generated.
The existense of test execution and feedback reports after every build allow the development team to be aware of most problems that may affect that build earlier.

**KSEG 1.8.** **Every software artifact MUST be registered in a source code quality analysis tool.**
Source code analysis tools screen the source code searching for pontential flaws, bad practices, vulnerabilities, unnecessary complexity, repeated code, lack of appropriate test coverage and applying many other metrics that help the developer to maintain the source code in a good quality standard, helping them to build better software products.

**KSEG 1.9.** **Every software artifact MUST be registered in a continuous deployment tool.**
Continuous deployment tools allow new versions of the software artifacts to be automatically published once approved by the integration process.
Using this tools allow the developer to focus on the development work and deploy as often as necessary.

**KSEG 1.10.** **Every software artifact MUST adhere to a consistent versioning scheme.**
Versioning schemes like [SemVer](http://semver.org) allow the consumer of a software artifact to have previsibility about how the changes in a new version will affect their softwares. Despite the selected scheme, a consistent one must be used and the rules about how it works must be explicitated in the software artifact documentation.

**KSEG 1.11.** **Every software artifact MUST be registered in a reuse management tool.**
Reuse management tools, or package distribution tools, allow the consumer of a software artifact to have a small set or a single source for the consumption of the software artifact files it depends on.
This tool must be used not only for open sourced software artifact but also for the software artifact developed inside the organization.
Tools like NuGet, Maven and NPM are standards package distribution tools for their respective platforms.

**KSEG 1.12.** **Every software artifact MUST consume other software artifacts only through reuse management tools.**
It is important that the minimum of package sources are used for consuming dependencies in a software artifact. If a new software developer in the team need to know specific details about how to consume specific packages, changes are he will eventually make a mistake. The use of a single or small set of package sources, through a reuse management tool helps mitigate this risk.

**KSEG 1.13.** **Every software artifact MUST have license terms.**
Since software artifacts are indended to be reused, internally to the organization of publicly as open source projects, there must exist license terms that define how these artifacts can be reused.
In some cases, the reuse will be allowed only internally to the organization. Other times, no reuse will be allowed at the time. Anyway, it is always necessary to have the license terms explicitated in the software artifact's documentation.
For open source projects, information about the most common license terms can be found at [http://opensource.org/licenses](http://opensource.org/licenses).

**KSEG 1.14.** **Relevant software artifact MAY have its evolution published in management boards.**
The owner of a software artifact may decide to publish its evolution in a management board. For small software artifacts, this is often not needed, but for large ones they might be necessary.

## KSEG 2. Guidelines for development of Software Systems

**KSEG 2.1.** **All guidelines applicable to software artifacts MUST also be applicable to software systems**.
Every software system is also a software artifact. The difference is that it can be used directly by an end user and not by other developers.

**KSEG 2.2.** **Every software system MUST have its development or extension managed by a software project.**
A software project will defined the requirements, specifications, plans and how the software system must be developed or extended to fullfil the customer needs.

**KSEG 2.3.** **Every software system MUST have its requirements validated by a software quality assurance team**.
Different from software artifacts, that are only parts of a software system and are directly used only by other software developers, software systems are directly used by a customer. Therefore, every software system need to be tested by a software quality assurance team, in order to avoid that its problems are identified by the customer after the deployment of the software.

**KSEG 2.4.** **Every software system MUST publish its evolution in a management board**.
At every moment, all stackholders, including the development team, must have access to the current state of the software system development. Therefore a management board for every software system is necessary.

## KSEG 3. Guidelines for management of Software Projects

**KSEG 3.1.** **Every software project MUST be supervised by a Project Management Office.**
A project management office is a division of the organization that rules the development of software projects and they shall be responsible for the supervision of every software project in execution.

**KSEG 3.2.** **Every software project MUST have a Project Manager.**
While every software artifact or system must always have a owner, a software project must have a project manager, which will be responsible for the management of the project and the delivery of the defined scope within the cost and time, as well as manage the development team accordingly.
It is important to emphasize that role of the project manager can not be confused with the role of the technical leader.

**KSEG 3.3.** **Every software project MUST have a Technical Leader.**
Even though the Project Manager is the main responsible for the software project, technical decisions and the management of the development team many times will not be among his/her qualifications. In these cases, the presense of an experienced professional, capable of addressing technical and interpersonal issues, acting as technical leader, will help the project manager to take the team to its best performance and produce better software systems.

**KSEG 3.4.** **Every software project MUST have a kickoff meeting.**
In a kickoff meetings, all relevant known details about the software should be presented and discussed with the development team. That allow everyone to start the project going to the same and right direction.

**KSEG 3.5.** **Every software project MUST balance agility and discipline.**
Agility does not imply in good software if the situation does not favor agile methodologies. It is important to know what agile and traditional practices best fit the needs of the project and how to reconcile and apply them accordingly.

**KSEG 3.6.** **Every software project MUST have a wiki page.**
As well as every software artifact and software system, every software project must have a wiki page to register its details and allow the stackholders to have a glance at them when needed.

**KSEG 3.7.** **Every software project MUST have its backlog maintained.**
Every software artifact and software system will have its own backlog, even when they are build by a specific software project. A software project ends but the software artifact and software sustem it produced continues moving on and other software projects may be consituted to manage such evolution, that is why it is importante to also have a software project backlog, summarizing the high level issues that are pertinent to the project itself.

**KSEG 3.8.** **Every software project MUST publish its evolution in a management board.**
While software artifact and software system management board details their features and evolution, project management board focus in the on going of the project. The same way wiki pages and backlogs for projects must be separated from artifacts and system, the management board shall also be indenpendent.

**KSEG 3.9.** **Every software MUST register and keep its scope, due dates and requirements updated and available to the development team during all the project duration.**
It is common some development teams loose the big picture and the right focus during the implementation of a software, even when using a iteractive process. Having the scope, due dates and requirements updated in the management board and rediscused during the evolution of the project help to mitigate this risk.

**KSEG 3.10.** **Every software project MUST perform frequent short meetings.**
These meeting might be daily or weekly or with any other cadence, but they need to be frequent enough to allow the team to be constantly aware of what any other team member is doing. In these meetings all team members must share what they did since the last talk, what they will do until the next one and what the others can do to help him. This not only improve awareness but also help each team member to focus in the work they are doing.

**KSEG 3.11.** **Every software project MUST have its development performed in an iterative way.**
Interative process are based on constant feedback and adaptative evolution. Agile methodologies have proven that this behavior can leed to better software.
Even though in some cases complete agile processes are not the best choice for certain projects, an iterative approach during the project execution can always be helpful.

**KSEG 3.12.** **Every software project MUST perform partial deliveries to the software quality assurance team.**
The software quality assurance team is responsible for verifying if the software system developed by the software project presents the expected quality and fulfill the project specifications. To enable that team to make their work, it is important that they receive frequent updates of the software system as it is implemented, avoiding that their tests loose value due to have being performed over outdated software versions.

**KSEG 3.13.** **Every software project MUST perform partial deliveries to the customer.**
A long lasting software project, with few or no feedback from the customer, has a high risk of delivering a system that do not attend the customer expectations, even fulfilling its formal specifications. The customers only know for sure if the software will add value to their business after they use it. So it is important that as soon as the software is validated by the software quality assurance team, it be delivered to the customer to evaluate or even use it in production.

**KSEG 3.14.** **Every software project MUST have a closing celebration.**
Software development teams tend to be passionate about their work and recognition of their success through money only is usually not enough. It is important, at the end of every software project, to give a celebration to the work done and thanks every person involved for their dedication and good job.
Some times it is also necessary just to make clear that that project is indeead done, and is not being perpetually extended or something like that.

##Final considerations
Different methodologies, practices, techniques and technologies may be used to follow the guidelines in this article. That allows the team to have the flexibility they need and still work in an organized manner.

And as expected for any open sourced project, this set of guidelines may change at any time and the feedback from the community is well appreciated.

## License
Creative Commons - CC0 1.0 Universal

## Versioning
SemVer 2.0

## About
Version: 1.1.0

GitHub Project: [KSEG](https://github.com/rafaelromao/KSEG)

Authored by [Rafael Romão](https://github.com/rafaelromao/) in August, 2015
