We have an xml where we have a table element and inside table element we have 3 more elements and with the information.
We have another XML here, and we have table element and then table has elements like tr, td.

![image](https://github.com/user-attachments/assets/a5e8faf2-6591-45ba-bcbd-7740ffcadeb2)

If we have 2 xml files and used these 2 xml files separately they are not associated with each other any ways.

If we have to combine these 2 xml files together, there will be a name conflict for the table element.
Name conflicts can be resolved in XML by using **prefix**.
Now there will be no conflicts as the two <table> elements have different names.
When using prefixes in our XML, a namespace for the prefix must be defined.

**xmlns:prefix="URI"**

**The namespace can be defined by an xmlns attribute in the start tag of an element.
All child elements with the same prefix are associated with the same namespace.
Namespaces can also be declared in the XML root element.**
====================================
Defining default namespace for an element saves us from using prefixes in all the child elements.

XML Namespaces are used for providing uniquley named elements and attributes in an XML
