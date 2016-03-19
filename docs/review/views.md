### Views review - Checklist

Drupal Views (DViews) that contain lists of entity types such as Node, Taxonomy, User etc.

**Notice**: a DViews may be a part of a DFeature of an Entity type and not a separate DFeature.

In order to use this checklist on an issue
[copy the source code](https://raw.githubusercontent.com/dropdog/docs/master/docs/review/views.md)
into the issue and treat the checklist accordingly.

**IMPORTANT**: If one or more checkboxes of the list do not apply
(eg there is no need for **Multilingual Settings**) please REMOVE the related
checkbox to avoid misunderstand.

**A. Basic checklist:**

 1. [ ] Commits are atomic
 2. [ ] Pull request (or branch) is atomic
 3. [ ] One Views Display (eg Page, Block etc) per DViews. Exceptions should be reported on commit messages
 4. [ ] DViews correct machine_name pattern
 5. [ ] DFeature correct machine_name pattern (if it is a separate DFeature)
 6. [ ] DViews has a proper Title
 7. [ ] DViews has not custom CSS classes
 8. [ ] DViews is using only Entity Display modes (Full, Teaser etc). Exceptions should be reported on commit messages.
 9. [ ] DViews has a tag same as your (development) nickname
 10. [ ] DViews has no Menu link through the DViews settings
 11. [ ] DViews does not use Ajax
 12. [ ] "No results behavior" is not empty
 12. [ ] DViews is using User Permissions for Access
 13. [ ] DViews has been tested (locally or remotely)
 14. [ ] All the dependencies exist already on D.O. or on the Github profile
 15. [ ] Multilingual settings have be set (if need to)
 16. [ ] Domain access (module) have been set (if need to), eg for DViews Blocks
 17. [ ] Multiple DViews of the same Entity type belong to the same DFeature (eg a Page, a Block and a Feed of node type Article)

 ----------

 **B. Extended checklist:**

 1. [ ] DViews has useful Administrative comments
 2. [ ] DViews contains Tests
 3. [ ] DFeature has no dependency to itself
 4. [ ] DFeature configuration files exist in place
 5. [ ] Additional README.txt with how to information has been added (if needed)
