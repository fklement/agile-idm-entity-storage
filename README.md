[![Build Status](https://travis-ci.org/Agile-IoT/agile-idm-entity-storage.svg?branch=master)](https://travis-ci.org/Agile-IoT/agile-idm-entity-storage)

#AGILE IDM Entity storage

This module uses a leveldb storage and transactions to handle entities in AGILE Identity Management. This module is required in the AGILE-IDM web component (to validate client secrets), and it is also used by agile-idm-core, also inside AGILE-IDM web to store entities.

## Main Responsibilities

Leveldb is a lightweight, open source, key value database. One of the main advantages for node.js applications is that a value can consitute and object (i.e. an entity for IDM). However, to remain lightweight, its node implementation implements an in-memory locking system, in which the database connection can be instantiated only once to ensure consistency. So, one of the main responsibilities of this component is to offer a module that ensures that only one database connection is used.

Furthermore, this component ensures that even if requests are executed in parallel, the execution of actions is serialized. This is achieved by using the leveldb-transactions node package.

## Functionality

AGILE IDM Entity Storage offers a high level, promise-based, API to:
* create, read, update and delete entities
* create, delete groups and read group information.
* add and remove entities to a group (equivalent to group update).
* look up entities for a given set of attribute values. For instance, it is possible to find entities with a particular owner and attribute name equal to "my sensor".

Even though some API calls of AGILE IDM Entity Storage resemble the AGILE-IDM Core API, they are focused on handling storage issues such as transaction synchronization, while the AGILE-IDM Core API also validates the entities schema, enforces policies, and includes owner information in the entities.

AGILE IDM Entity Storage component is only used by AGILE-IDM Web and by AGILE-IDM Core. However,  in case the reader is interested in usage examples, this component is currently used in AGILE-IDM Core to store entities (see https://github.com/Agile-IoT/agile-idm-core/blob/master/lib/api/api.js). Also, given that functionalities are constantly tested with unit test which verify response or expected status codes, the test folder of the AGILE IDM Entity Storage constitutes a good  starting point to interact with the AGILE IDM Entity Storage node js module.

#Debug mode

If you define the following variable (to be 1) this module will print debugging information.

export DEBUG_IDM_STORAGE=1

If no variable is set, or if any other value different than 1 is set, this component runs in quiet mode.
