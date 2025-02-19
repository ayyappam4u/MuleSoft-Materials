RAML (RESTful API Modeling Language) is a YAML-based language that allows you to define RESTful APIs in a structured and human-readable format. 
In Mule 4, RAML is often used to define APIs for designing, documenting, and testing API specifications.
The RAML file defines the structure of the API, including the resources, HTTP methods (GET, POST, PUT, DELETE), request/response data formats, and other details.

The Root of the Document:
	The root section of the RAML document describes the basic information about an API, such as its title and version. 
	The root section also defines assets used elsewhere in the RAML document, such as types and traits.
		
		#%RAML 1.0
		title: API
		version: v1

**Data Types:**
  In RAML, data types are used to define the structure and validation rules for the request and response payloads.
  Types can define two types of members: properties and facets. Both are inherited.
		Properties are regular, object oriented properties.
		Facets are special configurations. You specialize types based on characteristics of facet values. Examples: minLength, maxLength
		Only object types can declare properties. All types can declare facets.
  Types can included in RAML as below.
  ![image](https://github.com/user-attachments/assets/badd4994-f8ab-45d9-9d45-69a5f23aea01)
  ![image](https://github.com/user-attachments/assets/5066027f-a9b9-4361-9a18-ea20d6d1fedb)
  
**Traits:**
  In RAML, Traits are reusable sets of parameters, headers, and other common configurations that can be applied to multiple API methods or resources. 
  Traits help avoid repetition and promote reusability across your API design.
  For example, if several API methods require the same set of query parameters or headers, you can define those common elements as a trait and then apply it to each method.
    Traits can be defined at the root of the API Definition or traits can also be defined in an exteral files and these are included by using !inlude tag.
    A method can specify one or more traits by using the **is** node.
    The value of traits must be an Array of any number of elements.
    ![image](https://github.com/user-attachments/assets/c7caf72f-01ba-47fc-a3cd-887ae1172453)
    ![image](https://github.com/user-attachments/assets/10b8085a-9a62-4f5c-b4e9-21bc4d635778)


**Resource Type:**
In RAML (RESTful API Modeling Language), Resource Types are used to define common behaviors or structures for resources that can be reused across multiple resources or methods. 
Resource Types allow you to define a template for resource behavior (such as standard headers, responses, query parameters, etc.), and then apply that template to different resources or methods to avoid redundancy and improve maintainability.
![image](https://github.com/user-attachments/assets/79d7039c-f838-47d5-bb1e-25be4e8da082)
![image](https://github.com/user-attachments/assets/c0903dae-71c6-4781-94bf-0490078d6148)


**Fragments:**
Fragments are reusable snippets of RAML code that can be included in multiple API specifications. 
They help modularize and organize your RAML definitions.
We can create frgments for the following types:
  1. Traits
  2. Resource Type
  3. Library
  4. Data Type
  5. Example
  6. Security Schemas
  7. Annotation Type

A Trait Fragments
  ![image](https://github.com/user-attachments/assets/3221c42f-a98d-4983-a6bd-d26a66cb37ce)
A Data type Fragments
![image](https://github.com/user-attachments/assets/e82e4669-c847-4678-929b-1bc84a1cc79f)


**Libraries:**
In RAML, Library is the reusable component and one of the fragments type.
RAML libraries are used to combine any collection of data type declarations, resource type declarations, trait declarations, and security scheme declarations into modular, externalized, reusable groups.
While libraries are intended to define common declarations in external documents, which are then included where needed, libraries can also be defined inline.

Library fragment with Traits and Data Type:
![image](https://github.com/user-attachments/assets/5f191763-6784-4e01-87c3-a4940316e2be)
![image](https://github.com/user-attachments/assets/aa73bad4-fa91-4247-85ca-6c0fa5c58d2f)


[employee-api (1).zip](https://github.com/user-attachments/files/18876766/employee-api.1.zip)

[employee-with-rt-api.zip](https://github.com/user-attachments/files/18876775/employee-with-rt-api.zip)

    
