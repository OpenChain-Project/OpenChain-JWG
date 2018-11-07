# Report of studies on business workflow and roles for OSS compliance

### The OpenChain Japan work group

## 1.	Background of the work
For a company, to understand its business workflow of software is very important to improve OSS compliance process. In this context, “business workflow” means how software and license information is received from a supplier, transferred and processed from section to section inside an organization, and finally released to a recipient. Inside an organization, several functional blocks may cooperate each other to achieve OSS compliance.

The new proposal for the training part of the OpenChain specification requires an organization to define the roles for OSS compliance process. 

Therefore, it is important to share examples of how the roles could be structured in an organization. The OpenChain Japan workgroup would like to contribute by providing examples of the roles in business workflow.

The outcome of the studies has been disclosed at the OpenChain GitHub site and wiki.


## 2.	Approach taken by the Japan workgroup
The Japan work group took the following approach:

* (1)	Business workflow: At first, before defining the roles, the Japan workgroup has studied several examples of business workflows in industries, such as Automotive, CE, IT. The examples of the business workflow diagram across different domains have been created and those are also useful references for a company to apply OSS compliance process to itself.

* (2)	Universal model of business workflow: Then the Japan workgroup has built the universal model of business workflow derived from examples. This model consists of “supplier”, “organization” and “recipient”. The “organization” has internal functional blocks, those are candidates of roles.

* (3)	Roles: From the universal model, the Japan workgroup has defined the roles. The roles are not organizational but functional, because a function in OSS compliance can be carried out by different organizational units. For example, reviewing a license is done by legal department in some companies, and by intellectual property department in other companies. It is useful to define roles as functional, so that different companies can easily apply the roles and its concept to themselves. The roles are listed with explanation.

 
## 3.	Business workflow
The Japan work group has studied business workflow across automotive, CE, IT industries. 

## 3-1.	 Automotive industry (case for development of infotainment system)
The supply chain of the automotive industry consists of OEM (automotive company) and Tier-x suppliers. An OEM directly contracts with Tier-1 suppliers to develop a system. OSS comes indirectly via Tier-x suppliers.

The diagram shows the relationship of software supply chain. 

![automotive business workflow] (img/BF-AUTO-1.png)

 
## 3-2.	 CE (consumer electronics) industry
CE industry has several patterns for product development. 

### 3-2-1. Case CE-1: (brand: own brand / development: own development with ISV and contractual developer)
CE-1 is a typical pattern for development of CE products. A company develops a product in cooperation with a contractual software developer and an ISV (independent software vendor). In this case, the company has direct connection with the contractual developer and the ISV. The company release software embedded in a product to end users. OSS comes directly to the company, and indirectly via the contractual developer and the ISV. 

![CE business workflow 1](img/BF-CE-1.png)

 
### 3-2-2. Case CE-2: (brand: own brand / development: contractual developer)
In this case, a CE company does not develop software by itself, instead, a contractual developer develops whole software in cooperation with a ISV and the CE company receives software and verifies and releases software embedded in a product to end users.
OSS comes indirectly via the contractual developer and the ISV. 

![CE business workflow 2](img/BF-CE-2.png)

 
### 3-2-3. Case CE-3: (brand: own brand / development: SoC vendor)
In this case, a CE company does not develop software by itself, instead, an SoC vendor develops whole software and the CE company receives software and verifies and releases software embedded in a product to end users. 
OSS comes indirectly via the SoC vendor. 

![CE business workflow 3](img/BF-CE-3.png)


### 3-2-4. Case CE-4: (brand: own brand / development: ODM vendor)
In this case, a CE company does not develop software by itself, instead, an ODM vendor develops whole software and the CE company receives software and verifies and releases software embedded in a product to end users. 
OSS comes indirectly via the ODM vendor.

![CE business workflow 4](img/BF-CE-4.png)

 
### 3-2-5. Case CE-5: (brand: own brand / development: system integration)
In this case, a CE company purchases a hardware product, and builds system integrating with the purchased hardware and own developed software and service. 
CE company integrates system solution and releases the system solution to end users. 
OSS comes indirectly via the hardware product company.

![CE business workflow 5](img/BF-CE-5.png)

 
## 3-3.	 IT industry

### 3-3-1. Case IT-1: (brand: own brand / development: )

![IT business workflow 1](img/BF-IT-1.png)

### 3-3-2. Case IT-2: (brand: own brand / development: )

![IT business workflow 2](img/BF-IT-2.png)

### 3-3-3. Case IT-3: (brand: own brand / development: )

![IT business workflow 3](img/BF-IT-3.png)

### 3-3-4. Case IT-4: (brand: own brand / development: )

![IT business workflow 4](img/BF-IT-4.png)


 
## 4.	Universal model
The Japan work group has built the universal model of business workflow derived from examples. This model consists of “supplier”, “organization” and “recipient”. The “organization” has internal functional blocks.

Universal model of business workflow (img/Universal-Model.png)


 
## 5. Roles


