# xDriven #
### A base framework for Xamarin cross-platform solutions. ###

*This framework is under heavy construction currently...*

### Onion Archetecture
This solution implements a flavor of the [onion architecture](http://www.develop.com/onionarchitecture "Onion Architecture") framework pattern. 
The reasoning behind this is to allow separation of concern and modularity. This is especially useful when dealing with 
enterprise-level applications, but also can be applied to smaller projects. It maximizes code reusability and keeps your classes small and 
manageable. It also gives us the ability to swap out and re-use layers with little effort.

### Cross-platform Patterns
**Core.Application.Presenters**  
Keeps all non-UI related logic (business rules, validation, action logic, etc...) in the Core layer so it's re-usable in all presentation layers.

**Core.Application.Context**  
Persists the application context / settings using the data layer (SQLite in this case), making it available for use in all presentation layers.

**Core.Application.Injection**  
Uses a small singleton pattern to inject interface implementations (...until there's a good Xamarin port for Ninject ;).

### Archetecture Overview
**Core**

* **Application**  
Core contains the meat and potatoes of the application, including cross-platform stuff (like application context, presenters, 
broadcasters / events, and services). This also contains the Injector singleton used to register and resolve interfaces. The one and only 
dependency this project has is the Domain layer.
* **Domain**  
Domain namespace containing a sensible entity base as well as a generic repository interface. This layer has no dependencies.

**Infrastructure**
* **IoC**  
This is where dependency resolution is contained. It currently contains one namespace, SQLite, that handles resolving 
SQLite repositories.
* **SQLite**  
This contains the [SQLiteNET library](http://docs.xamarin.com/recipes/ios/data/sqlite/create_a_database_with_sqlitenet/ "SQLiteNET"). 

**Presentation**
* **iOS**  
Everything iOS specific. Anything beyond creation and placement of UI elements should fall back to a corresponding presentation class in Core.Application.
* **Android**  
Everything iOS specific. Anything beyond creation and placement of UI elements should fall back to a corresponding presentation class in Core.Application.

**Solution Items**
* README.md
* LICENSE
* .gitignore


## Items on the todo list:
* Create demo iOS presentation layer that shows use of cross-platform code
* Create demo Android presentation layer that shows use of cross-platform code
* Add notification scheduler base to iOS presentation layer
* Add reachability base to iOS presentation layer
* ...a bunch of other stuff... :)