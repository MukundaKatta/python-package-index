# MukundaKatta Python package index

A [PEP 503](https://peps.python.org/pep-0503/) simple package index hosted on GitHub Pages, serving authoritative links to releases of:

- [`bedrock-ops`](https://github.com/MukundaKatta/bedrock-ops) — production-grade boto3 toolkit for AWS Bedrock
- [`embspec`](https://github.com/MukundaKatta/embspec) — embedding pipeline ops + drift detection for production RAG
- [`agent-budget`](https://github.com/MukundaKatta/agent-budget) — production retry/budget primitive for LLM and agent calls

## Install from this index

```bash
pip install --index-url https://mukundakatta.github.io/python-package-index/simple/ \
    bedrock-ops embspec agent-budget
```

If your environment is locked and you also need PyPI for runtime deps:

```bash
pip install \
    --index-url https://mukundakatta.github.io/python-package-index/simple/ \
    --extra-index-url https://pypi.org/simple/ \
    bedrock-ops
```

## Why

PyPI's "too many new projects created" cap fired when these three packages were submitted in quick succession and has stayed sticky for >24 hours pending admin review. This index lets users install from the authoritative GitHub Release artifacts via standard `pip` tooling without waiting on PyPI.

The index points at GitHub Release wheels and sdists with verified `#sha256=...` fragments, so `pip` performs the same hash-check it would for a PyPI-hosted artifact.

## Layout

```
simple/
├── index.html               # PEP 503 root: list of projects
├── bedrock-ops/index.html
├── embspec/index.html
└── agent-budget/index.html
```

Each project's `index.html` lists the wheel and sdist with absolute URLs to the corresponding GitHub Release asset.

## Updating

When a new version of any package ships:

1. Compute the new wheel's `sha256` (`shasum -a 256 *.whl`)
2. Add a new `<a>` entry to `simple/<package>/index.html` pointing at the new GitHub Release URL
3. Commit and push; GitHub Pages rebuilds within ~60s

Old version entries should remain — pip resolves the latest matching version from the listed set.

## License

The hosted artifacts retain their upstream licenses (Apache-2.0). The index itself is CC0.
