### Entity type review - Checklist

An Entity may be of type Node, Taxonomy, User etc.

In order to use this checklist on an issue
[copy the source code](https://raw.githubusercontent.com/dropdog/docs/master/docs/review/entity.md)
into the issue and treat the checklist accordingly.

**A. Basic checklist:**

 1. [ ] Commits are atomic
 2. [ ] Pull request (or branch) is atomic
 3. [ ] One Entity Type per Drupal Feature
 4. [ ] Entity type correct machine_name pattern
 5. [ ] DFeature correct machine_name pattern
 6. [ ] Fields correct machine_name pattern
 7. [ ] Fields have a description
 8. [ ] Fields are not shared (exceptions need to be added on the commit messages)
 9. [ ] Display modes are not specific (for this Entity Type)
 10. [ ] Usage of Taxonomy vs Entityreference is OK
 11. [ ] Default core body field has been deleted
 12. [ ] DFeature has user permissions
 13. [ ] DFeature has been tested (locally or remotely)
 14. [ ] All the dependencies exist already on D.O. or on the Github profile
 15. [ ] Multilingual settings have be set (if need to)
 16. [ ] Domain access (module) have been set (if need to)
 17. [ ] Pathauto alias patterns (module) have been set (if need to)
 18. [ ] Workbench_moderation (module) settings have been set (if need to)

 ----------

 **B. Extended checklist:**

 1. [ ] DFeature contains the related DViews
 2. [ ] Entity type contains Tests
