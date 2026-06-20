# NuGridPy3

NuGridPy3 is a modernization fork of NuGridPy for nuclear astrophysics
analysis. The goal is to preserve the scientific value and familiar workflows of
NuGridPy while making the package easier to install, easier to use, compatible
with modern Python, and capable of producing publication-quality plots by
default.

This fork starts from the existing NuGridPy codebase and will evolve toward a
maintainable Python 3 package with stronger tests, clearer APIs, and modern
visualization defaults.

## Goals

- Support current Python 3 versions and keep compatibility work visible as new
  Python versions are released.
- Modernize packaging with `pyproject.toml`, standard dependency metadata, and
  reliable installation workflows.
- Replace legacy Python 2 compatibility layers and deprecated scientific Python
  APIs.
- Preserve existing NuGridPy user workflows where practical, especially common
  notebook and interactive-analysis patterns.
- Improve the plotting system so nuclear astrophysics figures are clear,
  beautiful, colorblind-aware, and suitable for papers, talks, and reports.
- Add tests around core scientific utilities, data readers, and plotting
  behavior so future refactors are safer.
- Improve documentation with modern examples for MESA, NuGrid `se` files,
  abundance profiles, Kippenhahn diagrams, HR diagrams, isotope charts, and
  publication exports.

## Compatibility Direction

NuGridPy3 is expected to target actively maintained Python versions. The exact
support window will be defined in project metadata and CI, but the intended
policy is:

- Test against multiple supported Python 3 releases.
- Avoid deprecated NumPy, SciPy, Matplotlib, and h5py APIs where possible.
- Prefer explicit compatibility shims over hidden version-specific behavior.
- Keep import-time side effects minimal so the package remains stable in
  scripts, notebooks, batch jobs, and documentation builds.

## Development Setup

NuGridPy3 uses `pyproject.toml` for package metadata and dependency groups.
Use a virtual environment for local development, then install the package in
editable mode with the development and documentation extras:

```bash
python3 -m venv .venv
source .venv/bin/activate
python3 -m pip install -r requirements-dev.txt
```

Run the test suite with:

```bash
python3 -m pytest
```

Runtime-only installs can use:

```bash
python3 -m pip install -r requirements.txt
```

## Plotting Direction

Plotting modernization is a first-class goal, not an afterthought. NuGridPy3
will add a coherent plotting layer with:

- Publication-oriented Matplotlib styles.
- Consistent figure sizing and export helpers.
- Colorblind-safe palettes and scientifically meaningful colormaps.
- Cleaner defaults for labels, legends, tick marks, line widths, and DPI.
- APIs that return `fig` and `ax` objects so users can customize figures
  without fighting global plotting state.
- Backward-compatible wrappers for established plotting methods where feasible.

## Migration Principles

- Modernize in small, reviewable steps.
- Keep scientific behavior stable unless a change is intentional and documented.
- Prefer additive APIs before removing legacy behavior.
- Mark breaking changes clearly.
- Maintain examples that can be run by users and by CI.

## Initial Roadmap

1. Establish modern packaging, dependency groups, and CI.
2. Define supported Python versions and a compatibility policy.
3. Remove Python 2 compatibility scaffolding and fix modern Python warnings.
4. Build a reliable test baseline for existing functionality.
5. Add the first centralized plotting style module.
6. Upgrade key analysis plots: HR diagrams, Kippenhahn diagrams, abundance
   profiles, isotope charts, and flux charts.
7. Refresh documentation and example notebooks around the new workflows.

## Relationship To NuGridPy

NuGridPy3 is a fork intended for modernization work. It should credit and
preserve the original NuGridPy project history while providing a place to make
larger Python 3 and plotting improvements without destabilizing legacy users.
