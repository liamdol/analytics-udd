# Jisc Learning Analytics Unified Data Definitions v1.3.1

## Introduction
The Unified Data Definitions (UDD) of the Jisc analytics project is a vocabulary of the chief data entities of interest to learning analytics: students, courses, modules, and so on, as well as their characteristics. The data coded with this vocabulary is typically extracted from the student record system of a particular college or university.

Along with xAPI recipes, the UDD makes up the core data specification of the Jisc learning analytics architecture.

## Differences between v1.2 and v1.3
The development of v1.3 has involved a number of additions and changes. [This overview page](differences.md) provides a mapped listing of each change.

## Data format
UDD data must be UTF-8 encoded. JSON is the preferred data format, but XML data is also supported. Other formats are not supported.

When providing UDD data, supply the data for different entities in separate files, 1 file per entity, using the [UDD filename conventions](https://github.com/jiscdev/analytics-udd/blob/v1.3.1/filename_conventions.md).

## Diagram
An [entity relation diagram of the whole UDD 1.3](diagram.md) provides a one page overview of the specification.

## Core sections

### Primary keys
Some entities have uniqueness constraints across multiple properties; for example student_on_course_instance has STUDENT_COURSE_MEMBERSHIP_ID plus COURSE_INSTANCE_ID. The MD files for these entities contain a note to this effect. These entities have a single primary key for ease of processing and to enable field-level extensibility. The data supplier may choose to provide the single primary key, or may choose to leave it blank, in which case it will be generated by the LRW loading mechanism.

### [assessment_instance](udd/assessment_instance.md)

### [course](udd/course.md)

### [course_instance](udd/course_instance.md)

### [institution](udd/institution.md)

### [module](udd/module.md)

### [module_instance](udd/module_instance.md)

### [module_vle_map](udd/module_vle_map.md)

### [student](udd/student.md)

### [student_course_membership](udd/student_course_membership.md)

### [student_on_assessment_instance](udd/student_on_assessment_instance.md)

### [student_on_a_module_instance](udd/student_on_a_module_instance.md)

### [student_on_course_instance](udd/student_on_course_instance.md)

## Additional sections
### [period](udd/period.md)

### [staff](udd/staff.md)

### [staff_on_course_instance](udd/staff_on_course_instance.md)

### [staff_on_mod_instance](udd/staff_on_mod_instance.md)

### [student_id_map](udd/student_id_map.md)

There are also files of code lists extracted from the MD files for machine processing.
### [UDD code lists in Welsh](udd/udd_codelists_cy.json)
### [UDD code lists in English](udd/udd_codelists_en.json)

## Mandatory and optional properties
The properties of the UDD are required in compliant datasets to different degrees. The _Mandatory properties in the UDD guide_ outlines the different categories of UDD property. It is available as both [Excel](media/UDDmandatoryFieldGuide.xls) and [ODF](media/UDDmandatoryFieldGuide.ods) spreadsheets.

## Code lists
Some UDD properties consist of code lists. Some have values derived from HESA tables (for HE) or ILR tables (for FE). In general these code lists are mapped to generic UDD code lists, so that they are standardised across data from multiple institutions. To extract code lists from the UDD MD files, you may wish to use the Python utility provided [here](utilities/Extract Code Lists from MD.py).

Some code lists will be specific to one or a limited group of institutions. These lists are not included in the UDD and can be generated by the vendor. They can be loaded to the LRW via a standard JSON format or can be handled via extensions (see below). An example of the JSON format is:

```
"MOD_LEVEL": {"A": null, "C": null, "B": null, "E": null, "D": null, "1": null, "0": null, "3": null, "2": null, "5": null, "7": null, "6": null, "9": null}}
```

## Extensions
There is provision for data extensions at the level of property (in other words, "field-level extensions"). Although not strictly part of the UDD, a separate entity is provided and described at [extension.md](extension.md).

## Specification development workflow
The simplest way of contributing to the UDD is as follows:

1. add an issue to the issue tracker to alert everyone to what you are working on and why
2. tag the issue with the version milestone of which you'd like the patch to be a part
3. make an edit or add a file in this repository, and save it to your own branch. If you prefer, you can fork the whole repository and work in your own repository
4. send a pull request once you're done
5. the pull request will be discussed at our fortnightly meeting and either merged, or kept in the queue, depending on whether more work is required.

You can do all this through the Github GUI, but you're welcome to use any other git tool you prefer.

Particular release versions will get their own branches, but the main branch will always contain the latest agreed release. Releases will be made after the group has come to an agreement.

Versioning is done broadly as follows: major versions (majorVersion.minorVersion.patch) indicate major datamodel changes. Minor versions denote changes that can break applications, such as the deletion of properties that were valid in earlier versions. Patches can include the addition of new properties.

Note that some properties will be marked as 'deprecated'. This means that the property is still valid, but will be removed by the next minor version update.

## Acknowledgements

Many thanks to all contributors who have raised issues, sent pull requests, commented and made suggestions. The UDD specification is the achievement of all of you.

- @alanepaull
- @andrewhickey
- @arc12
- @christoffballard
- @ds10
- @gryglbrt
- @ht2 
- @huwrobertsjisc
- @jfmullaney
- @michaelwebjisc
- @MiroslavKratchounov
- @robwynj
- @ryansmith94
- @sandeepmjay
- @wilmTap

### License
<a rel="license" href="http://creativecommons.org/licenses/by/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by/4.0/88x31.png" /></a><br />This work is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by/4.0/">Creative Commons Attribution 4.0 International License</a>.
