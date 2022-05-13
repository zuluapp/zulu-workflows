<div align="center">
  <a href="https://github.com/zuluapp/zulu-workflows">
    <img src="https://avatars.githubusercontent.com/u/96034374?s=200&v=4" alt="Logo" width="100" height="100">
  </a>

  <h3 align="center">Zulu Workflows Configuration</h3>
</div>

## Getting Started

1. Create your Feature Branch (`git checkout -b feature/[TICKET-ID]`)
2. Commit your Changes (`git commit -m '[TICKET-ID]'`)
3. Push to the Branch (`git push origin feature/[TICKET-ID]`)
4. Open a Pull Request

<p align="right">(<a href="#top">back to top</a>)</p>


<!-- CONTACT -->
## Contact

* Adrian - [@adrianhorizon](https://github.com/adrianhorizon)

__Project Link:__ [https://github.com/zuluapp/zulu-workflows](https://github.com/zuluapp/zulu-workflows)

<p align="right">(<a href="#top">back to top</a>)</p>


### example

```
name: Release

on:
  workflow_dispatch:
  push:
    branches: [develop]

jobs:
  release:
    uses: zuluapp/zulu-workflows/.github/workflows/release.yml@main
    secrets:
      github-token: ${{ secrets.GITHUB_TOKEN }}

  lint:
    needs: release
    uses: zuluapp/zulu-workflows/.github/workflows/lint.yml@main

  test:
    needs: lint
    uses: zuluapp/zulu-workflows/.github/workflows/test.yml@main

  sonar-cloud:
    needs: test
    uses: zuluapp/zulu-workflows/.github/workflows/build-security.yml@main
    secrets:
      github-token: ${{ secrets.GITHUB_TOKEN }}
      sonar: ${{ secrets.SONAR_TOKEN }}
```
