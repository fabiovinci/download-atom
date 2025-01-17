# Separate entries for each format/CRS combination

**Purpose**: The Dataset Feed must contain separate [entries](#entry) for each format/CRS combination in which the pre-defined dataset is made available for download.

**Prerequisites**

**Test method**

* For all [alternative link types](#alternatelinktypes) for this Dataset Feed, check that there are no duplicate values.
* For each [category element](#category) in the Download Service feed entity, which included the link to the Dataset feed document, check that at least one entry exists in the Dataset feed containing a category element with an identical term attribute.

**Reference(s)**:

* [TG DL](http://inspire.ec.europa.eu/id/ats/download-atom/3.1/atom-pre-defined/README#ref_TG_DL), Requirement 27

**Test type**: Automated

**Notes**

1. The method of discovering the parent Download Service Document(s) is left to the ETS. If the Dataset Feed contains the [up-link](#uplink) element it may be used for the parent feed discovery. Alternatively, the validator should use the information about the parent-child relation previously collected when validating the Download Service Feeds pointing to the Dataset Feed. If the validator has not (yet) followed any Download Service Feed entry links to validate this Dataset Feed, it should postpone validation until the parent feed is discovered.

## Contextual XPath references

The namespace prefixes used as described in [README.md](http://inspire.ec.europa.eu/id/ats/download-atom/3.1/atom-pre-defined/README#namespaces).

Abbreviation                                               |  XPath expression
---------------------------------------------------------- | -------------------------------------------------------------------------
entry <a name="entry"></a> | //atom:entry
alternate link types <a name="alternatelinkentries"></a> | //atom:entry[./atom:link[@rel='alternate']]/atom:link/@type
category element <a name="category"></a> | //atom:entry/atom:category[string-length(@term)>0 and string-length(@label)>0]
term attribute <a name="term"></a> | ./atom:category[string-length(@term)>0 and string-length(@label)>0]/@term
up-link <a name="uplink"></a> | /atom:link[@rel='up' and @type='application/atom+xml']
