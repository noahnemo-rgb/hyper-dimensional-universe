# ONE Hyper-dimensional Universe — Scaffold & Inheritance Law

> Part of the [ONE Multiverse](https://github.com/noahnemo-rgb/ONE-) | Governed by [HASEOS](https://github.com/noahnemo-rgb/haseos-spiral-swarm)

---

## Inheritance

ONE Hyper-dimensional Universe is a child universe under ONE Multiverse. It inherits the structural grammar, governance model, and scaffold law of ONE Universe. See [SCAFFOLD.md](https://github.com/noahnemo-rgb/ONE-/blob/main/one-multiverse/one-universe/SCAFFOLD.md) for the full rules.

Child universes may extend but never contradict multiverse-level governance contracts.

All layers of this universe operate under [HASEOS](https://github.com/noahnemo-rgb/haseos-spiral-swarm) (Human-AI Symbiotic Equality Orchestration System). Every layer must wire HASEOS governance before reaching `maturity: active`. Placeholder layers may declare `governed_by: HASEOS` without full wiring, but must list governance wiring in `known_gaps`.

This repo has `governance/`. It does not have `governance/constitution.yaml`. Current `ecology.yaml` and `ecosystem.yaml` files do not declare `governed_by`.

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
| Universe | `universe.yaml` | Universe record. The `ecologies` list fields are `name`, `slug`, `path`, `maturity`. |
| Ecology | `ecology.yaml` | `name`, `order`, `maturity`, `ecosystems`. |
| Ecosystem | `ecosystem.yaml` | `name`, `order`, `maturity`. |
| MVP / Product | `mvp.yaml` or `package.json` / `pyproject.toml` | No `mvp.yaml` in this repo. No field list is defined here. |

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
2. Create `containers/<slug>/` with the ecology folder layout above.
3. Write `ecology.yaml` with `name`, `order`, `maturity`, and `ecosystems`. Use `ecosystems: []` until an ecosystem exists. Set `order` to the next integer.
4. Set the `README.md` heading to the display name only.
5. Append an `ecologies` entry in `universe.yaml` with `name`, `slug`, `path`, and `maturity`.

### Ecosystem

1. Make a slug the same way.
2. Create `containers/<ecology-slug>/ecosystems/<slug>/` with the ecosystem folder layout above.
3. Write `ecosystem.yaml` with `name`, `order`, and `maturity`. Set `order` to the next integer within that ecology.
4. Set the `README.md` heading to the ecosystem display name only.
5. Append an entry to that ecology's `ecology.yaml` `ecosystems` list with `name`, `slug`, `path`, and `maturity`.

### MVP

1. Place the MVP directory under `mvps/monetized/` or `mvps/unmonetized/` on the ecology or the ecosystem that holds it.
2. Add a manifest. The ONE Universe scaffold law names `mvp.yaml` or `package.json` / `pyproject.toml` for an MVP / Product.
3. This repo does not define `mvp.yaml` fields.

---

## Maturity

| Level | Description |
|-------|-------------|
| `placeholder` | Declared in manifest, no files yet |
| `scaffolded` | Manifest + SCAFFOLD.md + directory structure exist |
| `in_progress` | Active development, incomplete governance |
| `active` | Fully wired — governance, manifest, scaffold, and at least one MVP |
| `stable` | Active + documented + tested |
| `deprecated` | Sunset, preserved for reference |

This universe is `scaffolded`: `universe.yaml`, this `SCAFFOLD.md`, and the directory structure exist. The six ecologies and the three ecosystems remain `placeholder`.

---

## Migration notes

| Date | Change |
|------|--------|
| 2026-10-09 | Added this file. Universe maturity set to `scaffolded`. |
