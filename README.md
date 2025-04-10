# ArchiMate Toolkit Best Practices & Resource Guide

This guide provides formal resources, best practices by industry experts, recommended workflows, and other key resources for using ArchiMate and the Archi toolkit effectively in individual and collaborative settings.
---


## 📛 Naming Conventions

**Consistency in naming improves model quality and makes collaboration smoother.**
Always check if others have addressed the same problem before, or even done work that could be reused for this problem. The source of most names are derived from more general sources:
- Existing literature from Industry and Vendors
- Existing organizational policies
- Common usage within audience / stakeholders

The topic of naming conventions, or nomenclature, is tied with more formalized topics:
- Controlled Vocabularies
- Translation
- Ontologies
- Metamodels

### Best Practices by Experts
- **Gerben Wierda** suggests that you in the first line put some grouping information in square brackets, e.g. device name in the technology layer, application name in the application layer or business unit in the business layer
in the second line put the element name in the third line put the element type in brackets. E.g. “[Customer System] Change Address (Application Process)” or “[Customer Service] Claim Handling (Business Service)”. [Gerben Wierda – Mastering ArchiMate](https://ea.rna.nl/mastering-archimate-edition-3-2/). To accomplish this, you can use Archi's [Label Expressions](https://github.com/archimatetool/archi/wiki/Label-Expressions).
  ```
  [${property:Group}]
  ${name}
  (${type})
  ```

### General Recommendations
- Use **compound terms** rather than standalone words to enhance clarity (e.g., `Student Information System` vs. `System`).
- Stick to **Singular Noun Phrases** for **structural elements** (e.g., `Ariba Reporting`, `Data Warehouse`, `User Portal`).
- Use **Verb Phrases** for **behavioral elements** (e.g., `Manage Applications`, `Generate Reports`, `Process Payments`).
- Avoid abbreviations unless they are well-known in your domain.
- Avoid qualifiers – e.g. `Reporting (Finance)`
- Use Title Case for Element names (e.g., `Auxiliary Services`)
- Use Title Case or PascalCase for Properties (e.g., `Course Registration`, `StudentInformationSystem`) 
- For Views, use conventions that can support hierarchies of information; this helps with navigation and reporting.
  - Use standardized prefixes for state (e.g., `ASIS_`, `TOBE_`, or `Current`,`Target`,`Project`)
  - Use Viewpoints abbreviation (if any) for suffixes (e.g. `_CAP` for Capability Map)
- Name Relationships explicitly only when semantically useful
- When creating custom Specializations, maintain a list of custom types in your model documentation for governance

### Links to Resources:
- [ANSI/NISO Z39.19-2005 (R2010) Guidelines for the Construction, Format, and Management of Monolingual Controlled Vocabularies](https://www.niso.org/standards-committees/vocab-mgmt)
- [ISO 704:2022 Terminology work — Principles and methods](https://www.iso.org/standard/79077.html)
- [OMG SVBR - Semantics Of Business Vocabulary And Business Rules](https://www.omg.org/spec/SBVR/)
- [Orbus Software Research Library - Naming Conventions in Architecture Modeling](https://www.orbussoftware.com/resources/research-library/naming-conventions-in-architecture-modeling)

---

## 📜 jArchi Scripts

**Automate repetitive tasks, enhance navigation, and enforce modeling standards.**
Collection of curated scripts. To share script on GitHub Gist, script must ends with .ajs (which is the default extension for jArchi scripts) and Description must contains the tag #jArchi

🛠 Collection Scripts:
- [Archi GitHub - jArchi Examples](https://github.com/archimatetool/archi-scripting-plugin/tree/master/com.archimatetool.script.premium/examples)
- [jArchi Sample Scripts (part of jArchi codebase)](https://github.com/archimatetool/archi-scripting-plugin/wiki/Community-shared-scripts)
- [jArchi Community Script Pack](https://github.com/archi-contribs/jarchi-community-script-pack)
- [jarchi-lib - Collection of jArchi scripts curated and developed by Robert Chevallier.](https://github.com/rchevallier/jarchi-lib)
- [jArchi Scripts - Collection of jArchi scripts and resources curated and developed by Thomas Rohde.](https://github.com/ThomasRohde/archi-scripts)
- [GitHub Gist - simple way to share (and thus find) jArchi script.](https://gist.github.com/search?utf8=%E2%9C%93&q=%23jarchi+extension%3Aajs&ref=searchresults)

Some Notable inclusions:
- [Single-page HTML Export by Phillip Beauvoir & Jean-Baptiste Sarrodie](https://github.com/archi-contribs/jarchi-single-page-html-export)
- [Colormap (or Heatmap) Wizard by Robert Chevallier](https://github.com/rchevallier/jarchi-lib/blob/main/doc/Colormap%20wizard.md)
- [SVG-based View2SingleHTML by Remco Schellekens](https://github.com/RemcoSchellekensNS/jarchi-View2SingleHTML/tree/main) - [Forum Post](https://forum.archimatetool.com/index.php?topic=1500.msg7726#msg7726)
- [Isolate View Into Separate Model by Remco Schellekens](https://gist.github.com/RemcoSchellekensNS/a528ba45bf1541920075c1504af975f4)
- [ArcHistory, display history of views in published websites by jsimoncello](https://forum.archimatetool.com/index.php?topic=1416.msg7388#msg7388)
- [Generate Markdown documentation by Richard Heward](https://gist.github.com/rich-biker/9a3c86c5a576ce0d8639856f3ee81651)
- [Audit Model based on MetaModel by Steven Mileham](https://gist.github.com/smileham/ea92a4133c81f51474596ce8428935f8)

---

## 🧠 Modeling Current and Future State

It is hard to use the same model for AS-IS and TO-BE architectures.  One represents Facts, such as Current State, Application Inventory, Process Maps, Technology Catalogs, etc. The other is to support or record decisions, such as future-state architectures and therefore subject to constant change.  Object names, definitions, relations and views will evolve from AS-IS across the different iterations of TO-BE.

In the [ArchiMateTool Forum](https://forum.archimatetool.com/index.php?topic=1153.msg6154#msg6154), JB Sarrodie suggests two different approaches:
```
In my case, I assume that name and definition won't change, only relationships and views will.
Another assumption is that people mainly interact with views, and view provide some context (the view title but also the way they are organized inside a folder hierarchy).
My last assumption is that, at some point some automation is needed which relies on the knowledge that some concept will appear in the future).
With those assumptions in mind, my approach relies on a well defined (but flexible) folder hierarchy for views which make it possible to distinguish views describing the current state or the future state (or even some state in-between). It then becomes easy to know the context in which a view sits.
(...)
```

```
Another option that I've seen (but have limited experience with) is to start with the AS-IS model, save it as another (TO-BE) model and do whatever you want in this TO-BE model. Then, if you want to reflect changes from AS-IS to TO-BE, you simply have to use the model import feature of Archi to import AS-IS into TO-BE. When you're done with TO-BE, make sure it contains only new or changed views, remove every concept that doesn't appear in at least one view and import TO-BE into AS-IS. Of course, this is very limited and doesn't permit in depth analysis of changes.
```

---
---
Anything after this needs more details
---
---

## 🗂 Managing Models

### Single Model vs Multiple Models

- **Single Model**: Easier to manage, better traceability across layers
- **Multiple Models**: Suitable for complex orgs or distributed teams, but requires governance
- **Federated Model**: Centralized AS-IS Model, distributed copies per Area / Project teams.  (???)

### Collaboration Strategies

- Define model ownership and editing boundaries
- Use shared element libraries for consistency

---

## 🌍 Using coArchi

**Version control and collaboration for teams.**

- Use Git-based repositories (GitHub, BitBucket, GitLab, Azure DevOps)
- Commit often and write meaningful messages
- Consider branch-per-feature or branch-per-domain strategies
- Change History tab: if you look at the message lines, one or two of them have a small icon to materialize HEADs of remote (yellow cylinder) and local (white sheet of paper

📘 Resources:
- [coArchi Download](https://www.archimatetool.com/plugins/#coArchi)

---

### 🔗 Database Plugin

**Database export/import plugin that store models in a central repository.**

- Export and import models to a relational database (PostGreSQL, MySQL, MS SQL Server, Oracle or SQLite)
- Export elements and relationships to a graph database (Neo4J)

[Archimate Tool Database-Plugin](https://github.com/archi-contribs/database-plugin)

---

## 🧱 ArchiMate Patterns

📚 Resources:
- [ArchiMate Community - Patterns Library](https://archimate-community.org/#!patterns.md)
- [Mastering ArchiMate by Gerben Wierda](https://masteringarchimate.com/)
- [ArchiMate Cookbook by Eero Hosiaisluoma](https://www.hosiaisluoma.fi/blog/archimate/)
- [Archimate Patterns by Steven Mileham](https://smileham.co.uk/2019/03/20/archimate-patterns-all-together-now/)

---

## 📤 Publishing & Sharing

**Make your work accessible to stakeholders.**

- Generate interactive websites with tools like [Archi HTML Report] to publish to a central intranet.
- SharePoint does not allow scripting by default. See .ASPX workaround: (https://forum.archimatetool.com/index.php?topic=1429.msg7450#msg7450)
- Generate Single-Page HTML file with [Single-page HTML Export by Phillip Beauvoir & Jean-Baptiste Sarrodie](https://github.com/archi-contribs/jarchi-single-page-html-export)
- Generate Single-Page HTML from View (with SVG) with [View2SingleHTML by Remco Schellekens](https://github.com/RemcoSchellekensNS/jarchi-View2SingleHTML/tree/main)

---

## 🏷 Utilizing Properties

**Leverage element/view properties to add metadata and context.**

- Add properties like `owner`, `domain`, `status`, `lastUpdated`
- Use scripts to batch assign or update
- Useful for filtering and custom exports
- Keeping metadata updated...

  
---

## 🧭 Model Navigation

**Help users find what they need quickly.**

- Use views as entry points to domains or layers
- Link views using drill-down or reference elements
- Add legends and instructions to guide viewers

---

## 🔍 Drilling Views

**Relate views to support layered understanding.**

- Use `ViewReference` elements or clickable shapes to link between views
- Maintain context by labeling transition elements

---

## 🧰 View Metadata & Updates

**Keeping model documentation relevant and accurate.**

- Create a `viewMeta` property with author/date/info
- Use a script to audit last modified dates
- Maintain a changelog view for major updates

---

## 🔗 Integration with External Sources

**Enrich your model with data from other systems.**

- Import CSVs (e.g., from CMDB, HR, or ERP systems)
- Use jArchi to pull/push data
- Sync architecture data with PowerBI, GraphDB, or ServiceNow

---

## 👥 Collaboration Patterns

### Single User

- Local modeling, occasional merge into shared repo

### Multiple Users

- coArchi with Git sync
- Clearly define branches and merge windows

---

## 🧪 Meta-Model Control

**Customize modeling constraints when needed.**

- Stick to standard ArchiMate or use element specializations
- Avoid meta-model bloat—review specializations regularly

---

## 🌿 coArchi Branch Strategies

- **Main + Feature Branch**: Each change in a separate branch
- **Team Branches**: One per domain team (e.g., `business-team`, `infra-team`)
- Tag stable versions for milestones

---

## 🧹 Model Sanity Checks

**Regular cleanups prevent chaos.**

- Remove orphaned elements and views
- Validate relationships using jArchi
- Run visual inspections for consistency

---

## 🖼 View Templating

**Maintain visual consistency.**

- Reuse views as templates
- Use legends, instructions, fixed layout patterns
- Keep a library of template views (e.g., Business Capability Map)

---

## 🧩 Combining EA + SA (Solution Architecture)

- Use one model with separate domains for EA and SA
- Use folders or tags to filter views
- Clearly differentiate strategic vs. project-specific views

---

## 📚 ArchiMate Resources & Further Reading

- 📘 [ArchiMate 3.2 Specification](https://pubs.opengroup.org/architecture/archimate3-doc/)
- 📗 [ArchiMate 101: A Practical Introduction](https://archimate-community.pages.opengroup.org/workgroups/archimate-101/)
- 📕 [Archi Official Site](https://www.archimatetool.com/)
- 📖 [Mastering ArchiMate – Gerben Wierda](https://masteringarchimate.com/)
- 🧰 [ArchiMate Cookbook – Eero Hosiaisluoma](https://ea.rgordon.org/ArchiMateCookbook.html)
- 🧑‍💻 [jArchi Plugin Documentation](https://github.com/archimatetool/archi-scripting-plugin)
- 💬 [Archi Forum](https://forum.archimatetool.com/)
- 🔄 [coArchi Plugin](https://www.archimatetool.com/plugins/coarchi/)
- 🧵 [Stack Overflow – ArchiMate Tag](https://stackoverflow.com/questions/tagged/archimate)
