# ArchiMate Toolkit Best Practices & Resource Guide

This guide provides formal resources, best practices by industry experts, recommended workflows, and other key resources for using ArchiMate and the Archi toolkit effectively in individual and collaborative settings.

---

## 📛 Naming Conventions

**Consistency in naming improves model quality and makes collaboration smoother.**
Always check if others have addressed the same problem before, or even done work that could be reused for this problem. The topic of naming conventions, or nomenclature, is tied in with several topics:
- Controlled Vocabularies
- Translation
- Ontologies
- Metamodels

Other sources for naming conventions:
- Existing literature
- Existing organizational policy
- Common usage within audience / stakeholders

### Formal Resources:
- [ANSI/NISO Z39.19-2005 (R2010) Guidelines for the Construction, Format, and Management of Monolingual Controlled Vocabularies](https://www.niso.org/standards-committees/vocab-mgmt)
- [ISO 704:2022 Terminology work — Principles and methods](https://www.iso.org/standard/79077.html)
- [OMG SVBR - Semantics Of Business Vocabulary And Business Rules](https://www.omg.org/spec/SBVR/)

### Best Practices by Experts
- **Gerben Wierda** suggests that you in the first line put some grouping information in square brackets, e.g. device name in the technology layer, application name in the application layer or business unit in the business layer
in the second line put the element name in the third line put the element type in brackets. E.g. “[Customer System] Change Address (Application Process)” or “[Customer Service] Claim Handling (Business Service)”. [Gerben Wierda – Mastering ArchiMate](https://ea.rna.nl/mastering-archimate-edition-3-2/)
- [Naming Conventions in Architecture Modeling - Orbus Software Research Library](https://www.orbussoftware.com/resources/research-library/naming-conventions-in-architecture-modeling)

### General Recommendations
- Use **compound terms** rather than standalone words to enhance clarity (e.g., `StudentInformationSystem` vs. `System`).
- Stick to **Singular Noun Phrases** for **structural elements** (e.g., `Ariba Reporting`, `Data Warehouse`, `User Portal`).
- Use **Verb Phrases** for **behavioral elements** (e.g., `Manage Applications`, `Generate Reports`, `Process Payments`).
- Avoid abbreviations unless they are well-known in your domain.
- Avoid qualifiers – e.g. “Reporting (Finance)”
- Use PascalCase or Title Case for element names (e.g., `StudentInformationSystem`, `Course Registration`)
- For Views, use conventions that can support hierarchies of information; this supports navigation and reporting.
  - standardized prefixes for state (e.g., `ASIS_`, `TOBE_`)
  - use viewpoints for suffixes (e.g. CAP for Capability Map)
- Name relationships explicitly only when semantically useful
- When creating custom specializations, maintain a list of custom types in your model documentation for governance

---

## 📜 jArchi Scripts

**Automate repetitive tasks, enhance navigation, and enforce modeling standards.**

- Add view legends dynamically
- Batch apply properties or visual styles
- Extract metadata or generate model documentation

🛠 Example Scripts:
- [Archi GitHub - jArchi Examples](https://github.com/archimatetool/archi-scripting-plugin/tree/master/com.archimatetool.script.examples)
- [Archi Scripting Community](https://forum.archimatetool.com/index.php?board=10.0)

---

## 🧠 Modeling Current and Future State

**Clearly distinguish between "as-is" and "to-be" architectures.**

- Use separate folders or views with prefixes (`ASIS_`, `TOBE_`)
- Tag elements using properties like `state=current` or `state=future`
- Consider visual differentiation (color, label) to indicate state

---

## 🗂 Managing Models

### Single Model vs Multiple Models

- **Single Model**: Easier to manage, better traceability across layers
- **Multiple Models**: Suitable for complex orgs or distributed teams, but requires governance

### Collaboration Strategies

- Define model ownership and editing boundaries
- Use shared element libraries for consistency

---

## 🌍 Using coArchi

**Version control and collaboration for teams.**

- Use Git-based repositories (GitHub, GitLab, Azure DevOps)
- Commit often and write meaningful messages
- Consider branch-per-feature or branch-per-domain strategies

📘 Resources:
- [coArchi Guide](https://www.archimatetool.com/plugins/coarchi/)

---

## 🧱 Model Structure and Patterns


📚 Resources:
- [Eero Hosiaisluoma – ArchiMate Cookbook](https://www.hosiaisluoma.fi/blog/archimate/)

---

## 📤 Publishing & Sharing

**Make your work accessible to stakeholders.**

- Export to HTML or PNG
- Generate interactive websites with tools like [Archi HTML Export](https://github.com/archimatetool/archi-models)
- Publish to a central intranet 

### Publishing HTML to SharePoint
- SharePoint does not allow scripting by default. To work around this see 

---

## 🏷 Utilizing Properties

**Leverage element/view properties to add metadata and context.**

- Add properties like `owner`, `domain`, `status`, `lastUpdated`
- Use scripts to batch assign or update
- Useful for filtering and custom exports

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

**Keep model documentation relevant and accurate.**

- Create a `viewMeta` property with author/date/info
- Use a script to audit last modified dates
- Maintain a changelog view for major updates

---

## 🔗 Integration with External Sources

**Enrich your model with data from other systems.**

- Import CSVs (e.g., from CMDB, HR, or ERP systems)
- Use jArchi to pull/push data to REST APIs
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
- 🧰 [Archi Official Site](https://www.archimatetool.com/)
- 📘 [Mastering ArchiMate – Gerben Wierda](https://masteringarchimate.com/)
- 📗 [ArchiMate Cookbook – Eero Hosiaisluoma](https://ea.rgordon.org/ArchiMateCookbook.html)
- 🧑‍💻 [jArchi Plugin Documentation](https://github.com/archimatetool/archi-scripting-plugin)
- 💬 [Archi Forum](https://forum.archimatetool.com/)
- 🔄 [coArchi Plugin](https://www.archimatetool.com/plugins/coarchi/)
- 🧵 [Stack Overflow – ArchiMate Tag](https://stackoverflow.com/questions/tagged/archimate)
