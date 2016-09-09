**Mogenerator template to parse NSDictionary into a NSManagedObject Subclass created with mogenerator**


This template allows to create entities filled with an NSDictionary (perfect for JSON mapping to Core Data) using:
```sh
+ insertWithDictionary:context:
```

or update an object with:

```sh
+ updateObject:withdictionary:context:
```

Every entity has methods to add from an NSArray of NSDictionaries and list all entities using sort descriptors array

```sh
+ (BOOL)insertAll:(NSArray *)objects;
+ (NSArray *)getAll:(NSArray *)sortDescriptors;
+ (void)deleteAllEntitiesInContext:(NSManagedObjectContext*)moc_;
```

How to Use:
Add for every property in our xcdatamodel that We want to be mapped you have to add a new row in its User Info dictionary (in Data Model Inspector).

- Key name: **jsonKey**
- Key value: NSDictionary Key that contains the object to be read.

If the property is a *relationship* (and you want to be added as relationship in your object) you have to be sure that its destination class also has created its subclass using mogenerator.

And that's it!

**Example of generation script**

```sh
#!/bin/bash
mogenerator --template-var arc=true -m CoreData/MyModel.xcdatamodeld/MyModel.xcdatamodel -M CoreData/Machine/ -H CoreData/Human/ --template-path coredata_templates_folder
```

### Version
1

### Author
Joan Biscarri
