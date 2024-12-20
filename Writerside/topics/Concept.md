# Ines ERP core

## Description
This is the central unity of the system, here we will manage all other modules and utilities. Attached here we will have a account management system, some tools to enable disable modules, and other basic configs that will be cross shared between all system.
___
## Some ideas to make it work
- To enable/disable modules:
    - I could try to prepare some scripts that runs a shell scripts to turn up/down some containers, those containers will talk to each other with some API (to be define the pattern), the ERP core module will provide any extra configuration that would be necessary to connect different modules.
- The core module will have all cross needs for all other modules. Account management, Module managements, other configs. It should work like Django settings file.
- I will need some server like NGinx to connect things
- (THIS WILL NOT WORK ONLY IN POSTGRES I will need do that in BE) Each module, will be responsible for its own database, only providing some endpoints to connect with other modules, I need to figure it out how to manage foriengkeys once the data bases will not be directly connected.
    - Maybe I could use some database_name/table_name/column_name to relate thinks. Need to research
    - Another possibility is use noSQL databases that could provide simple way to save and manage that.

___
We could make some use of meddlewares in C#

DBContext is bind to one specifica database and DbSet is bind to tables