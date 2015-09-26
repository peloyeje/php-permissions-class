# PHP Permissions Class v.1.0
A lightweight permissions class, with memory caching features
* Handles text and wildcards (\*)
* Handles group and user permissions
* Handles inheritance
Used for instance in [FeatherBB](http://featherbb.org)

### Requirements
* PHP 5.3


### Let's see some code

```php
$permissions = new Permissions()
$user = array('uid' => 32,
              'gid' => 1);

// Add parent to group / All permissions of group 2 will be valid for group 1
$permissions->addParent(1, 2);
// $permissions->delParent(1, 2);

// Add a group-wide permission
$permissions->allowGroup(1, 'topic.read');
// Or many permissions
$permissions->allowGroup(1, array('topic.read', 'topic.reply', 'topic.post'));

// Deny 'topic.read' for user 32 only
$permissions->denyUser(32, 'topic.read');

// Has user 32 permission to read the forums ?
$permissions->can(32, 'topic.read') // return FALSE

// Give group 1 all permissions for topic node
$permissions->allowGroup(1, 'topic.*');
```
