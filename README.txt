-------------------------
owORFilter :
-------------------------
owObjectRelationsFilter (owORFilter) provides an extended attribute filter for "Object relation" and "Object relations" datatypes.
This filter supports basic logical operators.
This will work with single relations as well as multiple.


-------------------------
Author
-------------------------
Simon Boyer, from a good work of Bertrand Dunogier and Grégory Becue (thanks) : http://projects.ez.no/enhanced_object_relation_filter


-------------------------
Installation instructions
-------------------------

1) If it does not exist, create a directory named "extension" in the base ezpublish directory.


2) Unpack the ZIP file and copy the directory "oworfilter" to the extension directory.


3) Activate extension :
---------------------------------
Add the following to your settings/override/site.ini.append.php file:
[ExtensionSettings]
ActiveExtensions[]=oworfilter

	OR

In administrator user interface, click 'setup' tab->'extensions' menu, select 'oworfilter', click button 'Apply Changes'



4) Regenerate autoloads :
---------------------------------
In administrator user interface, click 'setup' tab->'extensions' menu, click button 'Regenerate autoload arrays for extensions'

	OR
	
in eZ Publish installation folder, run "php bin/php/ezpgenerateautoloads.php -e"



5) Clear cache
---------------------------------
Clear INI and template caches. (from admin 'Setup' tab or commandline)



-------------------------
Usage
-------------------------

This filter is used like any extended attribute filter, as explained on the
documentation for the content/list fetch function:
http://doc.ez.no/eZ-Publish/Technical-manual/4.x/Reference/Modules/content/Fetch-functions/list

Examples :

Single object_id, single attribute :
---------------------------------------------
{def $nodeList = fetch(content, list, hash(parent_node_id, XX,
                          extended_attribute_filter, hash(
                              'id', 'orfilter',
                              'params', array(
                                array('classe1/attribut1', 61)
                              )
                          )))}
                          
                          
Multiple object_ids, single attribute  :
---------------------------------------------
{def $nodeList = fetch(content, list, hash(
							'parent_node_id', XX,
        					'extended_attribute_filter', hash(
                              		'id', 'orfilter',
                              		'params', array(
                              			array('classe1/attribut1', array(70, 71), 'or')
                              			)
                          )))}
                          
                          

Multiple object_ids, multiple attributes  :
---------------------------------------------
{def $nodeList = fetch(content, list, hash(
							'parent_node_id', XX,
        					'extended_attribute_filter', hash(
                              		'id', 'orfilter',
                              		'params', array(
                              			'or',
                              			array('classe1/attribut1', array(70, 71), 'or'),
                              			array('classe2/attribut2', array(80, 81), 'and')
                              			)
                          )))}





---------------------------------------------
Hope you find it useful! 

Simon Boyer

