---
layout: page
title: Primer for back-end development
permalink: /start/primer-develop-backend/
menuInclude: yes
menuTopTitle: Start
menuSubTitle: Primer back-end
menuSubIndex: 3
---

Start with introduction to [core code](/guides/#core-code)
and the [server-side](/source-code/#server-side) source code repositories.

The [Okapi Guide and Reference](https://github.com/folio-org/okapi/blob/master/doc/guide.md) provides the necessary background understanding.

The [FOLIO-Sample-Modules guide](https://github.com/folio-org/folio-sample-modules/blob/master/README.md) further explains what is a server-side module and how to develop one. Importantly, these examples show that any [programming language](/guides/any-programming-language) is possible.

Then see the guide to [Running a local FOLIO system](/guides/run-local-folio/) for guidance to establish your local FOLIO work environment.

The [Commence a module - structure and configuration](/guides/commence-a-module/) guide explains a consistent layout for a back-end module,
together with the guidelines to [Create a new FOLIO module and do initial setup](/guidelines/create-new-repo/).

The [RAML Module Builder](https://github.com/folio-org/raml-module-builder) (RMB) framework, is a special FOLIO module that abstracts much functionality and enables the developer to focus on implementing business functions. Define the APIs and objects in RAML files and schema files, then the RMB generates code and provides tools to help implement the module.
(Note that at this stage of the FOLIO project, only this Java-based framework is available.)

The [mod-rmb-template](https://github.com/folio-org/mod-rmb-template)
provides a Maven archetype to commence a new RMB-based module.

[Conduct cross-module joins via their APIs](/guides/cross-module-joins/).

The [Primer for RAML and JSON Schema](/start/primer-raml/) provides some guidance.
