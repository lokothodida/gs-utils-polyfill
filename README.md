# \*EXPERIMENTAL\* GetSimple CMS Plugin SDK
The purpose of this project is to provide a library that is:

* **portable** *(easy to add to add/remove from a plugin)*
* **unified** *(has a consistent, intuitive and stable interface)*
* **backward/forward compatible** *(works with old and new GetSimple versions)*
* **well documented**

in order to simplify the typical problems that arise during [GetSimple plugin](http://get-simple.info/wiki/) development. These problems include (but are not limited to):

* Building data structures for your plugin
* Sanitizing user inputs and avoiding XSS vulnerabilities
* Remaking/copying methods that exist in the core
* Accessing site data such as site/current user settings
* Building UI elements consistent with administration panel between versions

# Getting Started
## From scratch
* Download the [Hello World](https://github.com/lokothodida/gs-hello-world/) plugin example
* Rename the `hello_world.php` file and `hello_world/` folder
* You now have a ready-built plugin with the SDK library included
* *NOTE: currently only the GSPlugin class is in the Hello World example. Download the other classes from here.*

## From an existing plugin
* Create a /lib/ directory in your plugin's folder
* Download the `gsutils.php`, `gsui.php` and `gsplugin.php` files from this repository and put them in the lib directory
* `include` those files before your plugin is registered
* You can now use these classes in your plugin

# TODO
* Full documentation for below methods

# Libraries
## GSUtils
### SDK_VERSION
### __construct
### mkdir
### rmdir
### mvdir
### copy
### mkfile
### putfile
### rmfile
### mvfile
### getfile
### getfiles
### fileexists
### iswritable
### print
### slug
### translit
### clean

## GSUI
### SDK_VERSION
### __construct
### header
```php
echo $ui->header('Admin Page Title', array(
  // Navigation links
  array('label' => 'Page 1', 'href' => 'page1'),
  array('label' => 'Page 2', 'href' => 'page2'),
  array('label' => 'Page 3', 'href' => 'page3'),
));
```
### title
```php
echo $ui->title('Admin Panel Title');
```

### quicknav
```php
echo $ui->quicknav(array(
  array('label' => 'Page 1', 'href' => 'page1'),
  array('label' => 'Page 2', 'href' => 'page2'),
  array('label' => 'Page 3', 'href' => 'page3'),
));
```

### quicktab
```php
echo $ui->quicktab('tab-container', array(
  // Tabs
  array('label' => 'Tab 1'),
  array('label' => 'Tab 2'),
  array('label' => 'Tab 3'),
), array(
  // Content
  'Page 1',
  'Page 2',
  'Page 3',
));
```

### parag
```php
echo $ui->parag('A paragraph');
```
### section
```php
echo $ui->section(
  // Left section (can be given as an array)
  'Left section content',
  // Right section (can be given as an array)
  'Right section content',
);
```
### leftsec
### rightsec
### metawindow
```php
echo $ui->metawindow('Left content', 'Right content');
```

### table
```php
// Normal table
echo $ui->table(array(
  // Header
  'header' => array('Items', 'Year'),
  // Rows
  'rows' => array(
    array('Item 1', '2014'),
    array('Item 2', '2015'),
    array('Item 3', '2013')
  ),
));

// Editable table
echo $ui->table(array(
  'type' => 'edit',
  // Header
  'header' => array('Items', 'Year'),
  // Rows
  'rows' => array(
    array('Item 1', '2014'),
    array('Item 2', '2015'),
    array('Item 3', '2013')
  ),
));
```

### anchor
```php
// Cancel button
echo $ui->anchor('cancel', array(
  'label' => Cancel',
  'href' => 'http://.../',
));
```

### form
```php
echo $ui->form(array(
  'method' => 'post',
  'action' => 'path/to/script.php',
  'content' => 'Form content',
));
```

### input
```php
// Text field
echo $ui->input(array(
  'label' => 'Field',
  'name' => 'field',
  'value' => 'Initial value',
));

// Title text field
echo $ui->input(array(
  'type' => 'title',
  'name' => 'title',
  'value' => 'Your Title Here',
));

// Checkbox
echo $ui->input(array(
  'label' => 'Enable HTML Editor?',
  'type' => 'check',
  'name' => 'enableeditor',
  'value' => true,
));
```

### dropdown
```php
echo $ui->dropdown(array(
  // Container
  'name' => 'items',
), array(
  // Values
  array('value' => 'Item 1'),
  array('value' => 'Item 2'),
  array('value' => 'Item 3'),
));
```

### htmleditor
```php
echo $ui->htmleditor(array(
  'name' => 'content',
  'value' => 'Initial content for the editor',
  'config' => array(
    // CKEditor config
  ),
));
```

### codeeditor
```php
echo $ui->codeeditor(array(
  'name' => 'code',
  'value' => 'Your initial code',
  'config' => array(
    // CodeMirror config
  )
));
```

### submit
```php
echo $ui->submit(array(
  'name' => 'submit',
  'value' => 'Submit',
));
```

### submitline
### footer
### element
```php
echo $ui->element('div', array(
  'class' => 'class1 class2',
  'id' => 'yourdiv',
), 'Content');
```

## GSPlugin
### SDK_VERSION
### __construct
Instantiate the plugin wrapper with data about the plugin.
```php
$plugin = new GSPlugin(array(
  'id'       => 'your_plugin',
  'version'  => '1.0',
  'author'   => 'You',
  'website'  => 'http://yourwebsite.com',
  'tab'      => 'plugin_page_tab',
  'lang'     => 'default_language',
));
```
### id
Get the plugin id (same as the one given in the constructor)
```php
echo 'The plugin id is ' . $plugin->id();
```
### author
Get the plugin author (same as one given in the constructor)
```php
echo 'The plugin author is ' . $plugin->author();
```

### version
Get the plugin version (same as one given in the constructor)
```php
echo 'The plugin version is ' . $plugin->version();
```

### tab
#### `tab()`
Get the plugin tab (same as one given in the constructor)
```php
echo 'The plugin tab is ' . $plugin->tab();
```

#### `tab($id, $label, $action = null)`
Register a new tab for the plugin
```php
$plugin->tab(/* */);
```

### sidebar
### hook
### filter
### script
### style
### admin
### index
### i18n
### autoload
### init
