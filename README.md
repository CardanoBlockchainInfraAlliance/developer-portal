
# CBIA Developer Tools Compatibility Matrix Project

This page serves to publish Project updates and Technical aspects for Catalyst funded proposal [CBIA - Add Developer Tool Compatibility Matrix to Cardano Developers Portal](https://projectcatalyst.io/funds/11/cardano-open-developers/cbia-add-developer-tool-compatibility-matrix-to-cardano-developers-portal).

## Milestone #1 - “Ms1-Data”

### Stakeholder Updates

Regarding the Stakeholders side of this milestone, we confirm we are now in contact with the Cardano Foundation Dev Portal maintainers, having chatted with [Tommy](https://x.com/adatainment) (CF Community Team) and met with [Bora Oben](https://www.linkedin.com/in/boraoben) (Developer Advocate), who is in charge of overseeing changes to this portal.

We have also engaged with some Dev Portal tooling authors via a [GitHub issue on the portal’s repository](https://github.com/cardano-foundation/developer-portal/issues/1091) and gathered initial [indication of the compatibility of their tool with others](https://docs.google.com/spreadsheets/d/1IJ2LmhQpYqyL4M6hlg0YyVQDlqdqHy4VA54EehP0MLQ) from some CBIA members.

![Call between CBIA and Cardano Foundation](/readme_static/CBIAxCF_call.png)

### Technical Updates

Regarding the Technical side of this milestone, we have established a Data structure to enable the portal to gather the relationships and compatibility between different tools.

The data file located at `developer-portal/src/data/builder-tools.js` should be extended.

```js 
// Original data structure
{
    "title": "cardanocli-js",
    "description": "A library that wraps the cardano-cli in JavaScript.",
    "preview": "require('./builder-tools/cardanocli-js.png')",
    "website": "https://github.com/Berry-Pool/cardanocli-js",
    "getstarted": "/docs/get-started/cardanocli-js",
    "tags": ["javascript", "sdk"],
},
```

It will have a `releases` section, including `version`, `latest`, `dependencies` and `traits`.

```js
// Extended data structure
{
  "title": "cardanocli-js",
  "description": "A library that wraps the cardano-cli in JavaScript.",
  "preview": "require('./builder-tools/cardanocli-js.png')",
  "website": "https://github.com/Berry-Pool/cardanocli-js",
  "getstarted": "/docs/get-started/cardanocli-js",
  "tags": ["javascript", "sdk"],
  "releases": [
    {
      "version": "3.1.2",
      "latest": true,
      "dependencies": ["cardano-node"],
      "traits": ["babbage", "alonzo", "cip31", "cip32"]
    },
    {
      "version": "3.1.1",
      "dependencies": ["cardano-node"],
      "traits": ["alonzo"]
    }
  ]
}
```

To prove this, we have built the technical changes necessary to the Developer Portal, achieving an initial version of the code that will display these relationships and compatibility within the portal.

The repository can be found at https://github.com/Tanglius/cardano_matrix (its readme includes instructions to run it locally).

Here are a few screenshots exploring future use cases:
![Ms1-ScreenShot01.png](/readme_static/Ms1-ScreenShot01.png)
![Ms1-ScreenShot02.png](/readme_static/Ms1-ScreenShot02.png)
![Ms1-ScreenShot03.png](/readme_static/Ms1-ScreenShot03.png)
![Ms1-ScreenShot04.png](/readme_static/Ms1-ScreenShot04.png)


## Milestone #2 - “Ms2-Viz”

### Evidence of milestone completion

- Dependency Graph [running website](https://45b.io/cbia-infra-tools/tools-rels-compat/)

- Dependency Graph source code, was committed to the main repo in two commits:

  - [First commit](https://github.com/CardanoBlockchainInfraAlliance/developer-portal-cbia/commit/1708fd61b47fb762ab222781ed2405fcb1ac46b8) importing the visualzation tree, data and data-enriching script which we developed as a standalone

  - [Second commit](https://github.com/CardanoBlockchainInfraAlliance/developer-portal-cbia/commit/1708fd61b47fb762ab222781ed2405fcb1ac46b8) incorporating it onto the existing portal pages and style

- Dependency Graph documentation

  - We've included documentation in the repository itself [here](https://github.com/CardanoBlockchainInfraAlliance/developer-portal-cbia/blob/cbia-rels-compat/readme.cbia.md)



