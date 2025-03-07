In Mule 4, an Object Store is a built-in component that allows you to store and retrieve data in a persistent or non-persistent manner during the execution of a Mule application. 
It can be useful for caching data, managing state across multiple flows or sessions, or storing intermediate results.

**Default Object Store:**
    By default, each Mule app has an Object Store that is persistent and always available to the app without any configuration. Flows can use it to persist and share data.
    If you want to use the default Object Store, you can specify a key for the Object Store without selecting or creating an Object Store reference for the Object Store operation, and without specifying an               objectStore attribute in the XML element for the Object Store component.
    We can not configure Max Number of Entries, TTL, Expiration Interval.
    You use Anypoint Platform Runtime Manager to deploy Mule apps to CloudHub workers. 
    The key-value pairs (contents) are visible in Runtime Manager if you use persistent Object Store and key-value pairs are stored.
    The Key value pairs will reside in OS for 30 days by default unless until clear the OS or remove the keys
    
![image](https://github.com/user-attachments/assets/356f8dea-047b-4ff9-926b-2776696225d6)





**Custom Object Store:**
  Custom Object Stores must specify an objectStore attribute.
  We can indicate whether the Object Store is persistent (so that the Object Store data survives a Mule Runtime crash) or transient (where data does not survive a Mule Runtime crash).
  We can configure Max Number of Entries, TTL, Expiration Interval.
  The Key value pair will reside OS based on the TTL and based on the expiration inteval.
    Max Entries: Each entry over the limit of entries is discarded when the expiration thread runs.
    TTL(Time to Live): Every entry that exceeds the value given in entryTtl is automatically deleted.
    Expiration Interval: An expiration thread runs based on the value and discards the elements that exceed their time to live (TTL) or their maxEntries limit.

  ![image](https://github.com/user-attachments/assets/7fe0ae53-85bc-4b85-8bcc-b7f0ab5c4985)


