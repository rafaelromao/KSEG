# KSEG - Key Software Engineering Guidelines  

A set of key guidelines for keeping software development under control.

## Disclaimer

This article was originally written in 2015 and is republished here for portfolio purposes. The original version can be found in the `gh-pages` branch of the [GitHub repository](https://github.com/rafaelromao/KSEG).

## Objective

This article aims to summarize a set of guidelines intended to help teams organize their software development process.

Since they are guidelines, they state what is necessary to accomplish but not how, so development teams have enough freedom to tailor their development processes to their needs and reality.

## Motivation

Software development processes, methodologies, and even guidelines are abundant in our industry, yet no consensus exists about which one should be followed to be inevitably successful. Such a thing does not exist.

In recent years, agile methodologies and DevOps practices have become very popular and often lead to success, but other times they are abused and fail miserably.

The lack of consistency and practical references to guide teams during the application of these methodologies and practices leads to mess and confusion, which results in delays and poor quality.

The motivation for this article comes from the need to establish a set of guidelines that allow a team to be flexible and as agile as needed, and at the same time well organized, making use of the most popular and successful tools and practices available to deliver good software.

## Format

This article presents some definitions followed by a set of key guidelines to keep the production of software and the management of software projects under control.

The guideline names and reference codes will be highlighted in **bold** font.

The terms MUST, SHALL NOT, and MAY, used in this article, must be interpreted according to [RFC 2119](https://www.ietf.org/rfc/rfc2119.txt).

## Definitions

**Software Artifact**: Framework, library, component, or module developed or extended and used as part of a software system. Software artifacts can be open source or proprietary, developed by the company that uses them or by a software development community.

**Software Artifact Family**: Group of software artifacts that are logically related or interdependent. An example of a software artifact family is the set of components of a software framework.

**Software System**: Set of integrated software artifacts that meet a set of software project requirements. For every software system produced or extended, a software project must exist to manage it.

**Software System Family**: Group of software systems that are logically related or interdependent.

**Software Project**: Set of requirements, specifications, and plans that define how a software system shall be developed or extended.

**Management Board**: A physical or virtual board, accessible to all stakeholders, including the development team, that displays information about the project, artifact, or system evolution.

## KSEG 1. Guidelines for development of Software Artifacts

**KSEG 1.1.** **Every software artifact MUST have an owner.**  
The owner of the software artifact will be its maintainer, the professional responsible for its lifecycle and evolution.  
Establishing an owner for an artifact allows centralized control of its individual evolution, while distributing the load of responsibility throughout the development team.  
A software artifact owner will be responsible for:  
- Managing the evolution of the software artifact, implementing and coordinating the implementation of new features, managing its dependencies, and fixing defects.  
- Configuring and maintaining the execution of lifecycle management processes such as continuous integration and deployment, automated test execution, code quality analysis, as well as its wiki and backlog pages.  
- Transferring ownership of an artifact to another team member when necessary, as long as there is a valid justification for that change.

**KSEG 1.2.** **Every software artifact MUST have a wiki page.**  
A wiki page is used to describe the software artifact and provide any other relevant information about it, such as its purpose, applied technologies, dependencies, external links, and a short manual about how to use it.  
Maintaining the wiki makes knowledge about the software artifact explicit and easily accessible to the entire development team.  
This page SHALL NOT be seen as exhaustive documentation of the software artifact, but instead as a first reference for future use.

**KSEG 1.3.** **Every software artifact MUST have its backlog maintained.**  
The backlog of a software artifact is the set of work that must be done to deliver its next versions, and this work must be known and managed. Using a backlog management system, whether a software tool or even a wall and some sticky notes, prevents this work from being forgotten.  
Every software artifact can evolve independently from the software systems that use it, so it is important that its backlog be managed independently as well.

**KSEG 1.4.** **Every software artifact MUST have its source code managed by a version control system.**  
Registering the source code in a version control system gives developers more flexibility to work on different alternatives for solving a problem and to manage which of them will be integrated into the main source code. It also allows each developer to work in isolation on a subset of the source code that will not be continuously modified by the remaining team members.  
The modification history provided by the version control system also allows any version of the software artifact to be recovered and modified if necessary.  
Strategies like [Git Flow](http://nvie.com/posts/a-successful-git-branching-model/) are really helpful when different features and versions of a software artifact or system must be maintained.

**KSEG 1.5.** **Every software artifact MUST have its specifications verified by automated tests.**  
The use of formal specifications, verified by automated tests, allows developers to delimit their tasks and be notified when their implementations do not satisfy what is expected, as well as when a change breaks previously working functionality.  
Such specifications can be implemented using methodologies like [Specification By Example](http://martinfowler.com/bliki/SpecificationByExample.html) or [Test-Driven Development](http://c2.com/cgi/wiki?TestDrivenDevelopment).

**KSEG 1.6.** **Every software artifact MUST be developed using design techniques that favor its reuse.**  
By definition, a software artifact must be a reusable piece of software, and to allow for this property, the development of the software artifact must take it into consideration the whole time.  
Following principles and patterns such as [GRASP](https://en.wikipedia.org/wiki/GRASP_%28object-oriented_design%29) and [SOLID](https://en.wikipedia.org/wiki/SOLID_(object-oriented_design)), especially the Information Expert and SRP principles, is essential for a good degree of reusability.

**KSEG 1.7.** **Every software artifact MUST be registered in a continuous integration tool.**  
Continuous integration tools integrate the changes made by different developers into potentially shippable products. During this process, automated tests are executed and feedback reports are generated.  
The existence of test execution and feedback reports after every build allows the development team to become aware of most problems that may affect that build earlier.

**KSEG 1.8.** **Every software artifact MUST be registered in a source code quality analysis tool.**  
Source code analysis tools scan the source code, searching for potential flaws, bad practices, vulnerabilities, unnecessary complexity, duplicated code, lack of appropriate test coverage, and many other metrics that help developers keep the source code at a good quality standard and build better software products.

**KSEG 1.9.** **Every software artifact MUST be registered in a continuous deployment tool.**  
Continuous deployment tools allow new versions of software artifacts to be automatically published once approved by the integration process.  
Using these tools allows developers to focus on development work and deploy as often as necessary.

**KSEG 1.10.** **Every software artifact MUST adhere to a consistent versioning scheme.**  
Versioning schemes like [SemVer](http://semver.org) allow consumers of a software artifact to have predictability about how the changes in a new version will affect their software. Regardless of the selected scheme, a consistent one must be used, and the rules about how it works must be made explicit in the software artifact documentation.

**KSEG 1.11.** **Every software artifact MUST be registered in a reuse management tool.**  
Reuse management tools, or package distribution tools, allow consumers of a software artifact to have a small set or a single source for the consumption of the software artifact files they depend on.  
These tools must be used not only for open source software artifacts but also for software artifacts developed inside the organization.  
Tools like NuGet, Maven, and NPM are standard package distribution tools for their respective platforms.

**KSEG 1.12.** **Every software artifact MUST consume other software artifacts only through reuse management tools.**  
It is important that the minimum number of package sources be used for consuming dependencies in a software artifact. If a new software developer in the team needs to know specific details about how to consume specific packages, chances are he or she will eventually make a mistake. Using a single or small set of package sources, through a reuse management tool, helps mitigate this risk.

**KSEG 1.13.** **Every software artifact MUST have license terms.**  
Since software artifacts are intended to be reused, either internally within the organization or publicly as open source projects, there must be license terms defining how these artifacts can be reused.  
In some cases, reuse will be allowed only internally to the organization. Other times, reuse will not be allowed at all. In any case, it is always necessary to have the license terms explicitly stated in the software artifact documentation.  
For open source projects, information about the most common license terms can be found at [http://opensource.org/licenses](http://opensource.org/licenses).

**KSEG 1.14.** **Relevant software artifacts MAY have their evolution published on management boards.**  
The owner of a software artifact may decide to publish its evolution on a management board. For small software artifacts, this is often not needed, but for large ones it might be necessary.

## KSEG 2. Guidelines for development of Software Systems

**KSEG 2.1.** **All guidelines applicable to software artifacts MUST also be applicable to software systems.**  
Every software system is also a software artifact. The difference is that it can be used directly by an end user and not only by other developers.

**KSEG 2.2.** **Every software system MUST have its development or extension managed by a software project.**  
A software project will define the requirements, specifications, plans, and how the software system must be developed or extended to fulfill customer needs.

**KSEG 2.3.** **Every software system MUST have its requirements validated by a software quality assurance team.**  
Unlike software artifacts, which are parts of a software system and are directly used only by other software developers, software systems are directly used by customers. Therefore, every software system needs to be tested by a software quality assurance team, in order to avoid having its problems identified by the customer only after deployment.

**KSEG 2.4.** **Every software system MUST publish its evolution on a management board.**  
At every moment, all stakeholders, including the development team, must have access to the current state of the software system development. Therefore, a management board for every software system is necessary.

## KSEG 3. Guidelines for management of Software Projects

**KSEG 3.1.** **Every software project MUST be supervised by a Project Management Office.**  
A Project Management Office is a division of the organization that governs the development of software projects, and it shall be responsible for the supervision of every software project in execution.

**KSEG 3.2.** **Every software project MUST have a Project Manager.**  
While every software artifact or system must always have an owner, a software project must have a Project Manager, who will be responsible for the management of the project and the delivery of the defined scope within cost and time, as well as for managing the development team accordingly.  
It is important to emphasize that the role of the Project Manager must not be confused with the role of the Technical Leader.

**KSEG 3.3.** **Every software project MUST have a Technical Leader.**  
Even though the Project Manager is the main person responsible for the software project, technical decisions and the management of the development team will often not be among his or her qualifications. In these cases, the presence of an experienced professional, capable of addressing technical and interpersonal issues and acting as Technical Leader, will help the Project Manager lead the team to its best performance and produce better software systems.

**KSEG 3.4.** **Every software project MUST have a kickoff meeting.**  
In a kickoff meeting, all relevant known details about the software should be presented and discussed with the development team. That allows everyone to start the project moving in the same and right direction.

**KSEG 3.5.** **Every software project MUST balance agility and discipline.**  
Agility does not necessarily lead to good software if the situation does not favor agile methodologies. It is important to know which agile and traditional practices best fit the needs of the project and how to reconcile and apply them accordingly.

**KSEG 3.6.** **Every software project MUST have a wiki page.**  
As with every software artifact and software system, every software project must have a wiki page to record its details and allow stakeholders to have a quick view of them when needed.

**KSEG 3.7.** **Every software project MUST have its backlog maintained.**  
Every software artifact and software system will have its own backlog, even when they are built by a specific software project. A software project ends, but the software artifacts and software systems it produced continue evolving, and other software projects may be created to manage such evolution. That is why it is important to also have a software project backlog, summarizing the high-level issues that are pertinent to the project itself.

**KSEG 3.8.** **Every software project MUST publish its evolution on a management board.**  
While software artifact and software system management boards detail their features and evolution, project management boards focus on the ongoing status of the project. In the same way that wiki pages and backlogs for projects must be separated from artifacts and systems, the project management board shall also be independent.

**KSEG 3.9.** **Every software project MUST register and keep its scope, due dates, and requirements updated and available to the development team during the entire project.**  
It is common for some development teams to lose the big picture and the right focus during the implementation of a software system, even when using an iterative process. Keeping the scope, due dates, and requirements updated on the management board and revisiting them during the evolution of the project helps mitigate this risk.

**KSEG 3.10.** **Every software project MUST perform frequent short meetings.**  
These meetings might be daily, weekly, or follow any other cadence, but they need to be frequent enough to allow the team to stay constantly aware of what any other team member is doing. In these meetings, all team members must share what they did since the last meeting, what they will do until the next one, and what others can do to help them. This not only improves awareness but also helps each team member focus on the work they are doing.

**KSEG 3.11.** **Every software project MUST have its development performed in an iterative way.**  
Iterative processes are based on constant feedback and adaptive evolution. Agile methodologies have proven that this behavior can lead to better software.  
Even though in some cases fully agile processes are not the best choice for certain projects, an iterative approach during project execution can always be helpful.

**KSEG 3.12.** **Every software project MUST perform partial deliveries to the software quality assurance team.**  
The software quality assurance team is responsible for verifying whether the software system developed by the project presents the expected quality and fulfills the project specifications. To enable that team to perform its work, it is important that they receive frequent updates of the software system as it is implemented, avoiding having their tests lose value due to being executed on outdated software versions.

**KSEG 3.13.** **Every software project MUST perform partial deliveries to the customer.**  
A long-lasting software project with little or no feedback from the customer has a high risk of delivering a system that does not meet customer expectations, even if it fulfills its formal specifications. Customers only know for sure if the software will add value to their business after they use it. So it is important that, as soon as the software is validated by the software quality assurance team, it be delivered to the customer to evaluate or even use it in production.

**KSEG 3.14.** **Every software project MUST have a closing celebration.**  
Software development teams tend to be passionate about their work, and recognition of their success through money only is usually not enough. It is important, at the end of every software project, to hold a celebration of the work done and thank every person involved for their dedication and good job.  
Sometimes it is also necessary just to make clear that the project is indeed done, and is not being perpetually extended or something like that.

## Final considerations

Different methodologies, practices, techniques, and technologies may be used to follow the guidelines in this article. That allows the team to have the flexibility they need and still work in an organized manner.

And as expected for any open source project, this set of guidelines may change at any time, and feedback from the community is well appreciated.

## License

Creative Commons - CC0 1.0 Universal

## About

Version: 1.2.0

GitHub Project: [KSEG](https://github.com/rafaelromao/KSEG)

Authored by [Rafael Romão](https://github.com/rafaelromao/) in August 2015