# RolesAndPermissionsSeeder

###This Seeder class allows you to manage Roles & Permissions for the Laravel [Entrust package](https://github.com/Zizaco/entrust). 

Relationships between users, roles and permissions will automatically be updated when you make changes to the roles & permissions in the seeder class. To use, just add the class to your /database/seeds directory.



####Add your Roles and Permissions to the appropriate arrays within the seeder. e.g.

```php
class RolesAndPermissionsSeeder extends Seeder {

	protected $roles = [
	
		'admin' => [
			'display_name'	=>	'Administrator', // optional
			'description'	=>	'administer the website and manage users', // optional
			'permissions' 	=> ['edit_others_posts','can_add_users', 'edit_own_posts'] // optional
		],
		
		'editor' => [
			'permissions' 	=> ['edit_own_posts']
		],
		
		'member' => [] 
	];
	
	protected $permissions = [
		
		'edit_others_posts' => [
			'display_name' => 'Edit Other\'s Posts', // optional
			'description'	=>	'edit other users posts', // optional
		],
		
		'can_add_users' => [],
		
		'edit_own_posts' => []
	];

	...
```

####Run the seed class using the cli

```bash
php artisan db:seed --class=RolesAndPermissionsSeeder
```

You'll get the following output..

```bash
 
Creating/updating the 'admin' role
-----------------------------------------
  -> Created admin role
  -> Attached 3 permissions to admin role
 
Creating/updating the 'editor' role
-----------------------------------------
  -> Created editor role
  -> Attached 1 permissions to editor role
 
Creating/updating the 'member' role
-----------------------------------------
  -> Created member role
  -> Attached 0 permissions to member role
 
Cleaning up roles & permissions:
--------------------------------
  -> Done
```


When you update your roles & permissions here, the changes will be reflected in the database after running the seed. User and Permission relationships will be updated. The command line output will allow you to keep track of the changes made.



