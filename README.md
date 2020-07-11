FamilyTreeGenerator

[![GoDoc](https://godoc.org/github.com/spy16/droplets?status.svg)](https://godoc.org/github.com/spy16/droplets) [![Go Report Card](https://goreportcard.com/badge/github.com/spy16/droplets)](https://goreportcard.com/report/github.com/spy16/droplets)
[![FOSSA Status](https://app.fossa.io/api/projects/git%2Bgithub.com%2Fspy16%2Fdroplets.svg?type=shield)](https://app.fossa.io/projects/git%2Bgithub.com%2Fspy16%2Fdroplets?ref=badge_shield)

Generates a family tree randomly using Go. Inspired by the python Gramps project.

THis project will take specified settings, and generates a family tree structure. Will add more as details are fleshed out.

Step-by-step for application
1. Application starts, reads configuration file. This file holds configuration settings like start year, amount of family trees, etc...
2. Configuraton settings are loaded. Stored in variables that are available across the application.
3. Open connection to DB and verify that DB exists. If not, create using defined schema
4. Create the "Adam and Eve" start to a tree. This can be randomly generated from a specified name file, or use the ones provided in the settings file.
    1. If more then one "root couple" is defined, loop through them
    2. Once complete, save to DB 
5. Load all initial couples 
    6. For initial couples, there will be no check for infertility due to the possibility of having a family tree dead ending.
    7. A random amount of children will be generated, dependent on mother age (the older the mother, the less children generated). 
        8. If mother is over 40, end processing and return error
        9. A random name, birthdate and deathdate is generated.
            10. Birthdate must be after the parents marriage date, and before their the date of the mothers 40th birthday.
    11. Save the created children records, linking them to the parent records
    12. Perform this for all initial couples
13. 