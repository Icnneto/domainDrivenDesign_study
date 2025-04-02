# Domain-Driven Design

This repository provides a structured overview of **Domain-Driven Design (DDD)**, from fundamental concepts to more advanced topics. 
The goal is to create a concise and practical personal reference, and also to help others developers to understand and apply DDD principles effectively.

# Table of contents
1. [Introduction](#introduction)
2. [Domains and Subdomains](#paragraph1)

<a name="introduction"></a>
## Introduction to DDD
Domain-Driven Design (DDD) is a software development philosophy that emphasizes the importance of understanding and modeling the business domain. 
It is a strategy aimed at improving the quality of software by aligning it more closely with the business needs it serves.

First introduced by `Eric Evans in his 2003 book "Domain-Driven Design: Tackling Complexity in the Heart of Software"`, 
DDD provides a collection of principles and patterns that help developers craft elegant object systems. 
At its core, DDD navigates complexity by focusing software development on the 'domain'—the specific business context within which the software operates.

A key concept in DDD is the 'ubiquitous language'—a common language shared by both developers and business stakeholders. 
This shared vocabulary ensures that software accurately reflects the business domain it serves, effectively closing the gap between business reality and code.

When properly applied, DDD leads to software abstractions called domain models that encapsulate complex business logic. 
These models serve as a bridge between technical implementation and business requirements, resulting in systems that are not only technically sound but also meaningful from a business perspective.

<a name="paragraph1"></a>
## Domains and Subdomains - What are they?

### Domains
In Domain-Driven Design (DDD), the domain represents the sphere of knowledge, influence, or activity around which the application is built. It's not just the business core, but encompasses the problems the business is trying to solve, the specialized knowledge the business has developed, and the language experts use when discussing these problems.

"In Domain-Driven Design, the 'domain' represents the specific business problem space and associated knowledge that the software aims to address. It encapsulates the core business concepts, rules, processes, and relationships that define the organization's area of expertise. The domain is the 'why' behind the software's existence and provides the shared language (ubiquitous language) that connects technical implementation to business reality. Without a clear understanding of the domain, software risks becoming disconnected from the actual business needs it intends to serve."

Key aspects that strengthen this definition:

The domain includes both the problem space and the specialized knowledge
- It emphasizes that domain knowledge exists independently of software
- It highlights the importance of the ubiquitous language that bridges technical and business concerns
- It acknowledges that the domain provides context and meaning for all technical decisions

### Subdomains
Subdomains are logical partitions of your overall domain. They represent different business capabilities or concerns within your organization. 

Each subdomain:
- Has its own specialized language and concepts
- Addresses a specific aspect of the business
- Can often be assigned to a dedicated team
- May have different strategic importance to the business

#### 1. Core Subdomains
Core subdomains **represent the business's competitive advantage and strategic differentiators**.

**Characteristics**:
- Directly related to the organization's primary business function
- Create unique value and set the business apart from competitors
- Require significant domain expertise
- Usually demand custom development and substantial investment
- Most critical to business success

**Example**: For Netflix the `videos and algorithms recommendation`, and for DHL, the `logistics and package tracking systems.`

#### 2. Supporting Subdomains
Supporting subdomains are necessary for the business to function but don't provide competitive advantage by themselves.

**Characteristics**:
- Tailored to the specific business's needs
- Necessary for core subdomains to operate effectively
- Require some domain knowledge and customization
- Important but not as critical as core subdomains

**Example**: For Netflix might be `content licensing management and user profile management` - those are necessary but not a primary differentiator.

#### 3. Generic Subdomains
Generic subdomains are necessary business functions that don't differ significantly across companies in the industry.

**Characteristics**:
- Common across many businesses
- Don't require specialized knowledge specific to your business
- Can often be satisfied with off-the-shelf solutions or outsourcing
- Necessary but provide little competitive advantage

**Example**: For Netflix might include `billing systems, authentication.`

## Domain Storytelling
Domain Storytelling is a collaborative approach to understanding business domains. 
At its core, it recognizes that every domain has its own journey, and there's no better way to understand what needs to be done than by telling the story of what happens within that domain.

This method brings together people with various levels of knowledge to share their perspectives in a single document, providing a clear view of current processes and the boundaries of our story. 
It helps us visualize how different stakeholders with different viewpoints work together to create a cohesive and fluid narrative of how everything functions.

Domain Storytelling is particularly valuable because it:
- Creates a shared understanding between business and technical teams
- Makes domain knowledge explicit through visual storytelling
- Helps identify domain boundaries and relationships
- Builds a common language between stakeholders
- Provides context for software design decisions

This collaborative technique is essential for designing software that truly addresses business needs, as it ensures we understand the domain before implementing solutions.

### ROLES
### 1. Actors
An actor in Domain Storytelling may be a person, a group of people, an organization, a system, or even a physical object that participates in the domain activities.

Domain stories are designed through the lens of these defined actors, presenting the narrative we (as developers or consultants) want to understand. These actors perform activities, exchange information, and interact with work objects to accomplish domain goals.

It's important that actors are named after their roles or functions (e.g., 'Customer', 'Warehouse Manager', 'Payment System') rather than using personal names. This abstraction ensures the story focuses on responsibilities and relationships within the domain rather than specific individuals, making the model more broadly applicable and highlighting the organizational structure of the processes.

### 2. Work Objects
Work Objects in Domain Storytelling represent the items that actors work with or exchange during domain activities. These can include physical objects (products, equipment), documents (forms, contracts), digital artifacts (files, records), or information (data, messages) that flow through the system.

Actors interact with Work Objects by creating, modifying, transferring, or consuming them, and these interactions form the essential building blocks of our domain narrative. Work Objects help visualize what is being acted upon, transferred between actors, or transformed throughout a process.

### 3. Activities
Activities in Domain Storytelling represent the actions that actors perform on or with work objects. They are the verbs in our domain narrative that connect actors to work objects or to other actors.

Activities show what actors do within the domain, such as creating, modifying, transferring, requesting, approving, or analyzing work objects. These actions drive the domain story forward and reveal the sequential flow of processes, decision points, and business rules.

Worth mentioning that, at this point of our application, we do not use if-else conditions or loopbacks. We want our focus to remain on the flow of the storytelling. This approach keeps the narrative clear and accessible, prioritizing the understanding of the main process before introducing complexity through conditional paths or iterations.

### 4. Sequential Numbers
To be truly good, every story needs not only a good script, but also to have a logical sequence. In Domain Storytelling, we have Sequential Numbers that guide us through the story.

### 5. Notes
In Domains Storytelling we take notes to document important informations, such as limitations in certain activity, actions that should be taken, processes or events triggers.

### 6. Groups
Groups represent a part (or slice) of the storytelling that shares the same attributes or characteristics.

For example, they can be defined by repetitive actions, subdomains, or process limitations.

### Work Team
Now that we've understood the main roles that exists in the process of implementing a Domain Storytelling, let's move on to the next step: putting it into practice.

We need to assemble a team that will help us with this task. The most important step now is selecting the "right people" to be part of the team—people who are 
connected to the Domain and who will contribute to the story.

A suggested team composition is as follows:
- **Domain Experts**: As many as necessary to tell the story.
- **Listeners**: Everyone willing to learn about the story, usually the development team and some additional stakeholders.
- **Moderator**: The person who will guide the conversations, structuring questions logically and keeping the discussion aligned with the intended goals.
- **Modeler**: The one responsible for creating the story in a pictographic language and making the necessary annotations.

#### References
- **https://redis.io/glossary/domain-driven-design-ddd/**
- **https://medium.com/nick-tune-tech-strategy-blog/domains-subdomain-problem-solution-space-in-ddd-clearly-defined-e0b49c7b586c**





