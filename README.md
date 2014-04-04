## Modified Preorder Traversal Tree for Kohana 3.3 ORM

A port of Banks' Sprig_MPTT plus some code from BIakaVeron's ORM_MPTT module.

[ISC License](http://www.opensource.org/licenses/isc-license.txt)

### Setup

Place module in /modules/ and include the call in your bootstrap.

### Declaring your ORM object

	class Model_Category extends ORM_MPTT {
	}


### Usage Examples

#### Creating a root node:

	$cat = ORM::factory('Category_Mptt');
	$cat->name = 'Music';
	$cat->insert_as_new_root();
	echo 'Category ID'.$mptt->id.' set at level '.$cat->lvl.' (scope: '.$cat->scope.')';
	$c1 = $cat; // Saving id for next example

#### Creating a child node:

	$cat->clear(); // Clearing ORM object
	$cat->name = 'Terminology';
	$cat->insert_as_last_child($c1);

### Running unit tests

You need the test table inside your default database connection to run unit tests.

	CREATE TABLE `test_orm_mptt` (
		`id` INT UNSIGNED AUTO_INCREMENT PRIMARY KEY,
		`parent_id` INT UNSIGNED NULL,
		`lft` INT UNSIGNED NOT NULL,
		`rgt` INT UNSIGNED NOT NULL,
		`lvl` INT UNSIGNED NOT NULL,
		`scope` INT UNSIGNED NOT NULL
	) ENGINE=INNODB;
 
### Authors 
 * Mathew Davies
 * Kiall Mac Innes
 * Paul Banks
 * Brotkin Ivan
 * Brandon Summers
 * Alexander Yakovlev
 * Matthias Lill

