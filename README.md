# Compact GeoJSON schema project

The project is aimed to provide JSON schema for GeoJSON with minimal redundancy and reuse of definitions 
in order to enable easy extension of the schema.

## GeoJSON schema and validation

GeoJSON schemas can be found at data/ folder.

Schemas use the references to external files.

## GeoJSON validation
To validate JSON data against the GeoJSON schema following tools can be used:

### GeoJSON schema tool

For JSON validation the GeoJSON schema tool is available:

https://github.com/geojson/schema

This tool contains valid and invalid samples of GeoJSON data. It also can be used to generate GeoJSON schema. 

Unfortunately it doesn't support references and puts all the definitions in single file for each entity.

Compact GeoJSON schema removes duplication by using $ref for geometry entities.

### jsonschema (Python)

Follow the instructions to install jsonschema tool:

https://pypi.org/project/jsonschema/

Usage:

```
jsonschema -i data/jumble.geojson/valid/frauenkopf_sm.geojson  data/jumble.geojson.schema/GeoJSON.json
```

```
jsonschema -i data/jumble.geojson/invalid/frauenkopf_sm_inv.geojson  data/jumble.geojson.schema/GeoJSON.json
```

In order to check that modified Jumble JSON schema handles normal GeoJSON correctly:

1. Clone https://github.com/geojson/schema on the same level directory as jumble to obtain official GeoJSON's test samples.

2. Run validate_geojson_with_jumble.sh - it should return no error message.

3. Run check_invalid_geojson.sh - it should return error message for each test sample.

