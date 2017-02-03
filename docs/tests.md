## Basic testing
------------------

Here are some basic information about what things to test, how to create tests etc.

Code is TBD.

### Tests for Entities

See the related guides at [/development](/development/#building-content-types-and-fields)

 - Write tests by bundle
 - Generate dummy content
 - Test the machine_name pattern
 - Test by view_mode
 - Test by entity sbumission form
 - Test all the fields of the bundle (machine_name, no reused, non empty description, field type validation, labels, UI values)
 - Test the access permissions per user Role (VERY IMPORTANT!)

### Tests for Views

See the related guides at [/development](/development/#building-drupal-views)

 - Write tests by Views display (One View may have multiple displays)
 - Test the filters, exposed filters, sorting, pager, non empty description, non empty "no results" message.
 - Test that only View modes are used (when there are Views for Entities)
 - Test the access permissions per user Role (VERY IMPORTANT!)

### Tests per Parameter
Create a test for each one of the [Parameters](http://dropdog.readthedocs.org/parameters/).
