
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

- Dependency Graph [running website here](https://45b.io/cbia-infra-tools/tools-rels-compat/). We highlight some features:

  - Button on the /tools/ landing page
![Ms2-ScreenShot01.png](/readme_static/Ms2-ScreenShot01.png)

  - Visualization /tools-rels-compat/ on first load.

![Ms2-ScreenShot02.png](/readme_static/Ms2-ScreenShot02.png)

  - `Expand all` show dependents for bech32, flagging some incompatibility in red.

![Ms2-ScreenShot03.png](/readme_static/Ms2-ScreenShot03.png)

  - Scrooling down shows other `Top-level` tools, highlighting compatibility in green.

![Ms2-ScreenShot04.png](/readme_static/Ms2-ScreenShot04.png)

  - Toggling to `All tools` and `Collapse all` lists all 84 tools on the platform.

![Ms2-ScreenShot05.png](/readme_static/Ms2-ScreenShot05.png)

  - `Ctrl+Click` on a particular tool shows all dependents; Hovering over one shouws info about its maker and description.

![Ms2-ScreenShot06.png](/readme_static/Ms2-ScreenShot06.png)

  - Toggling to `Dependencies` we call see all the tools that depend on a particular 'root' tool (Atlas in this case).

![Ms2-ScreenShot07.png](/readme_static/Ms2-ScreenShot07.png)

  - Clickign a particular Category allows us to see dependencies for example all the 'Smart Contracts' items.

![Ms2-ScreenShot08.png](/readme_static/Ms2-ScreenShot08.png)

  - `Ctrl+Click` allows us to add categories one by one.

![Ms2-ScreenShot09.png](/readme_static/Ms2-ScreenShot09.png)




- Dependency Graph **source code**, was committed to the main repo in two commits:

  - [First commit](https://github.com/CardanoBlockchainInfraAlliance/developer-portal-cbia/commit/1708fd61b47fb762ab222781ed2405fcb1ac46b8) importing the visualzation tree, data and data-enriching script which we developed as a standalone

  - [Second commit](https://github.com/CardanoBlockchainInfraAlliance/developer-portal-cbia/commit/1708fd61b47fb762ab222781ed2405fcb1ac46b8) incorporating it onto the existing portal pages and style

  - The current visualization is the result of greatly extending the data by using the formats outlined above, in Milestone 1
    - Here are the [Original](https://github.com/CardanoBlockchainInfraAlliance/developer-portal-cbia/blob/cbia-rels-compat/src/data/builder-tools/tools.js) and [New file](https://github.com/CardanoBlockchainInfraAlliance/developer-portal-cbia/blob/cbia-rels-compat/src/data/builder-tools/enriched-tools.js)

- Dependency Graph **documentation**

  - We've included documentation in the repository itself [here](https://github.com/CardanoBlockchainInfraAlliance/developer-portal-cbia/blob/cbia-rels-compat/readme.cbia.md)



