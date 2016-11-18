[![Build Status](https://travis-ci.org/Agile-IoT/agile-idm-entity-storage.svg?branch=master)](https://travis-ci.org/Agile-IoT/agile-idm-entity-storage)

#AGILE IDM Entity storage


This module uses a leveldb storage and transactions to handle entities in AGILE Identity Management. This module is required in the Web-ui (to validate client secrets), but it is also used by agile-idm-core at the same time.

This enables both idm-core and idm-web-ui to share the same storage module :)
