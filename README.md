# Domain-Driven Design

This repository provides a structured overview of **Domain-Driven Design (DDD)**, from fundamental concepts to more advanced topics. 
The goal is to create a concise and practical personal reference, and also to help others developers to understand and apply DDD principles effectively.

# Table of contents
- [Introduction](#introduction)  
- [Domains and Subdomains](#section1)  
   - [Domains](#section1.1)  
   - [Subdomains](#section1.2)
- [Domain Storytelling](#section2)
   - [Roles](#section2.1)
   - [Work Team](#section2.2)
- [Ubiquitous Language](#section3)
- [Domain Model](#section4)
- [Bounded Context](#section5)
   - [Shared kernel](#section5.1)
   - [Client-Supplier](#section5.2)
- [Tactical Design](#section6)
   - [Architecture](#section6.1)
   - [Value objects](#section6.2)
   - [Entities](#section6.3)
   - [Aggregate](#section6.4)
   - [Domain Services](#section6.5)
- [References](#references)

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

<a name="section1"></a>
## Domains and Subdomains - What are they?

<a name="section1.1"></a>
### Domains
In Domain-Driven Design (DDD), the domain represents the sphere of knowledge, influence, or activity around which the application is built. It's not just the business core, but encompasses the problems the business is trying to solve, the specialized knowledge the business has developed, and the language experts use when discussing these problems.

"In Domain-Driven Design, the 'domain' represents the specific business problem space and associated knowledge that the software aims to address. It encapsulates the core business concepts, rules, processes, and relationships that define the organization's area of expertise. The domain is the 'why' behind the software's existence and provides the shared language (ubiquitous language) that connects technical implementation to business reality. Without a clear understanding of the domain, software risks becoming disconnected from the actual business needs it intends to serve."

Key aspects that strengthen this definition:

The domain includes both the problem space and the specialized knowledge
- It emphasizes that domain knowledge exists independently of software
- It highlights the importance of the ubiquitous language that bridges technical and business concerns
- It acknowledges that the domain provides context and meaning for all technical decisions

<a name="section1.2"></a>
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

<a name="section2"></a>
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

<a name="section2.1"></a>
### Roles
#### 1. Actors
An actor in Domain Storytelling may be a person, a group of people, an organization, a system, or even a physical object that participates in the domain activities.

Domain stories are designed through the lens of these defined actors, presenting the narrative we (as developers or consultants) want to understand. These actors perform activities, exchange information, and interact with work objects to accomplish domain goals.

It's important that actors are named after their roles or functions (e.g., 'Customer', 'Warehouse Manager', 'Payment System') rather than using personal names. This abstraction ensures the story focuses on responsibilities and relationships within the domain rather than specific individuals, making the model more broadly applicable and highlighting the organizational structure of the processes.

#### 2. Work Objects
Work Objects in Domain Storytelling represent the items that actors work with or exchange during domain activities. These can include physical objects (products, equipment), documents (forms, contracts), digital artifacts (files, records), or information (data, messages) that flow through the system.

Actors interact with Work Objects by creating, modifying, transferring, or consuming them, and these interactions form the essential building blocks of our domain narrative. Work Objects help visualize what is being acted upon, transferred between actors, or transformed throughout a process.

#### 3. Activities
Activities in Domain Storytelling represent the actions that actors perform on or with work objects. They are the verbs in our domain narrative that connect actors to work objects or to other actors.

Activities show what actors do within the domain, such as creating, modifying, transferring, requesting, approving, or analyzing work objects. These actions drive the domain story forward and reveal the sequential flow of processes, decision points, and business rules.

Worth mentioning that, at this point of our application, we do not use if-else conditions or loopbacks. We want our focus to remain on the flow of the storytelling. This approach keeps the narrative clear and accessible, prioritizing the understanding of the main process before introducing complexity through conditional paths or iterations.

#### 4. Sequential Numbers
To be truly good, every story needs not only a good script, but also to have a logical sequence. In Domain Storytelling, we have Sequential Numbers that guide us through the story.

#### 5. Notes
In Domains Storytelling we take notes to document important informations, such as limitations in certain activity, actions that should be taken, processes or events triggers.

#### 6. Groups
Groups represent a part (or slice) of the storytelling that shares the same attributes or characteristics.

For example, they can be defined by repetitive actions, subdomains, or process limitations.

<a name="section2.2"></a>
### Work Team
Now that we've understood the main roles that exists in the process of implementing a Domain Storytelling, let's move on to the next step: putting it into practice.

We need to assemble a team that will help us with this task. The most important step now is selecting the "right people" to be part of the team—people who are 
connected to the Domain and who will contribute to the story.

A suggested team composition is as follows:
- **Domain Experts**: As many as necessary to tell the story.
- **Listeners**: Everyone willing to learn about the story, usually the development team and some additional stakeholders.
- **Moderator**: The person who will guide the conversations, structuring questions logically and keeping the discussion aligned with the intended goals.
- **Modeler**: The one responsible for creating the story in a pictographic language and making the necessary annotations.

<a name="section3"></a>
## Ubiquitous Language
Ubiquitous Language is a core concept in Domain-Driven Design (DDD) that serves as a shared language between technical and non-technical team members. It's essentially a carefully crafted, consistent vocabulary that:

- Provides a common language
- Is composed organically as key concepts emerge
- Bridges business requirements and technical implementation
- Breaks down information silos

What makes it special is that this language isn't just for meetings - it literally shapes the code. Class names, method names, and variables in your codebase directly mirror the terms experts use when discussing the domain. This creates a seamless translation between business concepts and technical implementation.

A strong Ubiquitous Language evolves over time through continuous conversation and refinement. When a term becomes ambiguous or inadequate, the team works to clarify it, ensuring the language stays precise and valuable.

>As we progress through project planning and execution, a linguistic divide often arises. Business partners have limited understanding of technical jargon but they use the jargon of their field while expressing requirements. IT partners translate these requirements into a technical design. Some important concepts can become lost in the translation, resulting in vague requirements. As development progresses, the linguistic divide can grow as the technical implementation becomes set in stone. The problem domain begins to lose some of its expressiveness. — Eric Evans, Domain Driven Design

#### 1. Ambiguous Terms
Within a subdomain, we can have the same term with multiple meanings. For example, "policy" could mean a regulatory law or an internal school rule. In Ubiquitous Language, we need a clear definition for each term, so we might decide that "policy" will be used for both meanings, but with clear context.

#### 2. Synonyms Terms
Within a subdomain, we sometimes use a single term to refer to multiple concepts that actually have different details. For example, in IT we often use "login" to refer both to the act of authenticating in a system and to reference the user's account - which are completely different things that we've given the same name for convenience. In Ubiquitous Language, whenever possible, we should break these terms apart and give them unique, specific definitions to avoid future problems

<a name="section4"></a>
## Domain Model
When creating a Domain Model, we're designing an abstraction of a process to solve a specific problem. This documentation is essential for productive conversations with Domain Experts, helping us extract everything needed to understand the problem thoroughly. The Ubiquitous Language we establish is a crucial step in aligning communication between all parties.

The resulting model translates directly into software components—typically as classes with attributes defining object instances and methods that operate on them. This creates a powerful bridge of understanding between all stakeholders: business experts see their domain accurately reflected, while developers have clear blueprints for implementation.

<a name="section5"></a>
## Bounded Context
Bounded Context is a fundamental pattern in the strategic design section of Domain-Driven Design (DDD). It addresses the challenge of working with large, complex domain models by dividing them into distinct, well-defined contexts based on business intentions.

These contexts establish clear boundaries around where specific domain models apply. Within each bounded context, terms and concepts have precise, consistent meanings—a single entity might exist across multiple contexts but with different attributes and behaviors relevant to each context's specific business needs.

There's no fixed rule for determining the appropriate size of a bounded context—this requires careful architectural analysis. Ubiquitous language serves as an excellent metric for making these decisions: if terminology remains consistent across potential contexts and business processes are handled similarly, combining them might make sense. Conversely, if they differ significantly, separation allows for independent implementation without interference.

Bounded contexts enable teams to work on different parts of a complex system with clear boundaries, creating focused models that precisely serve their specific business purposes while explicitly defining relationships between contexts.

<a name="section5.1"></a>
### Shared Kernel
A Shared Kernel is a strategic pattern in Domain-Driven Design (DDD) where a specific subset of the domain model is deliberately shared between multiple bounded contexts or modules within the same domain. It serves as a central repository for common elements, including ubiquitous language definitions, domain logic, data structures, utility classes, and essential services that are needed across contexts.

<img src="https://github.com/user-attachments/assets/1eade700-c674-40f2-ac52-889a1108b375" alt="acl" width="600"/>

This is a case where communication becomes essential, as it theoretically violates the core principles of bounded contexts. Here, both solutions will be used beyond the proposed boundaries of their contexts. We have multiple teams working on these solutions and different requirements occurring within the same solution.

The major challenge is that any change to the solution affects all involved contexts. Therefore, any modification must be thoroughly tested across all scenarios in all contexts. This situation requires careful coordination and clear communication between teams to ensure changes don't negatively impact the different parts of the system that rely on the shared components

**Benefits**
- Reduced Duplication: Eliminates the need to duplicate common domain logic and data structures in each bounded context;
- Improved Consistency: Ensures consistent terminology and domain concepts across all contexts;
- Unified Domain View: Provides a central location for understanding the core domain concepts

**Challenges**
- Tight Coupling: Changes in the shared kernel can impact all dependent contexts, potentially introducing regressions;
- Complexity Management: Maintaining and evolving a shared kernel can be complex, especially when multiple teams contribute;
- Overhead of Synchronization: Requires a robust and coordinated approach to synchronize changes across dependent contexts

<a name="section5.2"></a>
### Client-Supplier
This model occurs when teams developing different contexts can work separately, but there's a dependency due to a shared service.

- **Supplier(upstream)**: provides a service;
- **Client(downstream)**: consumes a service

#### Conformist pattern
Let's say, we've chosen to use a third-party service that works with OAuth 2.0, since we already use services from this provider. However, we need to create our own Identity and Access Management layer to control who accesses what in our environment.

Since the authentication service belongs to an external vendor who provides services to multiple clients globally, we cannot negotiate for them to adapt to our specific needs. In this relationship, the vendor has the power, which means we must conform to working with the standard they provide and adapt our solution to use this pattern

#### Anti-Corruption Layer (ACL)
An Anti-Corruption Layer (ACL) is a strategic pattern in Domain-Driven Design that serves as a protective boundary between different bounded contexts or between your domain model and external systems.

The main purpose of an Anti-Corruption Layer is to:

- Isolate your domain model from external influences that could corrupt its design and conceptual integrity;
- Translate between different models by providing a two-way conversion mechanism;
- Shield your system from changes in external systems

Take as an example the Identity and Access Management layer who conforms with the third-party service of OAuth2.0. Now this layer has to provide it's service to the other teams (downstream) as it assumes the role of supplier (upstream). If the other teams do not adapt.

However, here we have a situation where the solution (shared kernel), which has Team 1 and Team 2 working on it, does not accept the protocol coming from Team Identity and Access. 
Team 3 won't change their protocol to meet the solution's demands, and the solution teams also refuse to alter their protocol to accommodate the other - which characterizes a non-conformist approach.

Based on this, Teams 1 and 2 decide to create a layer that abstracts the Identity and Access protocol and converts it to their own model, thus maintaining the integrity of their solution. This is a classic example of implementing an Anti-Corruption Layer, where the teams protect their domain model from external influences by creating a translation layer between the two incompatible systems.

<img src="https://github.com/user-attachments/assets/cbac5c07-d967-4255-b66a-5e0f391255da" alt="acl" width="600"/>

#### Open-Host Service (OHS)
Open-Host Service (OHS) is a pattern that stands in contrast to the Conformist approach. While in Conformism the client must adapt to the supplier's model, OHS flips this relationship by prioritizing the client's integration needs.

In this pattern, the service provider creates a standardized integration layer that exposes its capabilities in a language that clients can easily consume without adaptation. This service interface is designed to be stable over time, providing a consistent protocol that multiple clients can rely on while the internal implementation remains free to evolve.

The core benefit of OHS is that it reduces integration friction by having the supplier accommodate multiple clients through a well-defined, published protocol rather than forcing each client to conform to the supplier's internal model.

#### Published Language pattern
However, for the interaction above described to be consistent and reliable across different systems, the service must use a common, well-understood language to describe its inputs, outputs, and behaviors. This is where the Published Language (PL) pattern comes in.

#### Separate Paths
In this model, existing teams do not communicate or integrate their solutions. This typically happens when the cost of integration is significantly higher than developing an internal solution, making it impractical to expose the service to other contexts.

For example, suppose Team 1 and Team 2 both need a service to generate reports. However, their contexts differ significantly, and there is no common pattern in their Ubiquitous Language. Even though they share the same broad goal, their specific requirements and expectations for the service vary so much that integration would be overly complex and costly. In such cases, each team may choose to develop its own independent solution rather than attempting to align their implementations.

#### Big Ball of Mud
Vaughn Vernon (2013), in his book Implementing Domain-Driven Design, mentions the Big Ball of Mud, a model found in very large systems where lacks a clear structure, consistency, or modular design—essentially, it’s a tangled mess of code that evolved without a clear plan.

In this specific case, the recommendations are:

- Draw a boundary around it and call it a Big Ball of Mud.
- Do not attempt to apply any sophisticated modeling methods.
- Be cautious, as this Ball of Mud can contaminate other contexts.

### Context Map
After creating the integrations considering all the models, this is the part of designing the context map, which is the visual representation of bounded contexts and how they integrate.

<a name="section6"></a>
## Tactical Design
Here is where we analyze the "how." We will cover the main concepts of how to implement DDD (Domain-Driven Design), discussing Architecture and DDD Building Blocks. This is when we'll explore the foundations of our system, defining which technologies to use (for example: relational databases or NoSQL? Microservices or Service Bus?), and how they interact with each other.

<a name="section6.1"></a>
### Architecture
It's time to design our solution! We have already mapped our domain and subdomains, defined our ubiquitous language and bounded contexts, and established how they behave and communicate with each other. 

Now we need to create the design of our system - determining how each subdomain will be implemented and where the various logic components will be placed.

DDD organizes the architecture in 4 (four) parts:

#### 1. User interface layer
This is the layer that contains the User Interface (GUI), Command Line Interfaces (CLI), and APIs for integration with other systems

#### 2. Application layer
This layer mediates between the user interface and domain layers. It contains no business logic and doesn't change object states but monitors and reports changes to upper layers. It organizes system tasks. In some architectures, this layer is integrated with the user interface. It can define routines that trigger system-wide updates, like a function that tallies student absences daily and updates central school records—executing business logic without implementing it.

#### 3. Domain layer
The "heart of the software" (Eric Evans, 2003) contains business concepts and rules. Business logic executes here, state changes occur, and records are created. This layer doesn't store data but provides information for the Infrastructure Layer to record.

#### 4. Infrastructure layer
This layer provides technical support capabilities to higher layers. It handles messaging, data persistence, and serves as the standard for interactions between layers (when there's no direct integration).

<a name="section6.2"></a>
### Value Objects
Value objects are recognized by not having identifiers; we use their values to distinguish them from each other. Each is unique and immutable (created as a whole and unchangeable after creation). Vaughn Vernon (2013) has a great description of value objects:

- They measure, quantify, or describe something in the domain.
- They can be maintained as immutable.
- They create a conceptual model of integrity by composing all attributes as a unit.
- They are completely replaceable when a measurement or description changes.
- They can be compared to each other by equality of values.

Being immutable, a value object cannot be modified after creation as mentioned earlier. If any attribute changes, we create an entirely new value. Using a simple example, if we have x = 3, and then change to 4, we create a new x with value 4. 

The same happens with value objects: we don't alter the already created object, we replace it with a completely new one. If a new object is inserted into this table, we must first verify if its values exist. 

For example, if we try to insert "Name 3", "01/03/200", "Street 3", it won't be inserted because it already exists. But if we change an item to "Name 3", "01/03/200", "Street 5", then a new item enters our list. This maintains the uniqueness of the value object list, which requires us to check the object before creating it.

<a name="section6.3"></a>
### Entities
Entities, unlike Value Objects, have identifiers and are mutable. Each entity has a unique ID that will never be used by others, making immutability impossible since the Entity can and should be changed after creation. 

If a new Object is inserted into this table, unlike value objects, we don't need to verify if its values already exist. For example, if we try to insert ("Name 3", "01/03/200", "Street 3"), it will be inserted regardless of whether it already exists, because we'll have a new index. 

When modifying a value, we use its index to find it in the list, and then we can make any necessary changes

<a name="section6.4"></a>
### Aggregate
An aggregate is a collection of entities and value objects that maintain relationships with each other and have a defining boundary. 

One of the basic premises of aggregates is enforced consistency, which guarantees data integrity. Only the aggregate's logic can change its state, ensuring that the business logic defining it is always maintained. No object outside the aggregate can alter its state. 

External objects can read the aggregate's state but cannot change it—this can only be done by the aggregate itself. However, external entities can request that the aggregate perform actions that change its state. 

Note: external entities cannot make changes directly, but they can request modifications. This is exposed in the aggregate through external interfaces that enable what we call commands. Thus, an external object "commands" something to occur.

<a name="section6.5"></a>
### Domain services
Domain services are separately handled objects that work with various entities and aggregates whenever calculations, routine executions, and more are needed.

<a name="references"></a>
#### References
- **https://www.eduardopires.net.br/2016/03/ddd-bounded-context/**
- **https://martinfowler.com/bliki/BoundedContext.html**
- **https://medium.com/@johnboldt_53034/domain-driven-design-the-ubiquitous-language-4f516a385ca4**
- **https://redis.io/glossary/domain-driven-design-ddd/**
- **https://deviq.com/domain-driven-design/shared-kernel**
- **https://mehmetozkaya.medium.com/shared-kernel-pattern-in-domain-driven-design-ddd-21cba2a9f92a**
- **https://medium.com/nick-tune-tech-strategy-blog/domains-subdomain-problem-solution-space-in-ddd-clearly-defined-e0b49c7b586c**





