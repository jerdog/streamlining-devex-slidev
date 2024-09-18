---
titleTemplate: "%s - Slidev"
theme: slidev-theme-the-unnamed
title: "Streamlining DevEx: The Power of CI/CD Standardization and Interoperability"
author: "Jeremy Meiss"
info: |
  ## Streamlining DevEx 
  The Power of CI/CD Standardization and Interoperability

  ## Abstract
  In this talk, we delve into the core aspects of CI/CD which can significantly impact Developer Experience: Pipeline Standardization and Interoperability. We'll explore the pivotal role of standardized practices in CI/CD pipelines, fostering consistency and reducing friction in the development lifecycle. We will also look at how well-defined pipeline architecture and standardized configurations, can empower developers with a smoother and more efficient workflow.
  
  We will also discuss the critical importance of interoperability in CI/CD systems. Enabling seamless collaboration across the diverse toolsets and environments that exist today is a core advantage of interoperability. This enhancing flexibility, and allows teams to leverage their preferred tools without compromising the overall development pipeline.
conference: "devopsdays portugal 2024"
keywords: devex,developer experience,devops,ci/cd
presenter: true
download: true
exportFilename: dodporto2024-streamline-devex-slidevExport
export:
  format: pdf
  timeout: 30000
  dark: false
  withClicks: false
  withToc: false
remoteAssets: true
selectable: true
record: true
wakeLock: build
colorSchema: auto
aspectRatio: 16/9
favicon: 'https://raw.githubusercontent.com/jerdog/jmeiss-me-website/main/assets/images/fav.png'
fonts:
  sans: Roboto
  serif: Roboto Slab
  mono: Fira Code
drawings:
  persist: false
#class: text-center
# enable MDC Syntax: https://sli.dev/features/mdc
mdc: true
defaults:           # default frontmatter applies to all slides
  layout: center    # https://sli.dev/builtin/layouts#layouts
  transition: fade  # slide transition: https://sli.dev/guide/animations.html#slide-transitions
addons:
  - slidev-addon-rabbit
rabbit:
  slideNum: true
layout: cover
transition: slide-left
---

# Streamlining DevEx

## The Power of CI/CD Standardization and Interoperability

<!--
As a quick note, I used ChatGPT + DALL-E to generate the images in this presentation, which took entirely too much time because the effort to train the model for what I was trying to get was tedious and time consuming.
Over the next few minutes I am going to touch on some core principles and better practices for standardizing CI/CD and ensuring interoperability between systems and practices.
-->

---
layout: image
---

<img src="/images/slides/cncf-landscape.jpg" alt="CNCF Landscape" style="object-fit: contain; width: 100%; height: 100%;" />

<!--
In the rapidly evolving landscape of modern software development, illustrated here by the CNCF landscape (as of January 29, 2024) Continuous Integration and Continuous Deployment (CI/CD) stand as transformative pillars, reshaping how software is delivered and the very experience of those crafting it.
-->

---
layout: intro
---

<div class="multiCol">
    <div class="col">
        <h2 style="color: rgb(111, 168, 220);">Jeremy Meiss</h2>
        <p style="font-weight: bold; font-size: 1em;">Co-Founder, DevEx Consultant</p>
        <p style="font-size: 1em;"><em>DevEx Institute</em></p>
        <!-- <p style="font-size: 0.8em;"><a href="https://devex.institute" target="_blank">https://DevEx.Institute</a></p> -->
        <p>DevOpsDays Kansas City Organizer</p>
    </div>
    <div class="col">
      <img src="/images/profile-pic.jpg" width="60%" alt="Jeremy Meiss" />
    </div>
</div>

---
layout: default
background: "/images/slides/2b-d316afa9-e89f-4bb6-9bca-11f73973a99f.jpeg"
---

# A working definition of DevEx
  
>_"...the **journey** of developers and practitioners as they learn and deploy technology, which if successful, focuses on eliminating obstacles that hinder them from achieving success in their endeavors."_

-**Jessica West**, _Co-Founder, DevEx Institute_

<!--
Let's start with a definition of DevEx - DevEx is the journey of developers as they learn and deploy technology. When successful, it focuses on eliminating obstacles that hinder a developer or practitioner from achieving success in their endeavors.
-->

---
layout: image
# background: "/images/slides/good-devex-overall-satisfaction.jpg"
image: "/images/slides/good-devex-overall-satisfaction.jpg"
---


<!--
It's their overall satisfaction and efficiency while working on software projects. It's the tools, the processes, and the environments that shape their interactions with code, infrastructure, and each other. A positive DevEx is crucial for enhancing productivity as it directly influences how quickly and effectively developers can build, test, and deploy software.
-->

---
layout: image
image: "/images/slides/devex-integral-dev-lifecycle.jpg"
---

<!--
DevEx is such an integral part of the entire development lifecycle - not just if you're developing tools for use internally, choosing off-the-shelf tools to use, or creating products for other developers and companies to use. That means that the ease of use, reliability, how accessible and understandable documentation, how efficient the build processes are, the effectiveness of testing frameworks, and the smoothness of deployment procedures all have an impact on the overall dev experience.
-->

---
layout: image-left
image: "/images/slides/cornell-devex.jpg"
backgroundSize: contain
class: my-cool-content-on-the-right
---

## DevEx isn't new

_REF: F. Fagerholm and J. Münch, "[Developer experience: Concept and definition](https://ieeexplore.ieee.org/document/6225984?arnumber=6225984)," 2012 International Conference on Software and System Process (ICSSP), Zurich, Switzerland, 2012._

<!--
But DevEx isn't a new thing. The first mention of "developer experience" as a concept was in a paper was presented at the June IEEE 2012 International Conference on Software and System Process in Zurich. There are references in the paper going back to 1985 that deal with "programmer performance and the effects of the workplace." A few things stand out in this paper, which is a really great read.
-->

---
layout: image-left
image: /images/slides/cornell-devex.jpg
backgroundSize: contain
class: my-cool-content-on-the-right
---

## DevEx isn't new

>"New ways of working such as globally distributed development or the integration of self-motivated external developers into software ecosystems will require a better and more comprehensive understanding of developers' feelings, perceptions, motivations and identification with their tasks in their respective project environments."

_REF: F. Fagerholm and J. Münch, "[Developer experience: Concept and definition](https://ieeexplore.ieee.org/document/6225984?arnumber=6225984)," 2012 International Conference on Software and System Process (ICSSP), Zurich, Switzerland, 2012._

---
layout: image-left
image: /images/slides/cornell-devex.jpg
backgroundSize: contain
class: my-cool-content-on-the-right
---

## DevEx isn't new

>"...developer experience could be defined as a means for capturing how developers think and feel about their activities within their working environments, with the assumption that an improvement of the developer experience has positive impacts on characteristics such as sustained team and project performance."

_REF: F. Fagerholm and J. Münch, "[Developer experience: Concept and definition](https://ieeexplore.ieee.org/document/6225984?arnumber=6225984)," 2012 International Conference on Software and System Process (ICSSP), Zurich, Switzerland, 2012._

<!--
The second was this line, that DevEx could be a means for capturing how devs think and feel about their activities at work, and that improving their experience impacts things like sustained team and project performance.

So all of this interest in DevEx isn't a new concept - but is largely driven by companies trying to sell you something, from the top down, with very little (if any) focus on developers themselves. We've all been there - we've been told we need to adopt a new way of working, and then had some new tool from some friend on the C-Suite who says that by simply using it, we'll be happier, more productive, and instantly a 10x engineer. Meanwhile, you've used it before and it's shit.
-->

---

## Point of clarification

- "DevEx" by default focuses on "developer"
- View "DevEx" as a whole of the lifecycle
 
<!--
I think it's important to clarify that "DevEx" by default focuses on the "developer", but we should really view DevEx as a whole part of the lifecycle, and not just for developers only. So I'm happy to workshop some new terms for DevEx later on, maybe even in an Open Space.
-->

---
layout: image
image: "/images/slides/4-streamling-workflows.jpeg"
---

<!--
Putting in place a good DevEx that empowers the developers in your organization involves streamlining workflows, reducing friction, and providing intuitive tools so that developers and practitioners can focus on creating high-quality code, fostering innovation, and ultimately contributing to faster and more reliable software delivery. In this talk, we will hone in on two critical pillars: standardization and interoperability.
-->

---
background: "/images/slides/3-ci-cd-influence.jpeg"
backgroundSize: contain
---

# CI/CD

- Standardization
- Interoperability

<!--
If there's one concept that has had a profound influence on DevEx, it's CI/CD. It created a dynamic shift in how developers collaborate, create, and deliver software. By automating integration, testing, and deployment processes, CI/CD accelerates development cycles, empowering developers with faster feedback loops, improved code quality, and the ability to iterate swiftly. We'll talk over the next bit about two ways in which CI/CD can help you achieve DevEx: standardization, and interoperability.
-->

---

## CI/CD Standardization

- consistency to development pipelines
- reduces friction
- enhances collaboration

<!--
CI/CD Standardization aims to minimize variability, reduce errors, and foster an environment where developers can efficiently collaborate. Standardizing your pipelines is a really key part of enhancing DevEx in your org. So let's talk about some of the steps and better practices.]
-->

---
layout: default
---

# Implementing CI/CD Standardization
## Assessment and Analysis

- Thoroughly assess your current CI/CD pipelines
- Identify pain points and bottlenecks
- Analyze specific requirements and constraints

<!--
You can't make informed decisions and implement the necessary changes to processes, tools, or code that are needed for more efficiency without starting with a thorough assessment and analysis of your current pipelines. Understand the current state of your CI/CD pipelines, and get a baseline to work with. That means everything from understanding existing workflows, tools, and processes to identifying pain points, bottlenecks, and areas requiring standardization. **After assessment**, your organization can start setting clear goals and a pathway forward.
-->

---
layout: default
---

# Implementing CI/CD Standardization
## Define Standardization Goals

- Define goals and objectives, align with strategy and objectives
- Determine success, like reduced deployment times / error rates

<!--
You can't set clear goals, without knowing the desired outcome for your organization. That's really the only way to set specific, achievable objectives. A few examples of those would be: improving workflow efficiency, enhancing collaboration, and ensuring consistency across pipelines. But your goals _must_ align with the broader business objectives, which helps prioritize your efforts and drive tangible improvements. Then regularly review your progress and adjust as needed to ensure that you're on track to achieve your goals.
-->

---
layout: default
---

# Implementing CI/CD Standardization
## Select Tools and Practices

- Choose tools & practices aligned with organization needs, goals
- Establish standard templates and configurations for pipelines
- Enforce coding standards for consistency and readability

<!--
When selecting tooling, prioritize compatibility and ease of integration with existing systems and align with standardized practices. Make sure that you are able to use templating and can standardize your configs so you bring consistency throughout the CI/CD process. Whatever you select must be aligned with your organization’s specific requirements and objectives, and the templates and patterns you base your standardization efforts on must be consistent and reliable across all of your projects, but also flexible enough to adapt to project-specific requirements. Easy, right?
-->

---
layout: default
---

# Implementing CI/CD Standardization
## Utilize Version Control

- Store pipeline configs as code in version control systems
- Implement branching and pull request strategies

<!--
- Store CI/CD pipeline configurations as code in version control systems (e.g., Git). This practice ensures that configurations are versioned, traceable, and easily revertible.
- Implement branching and pull request strategies to manage changes to CI/CD configurations.
-->

---
layout: default
---

# Implementing CI/CD Standardization
## Automated Testing and Validation

- Integrate automated testing and validation into templates
- Implement code reviews and peer validation early in dev process

<!--
- Integrate automated testing and validation into the pipeline templates to ensure that standardized configurations produce expected results.
- Implement code reviews and peer validation to catch configuration errors early in the development process.
-->

---
layout: default
---

# Implementing CI/CD Standardization
## Documentation and Training

- Create comprehensive docs for processes, configs, best practices
- Provide training to ensure understanding and effective use

<!--
- Create comprehensive documentation that outlines the standardized CI/CD processes, including workflows, configurations, and best practices.
- Provide training sessions for development teams to ensure they understand and can effectively use the standardized CI/CD pipeline templates.
-->

---
background: "/images/slides/optimizing-cicd-standardization.jpg"
backgroundSize: contain
---

# Optimizing CI/CD Standardization

<!--
Once you’ve ensured the core practices are in place, it’s time to look at some key, optimized practices that can help you take the next step in your standardization efforts.
-->

---
background: "/images/slides/14-monitoring-and-improvement.jpeg"
backgroundSize: contain
---

# Optimizing CI/CD Standardization
## Continuous Monitoring & Improvement

- Detect pipeline issues and bottlenecks in real-time
- Establish culture of regular reviews and updating pipelines

<!--
- Set up monitoring and alerting for your CI/CD pipelines to detect issues and bottlenecks in real-time.
- Establish a culture of continuous improvement by regularly reviewing and updating standardized pipelines based on feedback and evolving project requirements.
-->

---
background: "/images/slides/15-governance-compliance.jpeg"
backgroundSize: contain
---

# Optimizing CI/CD Standardization
## Governance & Compliance

- Implement governance policies to enforce pipeline standards
- Validate compliance with industry regulations / internal standards
- Regularly audit and assess adherence to standardized practices

<!--
- Implement governance policies to enforce pipeline standardization and compliance with industry regulations or internal standards.
- Regularly audit and assess the adherence to standardized practices.
-->

---
background: "/images/slides/16-scaling-adaptation.jpeg"
backgroundSize: contain
---

# Optimizing CI/CD Standardization
## Scaling & Adaptation

- Ensure standardized templates can scale and adapt
- Maintain flexibility to accommodate unique project requirements

<!--
- Ensure that the standardized pipeline templates can scale and adapt to different project types, sizes, and technologies.
- Maintain flexibility to accommodate unique project requirements while adhering to standardized core practices.
-->

---
background: "/images/slides/17-feedback-collaboration.jpeg"
backgroundSize: contain
---

# Optimizing CI/CD Standardization
## Feedback Loop & Collaboration

- Foster collaborative environments where feedback & contributions encouraged
- Continuously communicate benefits of standardized pipelines & celebrate successes

<!--
- Foster a collaborative environment where developers can provide feedback and contribute to improving CI/CD standardization practices.
- Continuously communicate the benefits of standardized pipelines and celebrate successes.
-->

---
layout: image
image: "/images/slides/pipeline-standards-just-the-beginning.jpg"
---

<!--
Implementing these better practices will help you improve your CI/CD pipeline and the overall Developer Experience and quality of your software delivery process. However, it’s not the finish line. Let's talk about the role interoperability plays in your CI/CD systems.
-->

---

## CI/CD Interoperability

- seamless integration across diverse toolsets
- fosters flexibility in development environments

<!--
Interoperable systems refers to the ability of different tools, technologies, and components within a CI/CD ecosystem to work seamlessly together. It ensures that your various pipeline parts, including source code repositories, build systems, testing frameworks, deployment platforms, and monitoring tools, can communicate, integrate, and exchange data effectively without compatibility issues or disruptions.

-->

---
background: "/images/slides/24-achieving-standards.jpeg"
backgroundSize: contain
---

# Interoperability in CI/CD Systems
## Streamlined workflows

- Reduce manual intervention, increase automation with templates + reusable config
- Eliminate waste and improve efficiency
- Deliver faster with higher quality + better developer experience

<!--
Streamlined workflows in CI/CD systems refers to the efficient and optimized processes that enable the continuous integration, delivery, and deployment of software applications. It's about minimizing manual effort by automating repetitive tasks like building, testing, and deploying applications, speeding up software delivery cycles. Reduce development overhead by removing unnecessary steps and redundant processes, freeing developers to focus on core activities and maximize productivity. Streamlined workflows lead to faster software delivery, improved product quality through automation, and a better developer experience due to smoother workflows and less manual intervention.
-->

---
background: "/images/slides/29-interoperability-collab.jpeg"
backgroundSize: contain
---

# Interoperability in CI/CD Systems
## Cross-functional collaboration

- Have shared goals and break down silos
- Improve resource utilization and efficiency
- Leverage strengths and expertise of each team

<!--
Cross-functional collaboration becomes necessary to drive innovation, efficiency, and customer value through your CI/CD systems, especially when you have varying tool preferences or use different systems between departments. Reduce miscommunication by fostering a shared understanding of project goals across Development, Operations, QA, and other teams, allowing everyone to work towards the same objectives. Share knowledge, tools, and infrastructure to optimize your resource allocation, maximize productivity, and reduces delays. Leverage the diverse strengths and expertise of each team, and foster innovation, improve your problem-solving, and ultimately deliver high-quality software products.
-->

---
background: "/images/slides/34-interop-flexibility.jpeg"
backgroundSize: contain
---

# Interoperability in CI/CD Systems
## Flexibility and adaptability

- Respond quickly to rapid change by adjusting workflows, add new tools, adopt new practices
- Experiment and innovate quickly by leveraging new tools and technologies
- Increase efficiency by leveraging existing resources and tools

<!--
Prioritizing flexibility and adaptability allows organizations to integrate with diverse toolsets and accommodate varying development needs. By bridging gaps between different technologies and systems you can create central hubs that connect other parts and enhance the flexibility of CI/CD pipelines and developer workflows, ultimately promoting a more efficient and collaborative development environment and experience. Backstage is a perfect example of this.
-->

---
layout: image
image: "/images/slides/interop-advanced-mode.jpg"
---

<!--
Once you have adopted the above practices or already have them, the following can help you reach “Advanced Mode,” taking your organization to another level within the DevEx world and can continue advancing across several aspects.
-->

---
background: "/images/slides/ecosystem-integration.jpg"
backgroundSize: contain
---

# Advanced Interoperabilty
## Ecosystem integration

- Assemble customized toolchain tailored to your requirements
- Minimize manual intervention via End-to-end automation
- Greater visibility + traceability via aggregation of info

<!--
Ecosystem integration in CI/CD systems involves seamlessly incorporating and interacting with various tools, services, and platforms within the software development and delivery ecosystem. From VCS, build automation, testing frameworks, deployment platforms, and observability, integration allows for assembling a customized toolchain that's tailored to your specific needs. Add in the ability to automate end-to-end processes, and you can create a more efficient and collaborative development environment and experience, and then aggregate all the information into a single view for greater visibility.
-->

---
background: "/images/slides/ecosystem-open-source-community.jpg"
backgroundSize: contain
---

# Advanced Interoperabilty
## Ecosystem integration
### Role of community and Open Source

- Address potential interoperabilty challenges (case studies, submitting fixes)
- Create external community around your tools, gathering feedback directly

<!--
Participation in the broader ecosystem, like communities, open source projects, forums, and professional groups centered around the tools you use, vastly enriches DevEx for your company. It offers developers a chance to contribute to larger projects, learn from peers outside their organization, and stay abreast of industry trends and better practices. Encouraging this helps get ahead of potential challenges by upping your collaboration and raising awareness. Create an external community to help external users give feedback and contribute to your company's success and DevEx.
-->

---
background: "/images/slides/troubleshooting-debugging.jpg"
backgroundSize: contain
---

# Advanced Interoperabilty
## Troubleshooting and debugging

- Identify and resolve issues early
- Proactive problem solving with data and automation
- Faster resolution and improved reliability

<!--
Two crucial components of CI/CD systems are **troubleshooting** and **debugging**, both ensuring the smooth operation and reliability of your pipelines. Effectively implementing them requires comprehensive monitoring and logging capabilities throughout the CI/CD pipeline with each stage instrumented to capture valuable data and insights. Automation also plays a pivotal role in streamlining troubleshooting and debugging processes by integrating testing, validation, and verification steps into the pipeline. Be proactive to minimize manual effort, accelerate issue resolution, and enhance overall reliability.
-->

---
background: "/images/slides/cross-platform-deployments.jpg"
backgroundSize: contain
---

# Advanced Interoperabilty
## Cross-platform deployment

- Provide uniform approach for diverse platforms
- Reduced complexity and increased efficiency
- Broader reach and greater impact

<!--
Cross-platform deployment offers a single method to package and deliver applications across various platforms (operating systems, cloud services, etc.). This simplifies CI/CD pipelines by removing the need for platform-specific deployment configurations. By abstracting platform complexities, cross-platform deployment reduces overhead in managing deployments. This saves time and effort, improves consistency, and leads to more reliable deployments. Cross-platform deployment allows applications to reach wider audiences on desktops, mobile devices, and cloud environments. This maximizes software accessibility, marketability, and competitiveness, ultimately driving business growth.
-->

---
layout: image
image: "/images/slides/30-interop-bridge.jpeg"
---

<!--
In essence, implementing CI/CD interoperability acts as a bridge, connecting different parts of the development and delivery process, fostering collaboration, and ensuring that teams can work cohesively and efficiently, even when using diverse toolsets and technologies. This flexibility and adaptability is essential for modern software development, where agility and collaboration are paramount.
-->

---

## CI/CD Interoperability Challenges...
### ...and Remedies

| Challenges                                | Remedy                                                                 |
|-------------------------------------------|------------------------------------------------------------------------|
| Diverse Toolsets & Ecosystems             | _Prioritize critical dependendencies, objectives_                        |
| Data formats and schema differences       | _Implement unified data formats_                                         |
| Authentication and Authorization          | _Standardize methods, integrate governance_                              |
| Versioning and compatibility testing      | _Clear versioning policies, regular compatibility testing_               |
| Lack of documentation                     | _Prioritize efforts + allocate resources, implement standards + process_ |

<!--
Implementing interoperability between your various systems and CI/CD pipelines is essential, but not without its challenges, nor remedies.
-->

---
layout: image
image: "/images/slides/37-efficiences.jpeg"
backgroundSize: contain
---

<!--
By applying these strategies and tips, organizations can overcome the common interoperability challenges and establish robust connections between Spinnaker, Backstage, and other CI/CD tools, fostering a more seamless and integrated development ecosystem.The efficiencies gained by making sure you're using tools that provide CI/CD standardization as well as being interoperable between all of the systems your developers are using is at the core of what Developer Experience really is about…
-->

---

# DevEx reflects an organization's values

<Tweet id="1750563607266410692" />

<!--
The level of investment that a company invests in DevEx can be a reflection of a company's values towards its employees, especially its developers. A strong focus on DevEx shows a commitment to employee well-being and efficiency. And prioritizing DevEx helps foster a culture of excellence and innovation. When developers are provided with the right tools, support, and environment, they are more likely to produce high-quality work and push the boundaries of what's possible.
-->

---
layout: default
---

# DevEx is...

> ### ...ruthlessly eliminating the barriers (and blockers) that keep your developers (and practitioners) from being successful

_-**Me**_

<!--
I'll leave you with this that, that DevEx is ruthlessly eliminating barriers (and blockers) that keep your developers (and practitioners) from being successful.
-->

---

<div class="multiCol">
    <div class="col" style="text-align: center;">
        <h2 style="color: #04aa51; text-shadow: none;">Thank You.</h2>
    </div>
    <div class="col" align="center">&nbsp;</div>
    <div class="col" align="left" style="font-size: .5em;">
        <p style="font-size: 1rem;"><img src="/images/linkedin.png" style="vertical-align: middle; display: inline; margin: 5px; max-height:50px;">/in/jeremymeiss</p>
        <p style="font-size: 1rem;"><img src="/images/twitter.png" style="vertical-align: middle; display: inline; margin: 5px; max-height:50px;">@IAmJerdog</p>
        <p style="font-size: 1rem;"><img src="/images/devto.png" style="vertical-align: middle; display: inline; margin: 5px; max-height:50px;">@jerdog</p>
        <p style="font-size: 1rem;"><img src="/images/mastodon.png" style="vertical-align: middle; display: inline; margin: 5px; max-height:50px;">@jerdog@hachyderm.io</p>
    </div>
</div>


<!--

-->

---
layout: end
---

<!--

-->

