# Searching through the collection

Searching through a Tree will allow you to immediately jump to the right `tree:Node`.

The `tree:Node` in this case does not need to be explicitly defined, but the current URL need to be linked to the collection cfr. [1. Discovery](1-discovery.md). The collection itself then __must__ have a `hydra:search` property, describing a search form. For different use cases, the Tree Ontology specifies different search forms (add your own through a pull request):

## 1. Geospatial tiles search form

Example:
```json
{
   "@context": {
     ...
   },
  "@id": "https://tiles.openplanner.team/planet/14/8411/5485/",
  "tiles:zoom": 14,
  "tiles:longitudeTile": 8411,
  "tiles:latitudeTile": 5485,
  "dcterms:isPartOf": {
    "@id": "https://tiles.openplanner.team/planet/",
    "@type": "hydra:Collection",
    "dcterms:license": "http://opendatacommons.org/licenses/odbl/1-0/",
    "dcterms:rights": "http://www.openstreetmap.org/copyright",
    "hydra:search": {
      "@type": "hydra:IriTemplate",
      "hydra:template": "https://tiles.openplanner.team/planet/{z}/{x}/{y}",
      "hydra:variableRepresentation": "hydra:BasicRepresentation",
      "hydra:mapping": [
        {
          "@type": "hydra:IriTemplateMapping",
          "hydra:variable": "x",
          "hydra:property": "tiles:longitudeTile",
          "hydra:required": true
        },
        {
          "@type": "hydra:IriTemplateMapping",
          "hydra:variable": "y",
          "hydra:property": "tiles:latitudeTile",
          "hydra:required": true
        },
        {
          "@type": "hydra:IriTemplateMapping",
          "hydra:variable": "z",
          "hydra:property": "tiles:zoom",
          "hydra:required": true
        }
      ]
    },
    "hydra:member": [ ..., ... ]
  }
}
```

This search form describes a specific search form that uses a quad tree. The zoom level describes the depth, the longitudeTile and latitudeTile describe the x and y index of the fragmentation. (e.g., on zoom level 0, there’s 1 tile, on zoom level 1, there are 4 tiles, etc.)

This SPARQL query can be used to discover a geospatial search form. Mind that the ?currentUrl variable needs to be filled out.

### 2. Searching through an ordered list of objects

#### 2.1 Time series

#### 2.2 Linked Connections

### 3. Skip Graphs

Using this specification, you can as well model skip graphs. //TODO: Harm

