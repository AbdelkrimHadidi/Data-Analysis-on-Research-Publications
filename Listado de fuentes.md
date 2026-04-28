## 3. Fuentes de Datos

**Nota**: Para el desarollo de la ontología no se ha usado todas las fuentes propuestas pero se han dejado para uso futuro.

El grafo se construye a partir de seis fuentes externas, combinando **APIs REST** y **endpoints SPARQL** para asegurar tanto una amplia cobertura de datos como un alto nivel de riqueza semántica.


| Fuente                               | Tipo de acceso    | Función principal                                                                      |
| ------------------------------------ | ----------------- | -------------------------------------------------------------------------------------- |
| OpenAlex                             | API REST          |  Datos bibliográficos (publicaciones, autores, instituciones y temas) |
| ORCID                                | API REST          | Identificación y trayectoria de investigadores                                         |
| ROR                                  | API REST          | Estandarización de organizaciones de investigación                                     |
| OpenAIRE                             | API REST + SPARQL | Información sobre financiación y proyectos                                             |
| ORKG (Open Research Knowledge Graph) | SPARQL            | Representación estructurada del conocimiento científico                                |
| Wikidata                             | SPARQL            | Enriquecimiento semántico de los datos                                                 |

### 3.1 OpenAlex (API REST)

Nos da la fuente bibliográfica central. Se extraen:

- **Publicaciones**: título, resumen, DOI, año, tipo, revista, número de citas y referencias.
- **Autores**: identificadores OpenAlex y ORCID, nombre y posición de autoría.
- **Instituciones**: identificador ROR, nombre, país y tipo.
- **Conceptos / Topics**: descriptores temáticos jerárquicos asociados a cada publicación.

**Entidades a las que contribuye:** `Paper`, `Person`, `Organization`, `Topic`.

### 3.2 ORCID (API REST)

Repositorio de identidades de investigadores. Aporta:

- Identificador ORCID iD persistente.
- Nombre completo, biografía y áreas de especialización declaradas.
- Historial de afiliaciones (educación y empleo).
- Lista de publicaciones reivindicadas por el investigador.

**Entidades a las que contribuye:** `Person`, y de forma complementaria `Organization` y `Paper` mediante las relaciones de afiliación y autoría.

### 3.3 ROR — Research Organization Registry (API REST)

Registro de organizaciones dedicadas a la investigación. Proporciona:

- Identificador ROR persistente.
- Nombre oficial y denominaciones alternativas.
- Tipo de organización (universidad, hospital, centro de investigación, etc.).
- País, ciudad y coordenadas geográficas.
- Relaciones jerárquicas (institución matriz, subunidades).

**Entidades a las que contribuye:** `Organization`.

### 3.4 OpenAIRE (API REST + SPARQL)

Aporta información sobre el contexto de financiación y proyectos europeos:

- Proyectos de investigación, número de subvención y entidad financiadora.
- Vinculación entre publicaciones y proyectos financiadores.
- Identificadores cruzados (DOI, ORCID, ROR) que permiten consolidar las entidades.

**Entidades a las que contribuye:** `Paper`, `Organization` y `Person`, principalmente como fuente de validación cruzada y vinculación con instituciones financiadoras.

### 3.5 ORKG — Open Research Knowledge Graph (SPARQL)

Grafo de conocimiento que representa contribuciones científicas de manera estructurada. Permite extraer:

- Contribuciones asociadas a publicaciones (problema abordado, método, resultados).
- Comparaciones entre trabajos sobre un mismo problema.
- Relaciones semánticas entre conceptos de investigación.

**Entidades a las que contribuye:** `Paper` y `Topic`.

### 3.6 Wikidata (SPARQL)

Base de conocimiento de enriquecimiento semántico. Aporta:

- Vínculos con conceptos biomédicos (enfermedades, fármacos, técnicas).
- Nacionalidades de los autores

**Entidades a las que contribuye:** `Topic` `Person`.
