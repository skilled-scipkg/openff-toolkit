---
name: openff-toolkit-templates
description: This skill should be used when users ask about templates in openff-toolkit; it prioritizes documentation references and then source inspection only for unresolved details.
---

# openff-toolkit: Templates

## High-Signal Playbook

### Route Conditions
- Use this skill for Sphinx autosummary template behavior and API-doc rendering customization (`docs/_templates/autosummary/module.rst`, `docs/_templates/autosummary/base.rst`).
- Route runtime API/wrapper behavior to `openff-toolkit-api-and-scripting`.
- Route domain modeling and simulation questions to `openff-toolkit-inputs-and-modeling`.

### Triage Questions
- Are you customizing module pages, class/method pages, or both?
- Do you need autosummary lists for attributes/functions/classes/exceptions?
- Should submodules render recursively in generated docs?
- Is title formatting expected to include parent object names?
- Are generated docs missing members, or incorrectly grouped?
- Is the issue in template logic or in object discovery/autodoc imports?

### Canonical Workflow
1. Choose target template file (`docs/_templates/autosummary/module.rst` or `docs/_templates/autosummary/base.rst`).
2. Update only the needed Jinja/autosummary block.
3. Rebuild docs and inspect generated API pages.
4. Confirm object grouping and headings match expectations.
5. If missing objects persist, inspect import paths/autosummary targets in API docs.

### Minimal Working Example
```rst
.. automodule:: {{ fullname }}

.. autosummary::
{% for item in classes %}
   {{ item }}
{%- endfor %}
```

```rst
.. currentmodule:: {{ module }}
.. auto{{ objtype }}:: {{ objname }}
```

### Pitfalls and Fixes
- Treating these files as runtime code: they only control docs generation (`docs/_templates/autosummary/*.rst`).
- Missing module recursion in generated docs: ensure `:recursive:` path is present where needed (`docs/_templates/autosummary/module.rst`).
- Unexpected page titles for methods/attributes: check parent-name capitalization logic in template preamble (`docs/_templates/autosummary/base.rst`).
- Autosummary shows empty sections: verify upstream API docs expose the expected object lists.

### Convergence and Validation Checks
- Documentation build completes without autosummary/autodoc errors.
- Generated pages include expected objects under expected rubrics.
- Title rendering for class members and free functions matches intended style.
- No unrelated API docs regress after template edits.

## Scope
- Handle questions about documentation grouped under the 'templates' theme.
- Keep responses abstract and architectural for large codebases; avoid exhaustive per-function documentation unless requested.

## Primary documentation references
- `docs/_templates/autosummary/module.rst`
- `docs/_templates/autosummary/base.rst`

## Workflow
- Start with the primary references above.
- If details are missing, inspect `references/doc_map.md` for the complete topic document list.
- If ambiguity remains after docs, inspect `references/source_map.md` and start with the ranked source entry points.
- Cite exact documentation file paths in responses.

## Source entry points for unresolved issues
- `docs/_templates/autosummary/module.rst` (module-page section layout)
- `docs/_templates/autosummary/base.rst` (single-object page title + body rendering)
- `openff/toolkit/utils/base_wrapper.py` (common API object patterns reflected in autosummary output)
- `openff/toolkit/utils/toolkits.py` (high-traffic API objects frequently rendered by templates)
- Prefer targeted source search (for example: `rg -n "<symbol_or_keyword>" docs openff/toolkit`).
