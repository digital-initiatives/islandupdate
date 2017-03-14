### islandupdate
----
_This may not work correctly with any other system than our own._
----
####  Local bash script to update islandora installation to HEAD.
 This is a script to update the islandora related modules, all at the same time so they match what is in HEAD.
 
* does not update everything in drupal - use the periodic drush pm-update for that 
* does not update all libraries, just ones that are updated more frequently
* some modules are commented out because they were in testing or used for one purpose at a particular time.
* does not update any other applications or dependencies, solr, tesseract, etc.
* updates through git from github.com/Islandora, github.com/Islandora-Labs, github.com/discoverygarden, and from our own custom modules at github.com/utkdigitalinitiatives.
* the three scripts here are for three servers with slight changes between them

#### Do these Manual Pre-checks before running script

* check to see if github is working - it has been down several times in the past couple of years
* check the date on the module/library backup directories in /home/islandora, this was the last time the script was used.
* check that no one is doing gui or batch ingests
* send out a notice of service interruption
* merge custom module changes into local repo while updating from HEAD (if you have a custom module that needs to be merged with head before this script runs.)

#### Process inside the script:

1. The script makes dated backups of current modules and libraries
2. Puts drupal into maintenence mode
3. Disables modules
4. Updates libraries
5. with each module:
  - erase old module
  - download new from git (from various sources, including local customizations)
6. enable modules
7. cancel the drupal maintenence mode
8. go to the modules list and run the "update db" link.
9. check to see if all the modules were re-enabled in the correct order.

Note:  careful understanding of what this script does is encouraged. This will delete and change the modules and libraries.
