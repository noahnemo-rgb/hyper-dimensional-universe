# ONE Hyper-dimensional Universe — Scaffold & Inheritance Law

> Part of the [ONE Multiverse](https://github.com/noahnemo-rgb/ONE-) | Governed by [HASEOS](https://github.com/noahnemo-rgb/haseos-spiral-swarm)

---

## Inheritance

ONE Hyper-dimensional Universe is a child universe under ONE Multiverse. It inherits the structural grammar, governance model, and scaffold law of ONE Universe. See [SCAFFOLD.md](https://github.com/noahnemo-rgb/ONE-/blob/main/one-multiverse/one-universe/SCAFFOLD.md) for the full rules.

Child universes may extend but never contradict multiverse-level governance contracts.

All layers of this universe operate under [HASEOS](https://github.com/noahnemo-rgb/haseos-spiral-swarm) (Human-AI Symbiotic Equality Orchestration System). Every layer must wire HASEOS governance before reaching `maturity: active`. Placeholder layers may declare `governed_by: HASEOS` without full wiring, but must list governance wiring in `known_gaps`.

`governed_by: HASEOS` is set on `universe.yaml`, each `ecology.yaml`, and each `ecosystem.yaml`. `governance/constitution.yaml` inherits [HASEOS-IDAO CONSTITUTION.md](https://github.com/noahnemo-rgb/HASEOS-IDAO/blob/main/CONSTITUTION.md) (first formal draft, unratified). [haseos-spiral-swarm governance/charter.md](https://github.com/noahnemo-rgb/haseos-spiral-swarm/blob/main/governance/charter.md) is a workshop stub. It is not the HASEOS Constitution. Each ecology and ecosystem has `governance/constitution.yaml` extending the universe file. Local rules are empty.

---

## Layers

The model is a universe of many ecologies, each with many ecosystems, populated with monetized and unmonetized website/app SaaS MVPs plus ideations and documents.

The container layer is the ecology layer. It lives under `containers/`.

```
ONE Multiverse
└── one-hyper-dimensional-universe
    └── containers/ (ecology layer)
        └── ecosystems/
            ├── mvps/monetized/
            ├── mvps/unmonetized/
            ├── ideations/
            └── documents/
```

Each ecology also holds `mvps/monetized/`, `mvps/unmonetized/`, `ideations/`, and `documents/`.

### Canonical hierarchy

```
ONE Multiverse
└── one-hyper-dimensional-universe  ← you are here
    ├── containers/ (ecology layer)
    │   ├── UFOs/UAPs
    │   ├── Ancient Texts describing Hyper-Dimensional Entities
    │   ├── Paranormal Phenomena
    │   ├── Crop Circles
    │   ├── Documented Channelings
    │   └── Documented Outliers
    │       ├── Anomalies
    │       ├── Enigmas
    │       └── Erratics
    └── governance/ (HASEOS)
```

UFOs/UAPs, Ancient Texts describing Hyper-Dimensional Entities, Paranormal Phenomena, Crop Circles, and Documented Channelings have empty ecosystems lists. No MVPs, ideations, or documents have been added.

Repo-root `ecosystems/` is a separate empty directory. Ecosystems are added under `containers/<ecology-slug>/ecosystems/`.

---

## Manifests

Every layer of the hierarchy must have a machine-readable manifest.

| Layer | Manifest | Fields in this repo |
|-------|----------|---------------------|
| Universe | `universe.yaml` | Universe record, including `governed_by`. The `ecologies` list fields are `name`, `slug`, `path`, `maturity`. |
| Ecology | `ecology.yaml` | `name`, `order`, `maturity`, `governed_by`, `ecosystems`. |
| Ecosystem | `ecosystem.yaml` | `name`, `order`, `maturity`, `governed_by`. |
| MVP / Product | `mvp.yaml` or `package.json` / `pyproject.toml` | No MVP exists yet. The template fields are below. |

`path` is from the repo root. `order` is on `ecology.yaml` and `ecosystem.yaml` only. It is not repeated on the parent list.

An `ecology.yaml` `ecosystems` entry has `name`, `slug`, `path`, and `maturity`, or the list is `[]`.

YAML keys are `snake_case`. Double-quote values that contain spaces or other special characters.

---

## Folder layout

Ecology (`containers/<slug>/`):

```
<slug>/
├── README.md
├── ecology.yaml
├── governance/
│   └── constitution.yaml
├── ecosystems/
├── mvps/
│   ├── monetized/
│   └── unmonetized/
├── ideations/
└── documents/
```

Ecosystem (`containers/<ecology-slug>/ecosystems/<slug>/`):

```
<slug>/
├── README.md
├── ecosystem.yaml
├── governance/
│   └── constitution.yaml
├── mvps/
│   ├── monetized/
│   └── unmonetized/
├── ideations/
└── documents/
```

The `README.md` heading at each of these layers is the display name only. Empty holding directories contain `.gitkeep`.

---

## Names

Directory names are lowercase and hyphenated: no underscores, no spaces, no camelCase. The directory name is the slug. The display name is the `name` field and stays as written. Renames require a migration note in this file.

`/` cannot be a directory name. The display name `UFOs/UAPs` uses the slug `ufos-uaps`.

| Order | Display name | Slug |
|------:|--------------|------|
| 1 | UFOs/UAPs | `ufos-uaps` |
| 2 | Ancient Texts describing Hyper-Dimensional Entities | `ancient-texts-describing-hyper-dimensional-entities` |
| 3 | Paranormal Phenomena | `paranormal-phenomena` |
| 4 | Crop Circles | `crop-circles` |
| 5 | Documented Channelings | `documented-channelings` |
| 6 | Documented Outliers | `documented-outliers` |

Documented Outliers ecosystems:

| Order | Display name | Slug | Path |
|------:|--------------|------|------|
| 1 | Anomalies | `anomalies` | `containers/documented-outliers/ecosystems/anomalies` |
| 2 | Enigmas | `enigmas` | `containers/documented-outliers/ecosystems/enigmas` |
| 3 | Erratics | `erratics` | `containers/documented-outliers/ecosystems/erratics` |

---

## How to add

### Ecology

1. Make a slug from the display name: lowercase, hyphenated, and safe as a directory name.
2. Copy `shared_scaffold/ecology/` to `containers/<slug>/`.
3. Fill `<display name>` and `order` in `ecology.yaml` and the `README.md` heading. Keep `governed_by: HASEOS`. Use `ecosystems: []` until an ecosystem exists.
4. Append an `ecologies` entry in `universe.yaml` with `name`, `slug`, `path`, and `maturity`.

### Ecosystem

1. Make a slug the same way.
2. Copy `shared_scaffold/ecosystem/` to `containers/<ecology-slug>/ecosystems/<slug>/`.
3. Fill `<display name>` and `order` in `ecosystem.yaml` and the `README.md` heading. Keep `governed_by: HASEOS`.
4. Append an entry to that ecology's `ecology.yaml` `ecosystems` list with `name`, `slug`, `path`, and `maturity`.

### MVP

1. Place the MVP directory under `mvps/monetized/` or `mvps/unmonetized/` on the ecology or the ecosystem that holds it.
2. Add a manifest. The ONE Universe scaffold law names `mvp.yaml` or `package.json` / `pyproject.toml` for an MVP / Product.
3. Copy `shared_scaffold/mvp/monetized/` or `shared_scaffold/mvp/unmonetized/`. The parent law does not define `mvp.yaml` fields. ONE Universe `sub_components` entries use `name`, `role`, and `maturity`. The template also sets `governed_by: HASEOS` and `monetized`. `monetized` matches the folder. It is not a parent-law field.

---

## Templates

`shared_scaffold/` holds fill-in skeletons:

| Template | Path |
|----------|------|
| Ecology | `shared_scaffold/ecology/` |
| Ecosystem | `shared_scaffold/ecosystem/` |
| Monetized MVP | `shared_scaffold/mvp/monetized/` |
| Unmonetized MVP | `shared_scaffold/mvp/unmonetized/` |
| Ideation | `shared_scaffold/ideation/ideation.md` |
| Document | `shared_scaffold/document/document.md` |

README headings and the ideation and document files are `# <display name>` only. No ideation or document body fields are defined.

## Maturity

| Level | Description |
|-------|-------------|
| `placeholder` | Declared in manifest, no files yet |
| `scaffolded` | Manifest + SCAFFOLD.md + directory structure exist |
| `in_progress` | Active development, incomplete governance |
| `active` | Fully wired — governance, manifest, scaffold, and at least one MVP |
| `stable` | Active + documented + tested |
| `deprecated` | Sunset, preserved for reference |

This universe is `in_progress`. Scaffold law defines `in_progress` as active development, incomplete governance. Manifest, this `SCAFFOLD.md`, the directory structure, and HASEOS wiring by reference exist. Local charter, roadmap, policies, and compliance sections are empty. There is no MVP, so this is not `active`. The six ecologies and the three ecosystems remain `placeholder`.

---

## Migration notes

| Date | Change |
|------|--------|
| 2026-10-08 | Added this file. Universe maturity set to `scaffolded`. |
| 2026-10-08 | Wired `governance/` to HASEOS by reference. Populated `shared_scaffold/` templates. Universe maturity set to `in_progress`. |
