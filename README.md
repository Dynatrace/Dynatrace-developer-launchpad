
# Developer Launchpads
This repository collects templates and examples for Launchpads and Segments tailored to the needs of developers using Dynatrace.

## Goal
Development teams need observability insights on the applications and services they build and own and how these services perform from pre-production to production. As Dynatrace has a vast variety of features, you need to tailor start pages to the needs of individual teams, ideally based on a template. Basically, you need to show them “Their Stuff”. The following provides a framework for your central platform engineering team to create Developer Launchpads (see example), that offer departmental development teams a starting point to crucial apps and data, and to guide them through their most important use cases, both on and off the Dynatrace Platform. 

## License
Apache License v2.0. https://github.com/Dynatrace/Dynatrace-workflow-samples/blob/main/LICENSE

## Value and Benefits 

### Value of Launchpads for Development Teams
* **Streamlined Onboarding** Simplifies the onboarding process for new users by providing a clear starting point.
* **Increased Efficiency** Reduces the time spent navigating through Dynatrace, allowing users to focus on critical tasks.
* **Customization** Tailors the user experience to specific roles, teams, or processes, enhancing relevance and usability.
* **Consistency** Ensures a consistent approach to observability across different teams and projects.
* **Scalability** Supports the scalable rollout of Dynatrace across large organizations by providing structured and easy-to-follow start pages.

### Benefits for the Central Team
* **Centralized Control** Allows the central team to manage and standardize the observability experience across the organization.
* **Improved Communication** Facilitates better communication of best practices and guidelines through curated start pages.
* **Resource Optimization** Saves time and resources by reducing the need for repetitive training and support.
* **Enhanced Adoption** Encourages wider adoption of Dynatrace by making it more accessible and user-friendly for different teams.
* **Feedback Loop** Provides a mechanism for collecting user feedback and continuously improving the observability setup.

## Launchpad Sections
The Developer Launchpad should be a landing page or centralized hub on the Dynatrace Platform designed to provide developers with all the information on tools, processes, and resources they need to efficiently build, deploy, and monitor their applications. 
Focus the content on apps and services of development teams and responsibilities such as debugging and troubleshooting, understanding and optimization of runtime behavior, optimizing end user experiences and business outcomes, ensure high-quality and secure releases, resolve security incidents, or how to collaborate with central teams

![alt text](image.png)
*Figure: Example Launchpad for a Development Team*

This Example Launchpad is structured into the following sections:
* **Dynatrace Key Apps** Highlight the most critical Dynatrace apps that developers frequently need. Essential tools and apps that developers will most likely need, such as Metrics, Logs, Dashboards, Distributed Tracing, Profiling, or a Live Debugger.
* **Essential Dashboards** Collect dashboards that can act as starting points for developers in a team, either parametrized ready-made dashboards or customized dashboards.
* **Developer Tools and Platforms** List integrations with other tools and platforms that developers use, such as Git repositories, CI/CD tools, and issue trackers.
* **Developer Documentation and Resources** Provide quick access to relevant documentation, coding standards, best practices, quick-start tutorials, sample projects, templates, and other resources to help developers troubleshoot and optimize their workflows. Include links to Dynatrace developer documentation and API guides. 

Additional sections to add immediated value for developers:
* **Team Collaboration** Include links to collaboration tools and channels, such as specific channels in Slack, Microsoft Teams, or project management boards, to facilitate communication within the team.
* **Internal Support and Service** Links to relevant internal services and support, for instance how to get access permissions to dashboards or data, request a tool, get access permissions to other platforms, and so on. Add community forums and internal support channels. 
* **Onboarding and Learning** Offer resources and guides to help new developers get up to speed quickly and continue learning. This might include developer-specific content on learning platforms like Dynatrace University, Coursera, Udemy, or Pluralsight.
* **Feedback and Improvement** How to provide feedback on the launchpad and suggest improvements, ensuring it evolves to meet developer needs.
* **Developer Use Cases** Group content according to frequent use cases for developers in our context, such as  Understanding and Diagnosing  Code Execution, Diagnostics of Optimization and Runtime behavior, Frontend/User Analytics, Developer Security
* **Other Launchpads** You might want to set up a hierarchical Launchpad landscape, and refer to related product domains in developer launchpads.


## How to set up a Developer Launchpad



### Launchpad Custom Links 
In order to provide fast access to data for Development teams a leverage custom links in Launchpads by parameterizing them with suitable filters. 

![alt text](image-1.png)´
*Figure: Configuring Parameters of the Ready-made Kubernetes Dashboard*

![alt text](image-2.png)
*Figure: Adding a custom link to a Ready-made Kubernetes Dashboard*

### Manage and control Data Access with Segments
One crucial element to create a launchpad that is focused on apps and services owned by a development team, to show them only “their stuff”, are Segments. Segments enable you to manage access to specific view on available observability data and ensure that users can only view and analyze data relevant to them while protecting sensitive information. Before continuing make sure to understand how to include data into segments and how to use variables.
Specific use cases in the Dynatrace documentation explain how to configure a segment, e.g., for specific buckets or for signals and monitored entities related to specific Kubernetes clusters in a common stack. However, these segments contain too much information for developers who want to observe their particular apps and services. 
Example: Configuration of a Segment for a Development Team
The following example shows the configuration of an observability data segment that includes signals originating from multiple Kubernetes clusters (dtp-dev-*). It filters observability information (logs, events, metrics) for a service slo-service including related entitities process group, request and host, as well as log entries created by the app dynatrace.service.level.objectives, and events created by processes in the process group slo*. 
 
Figure: Segment Configuration for the SLO team
Example: Define a Segment for a specific App 
The following example shows the configuration of a segment for events, logs, spans and metrics related to the App dynatrace.site.reliability.guardian. 
 Figure: Segment Configuration for the Site Reliability Guardian team
Access Control and Permissions
For a seamless Launchpad experience and to reduce support efforts it is of utter importance to have roles, groups, and access permissions for all included referenced items in place. Make sure that developers know how to get support if they don’t have access or no data is displayed.
•	Segment visibility: The visibility settings of a segment determines who sees it in their list of segments, which is either unlisted or anyone in the environment. 

 
Figure: Segment Visibility Configuration
	
Unlisted segments can still be made available to others by being referenced in apps, such as in shared notebooks and dashboards. Everyone has read-only access to all segments.

Regardless of configured visibility, any segment can be accessed with storage:filter-segments:read permission. This guarantees that even unlisted segments that may be referenced in a shared notebook, can be used by anyone having access to that notebook.

* **Data in Segments** Segments themselves don't contain any data. All queries, with or without segments, always respect data access permissions enforced by IAM policies.
* **Basic access control**concepts: Users must be able to access apps and tools, as well as have visibility into data in referenced Notebooks or Dashboards, and other information they need while maintaining security and control.
* **Dashboard Access** Ensure developers have access to referenced dashboards, including duplication, downloading, uploading, or sharing dashboards. 
* **App-specific Permissions** Control access to referenced Dynatrace apps, ensuring that developers can utilize referenced applications they need. This includes setting up rules to allow or deny access based on user roles. You can use app-specific permissions to control who can access and run specific apps.
* **Developer Tool Access** This includes access permissions for integrated tools and platforms, such as Git repositories, CI/CD tools, and issue trackers, ensuring that users can seamlessly interact with these resources. 
* **Collaboration Tools Access** This involves permissions for collaboration tools and channels, like Slack or Microsoft Teams, to facilitate communication and teamwork. 
* **Documentation, Onboarding and Training** Ensure that developers have access to essential documentation and training platforms. This will allow them to easily find and utilize the information they need and consume training in a self-service fashion. 
