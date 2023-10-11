# Summary of tests

## Stac validation
no error

## core validation
- pystac validation error: Validation failed for Collection at https://datacube-stage.services.geo.ca/stac/api/collections/hrdem with ID hrdem against schema at https://schemas.stacspec.org/v1.0.0/collection-spec/json-schema/collection.json

## collection validation
- [Collections] : GET https://datacube-stage.services.geo.ca/stac/api/collections failed stac-validator validation: [{'version': '1.0.0', 'path': None, 'schema': ['https://schemas.stacspec.org/v1.0.0/collection-spec/json-schema/collection.json'], 'valid_stac': False, 'error_type': 'JSONSchemaValidationError', 'error_message': "'' is too short. Error is in description "}]

## item-search validation
- [Item Search] : GET https://datacube-stage.services.geo.ca/stac/api/search params={'datetime': '/1984-04-12T23:20:50.52Z/1985-04-12T23:20:50.52Z'} body= had unexpected status code 200 instead of 400: 
invalid datetime returned non-400 status code
- [Item Search] : GET https://datacube-stage.services.geo.ca/stac/api/search params={'datetime': '1984-04-12T23:20:50.52Z/1985-04-12T23:20:50.52Z/'} body= had unexpected status code 200 instead of 400: 
invalid datetime returned non-400 status code
- [Item Search] : GET https://datacube-stage.services.geo.ca/stac/api/search params={'datetime': '/1984-04-12T23:20:50.52Z/1985-04-12T23:20:50.52Z/'} body= had unexpected status code 200 instead of 400: invalid datetime returned non-400 status code
- [Item Search] : GET https://datacube-stage.services.geo.ca/stac/api/search params={'intersects': '{"type": "GeometryCollection", "geometries": [{"type": "Point", "coordinates": [100.0, 0.0]}, {"type": "LineString", "coordinates": [[101.0, 0.0], [102.0, 1.0]]}]}'} body= had unexpected status code 400 instead of 200:
- [Item Search] : POST https://datacube-stage.services.geo.ca/stac/api/search params=None body={"intersects": {"type": "GeometryCollection", "geometries": [{"type": "Point", "coordinates": [100.0, 0.0]}, {"type": "LineString", "coordinates": [[101.0, 0.0], [102.0, 1.0]]}]}} had unexpected status code 400 instead of 200:

## transaction validation
- DEBUG:urllib3.connectionpool:https://datacube-stage.services.geo.ca:443 "PATCH /stac/api/collections/river-ice-canada-archive/items/S2A_47XNF_20230423_0_L2A HTTP/1.1" 405 31

## pagenation validation
- [Features] : GET https://datacube-stage.services.geo.ca/stac/api/collections/river-ice-canada-archive/items/S2A_47XNF_20230423_0_L2A is not a valid STAC object: '3.14' is not of type 'number'. Error is in properties -> eo:cloud_cover

# Recommendations
- can be used to validate STAC format
- can be used to validate a collection (not including transactional operations)
- can be used to validate an item (including transactional operations, except PATCH)
- can be used to validate item-search (requirement specific query string and auth settings)
- can be used to validate pagination