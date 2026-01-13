# Store Layout JSON Example

## Overview

This document provides a complete JSON example of a store layout structure, showing the hierarchical organization from store to product placement.

## Complete Store Layout JSON

```json
{
  "store": {
    "storeId": "STORE-001",
    "name": "Supermarket Downtown",
    "address": {
      "street": "123 Main St",
      "city": "City",
      "state": "State",
      "zipCode": "12345"
    },
    "format": "SUPERMARKET",
    "size": 50000,
    "layout": "STANDARD",
    "constraints": {
      "maxGondolaHeight": 84,
      "aisleWidth": 8,
      "ceilingHeight": 12,
      "floorSpace": 50000
    }
  },
  "aisles": [
    {
      "aisleId": "AISLE-001",
      "storeId": "STORE-001",
      "number": 5,
      "name": "Beverages",
      "category": "BEVERAGES",
      "length": 60,
      "width": 8,
      "gondolas": [
        {
          "gondolaId": "GONDOLA-001",
          "number": 1,
          "type": "STANDARD",
          "width": 48,
          "depth": 24,
          "height": 84,
          "modules": [
            {
              "moduleId": "MODULE-001-L",
              "side": "LEFT",
              "width": 24,
              "depth": 18,
              "shelves": [
                {
                  "shelfId": "SHELF-001",
                  "level": 1,
                  "height": 12,
                  "depth": 18,
                  "width": 24,
                  "maxWeight": 1000,
                  "positions": [
                    {
                      "positionId": "POS-001",
                      "index": 1,
                      "x": 0,
                      "width": 6,
                      "depth": 18
                    },
                    {
                      "positionId": "POS-002",
                      "index": 2,
                      "x": 6,
                      "width": 6,
                      "depth": 18
                    },
                    {
                      "positionId": "POS-003",
                      "index": 3,
                      "x": 12,
                      "width": 6,
                      "depth": 18
                    },
                    {
                      "positionId": "POS-004",
                      "index": 4,
                      "x": 18,
                      "width": 6,
                      "depth": 18
                    }
                  ]
                },
                {
                  "shelfId": "SHELF-002",
                  "level": 2,
                  "height": 24,
                  "depth": 18,
                  "width": 24,
                  "maxWeight": 800,
                  "positions": [
                    {
                      "positionId": "POS-005",
                      "index": 1,
                      "x": 0,
                      "width": 6,
                      "depth": 18
                    },
                    {
                      "positionId": "POS-006",
                      "index": 2,
                      "x": 6,
                      "width": 6,
                      "depth": 18
                    },
                    {
                      "positionId": "POS-007",
                      "index": 3,
                      "x": 12,
                      "width": 6,
                      "depth": 18
                    },
                    {
                      "positionId": "POS-008",
                      "index": 4,
                      "x": 18,
                      "width": 6,
                      "depth": 18
                    }
                  ]
                },
                {
                  "shelfId": "SHELF-003",
                  "level": 3,
                  "height": 36,
                  "depth": 18,
                  "width": 24,
                  "maxWeight": 600,
                  "positions": [
                    {
                      "positionId": "POS-009",
                      "index": 1,
                      "x": 0,
                      "width": 6,
                      "depth": 18
                    },
                    {
                      "positionId": "POS-010",
                      "index": 2,
                      "x": 6,
                      "width": 6,
                      "depth": 18
                    },
                    {
                      "positionId": "POS-011",
                      "index": 3,
                      "x": 12,
                      "width": 6,
                      "depth": 18
                    },
                    {
                      "positionId": "POS-012",
                      "index": 4,
                      "x": 18,
                      "width": 6,
                      "depth": 18
                    }
                  ]
                },
                {
                  "shelfId": "SHELF-004",
                  "level": 4,
                  "height": 60,
                  "depth": 18,
                  "width": 24,
                  "maxWeight": 500,
                  "positions": [
                    {
                      "positionId": "POS-013",
                      "index": 1,
                      "x": 0,
                      "width": 6,
                      "depth": 18
                    },
                    {
                      "positionId": "POS-014",
                      "index": 2,
                      "x": 6,
                      "width": 6,
                      "depth": 18
                    },
                    {
                      "positionId": "POS-015",
                      "index": 3,
                      "x": 12,
                      "width": 6,
                      "depth": 18
                    },
                    {
                      "positionId": "POS-016",
                      "index": 4,
                      "x": 18,
                      "width": 6,
                      "depth": 18
                    }
                  ]
                },
                {
                  "shelfId": "SHELF-005",
                  "level": 5,
                  "height": 72,
                  "depth": 18,
                  "width": 24,
                  "maxWeight": 400,
                  "positions": [
                    {
                      "positionId": "POS-017",
                      "index": 1,
                      "x": 0,
                      "width": 6,
                      "depth": 18
                    },
                    {
                      "positionId": "POS-018",
                      "index": 2,
                      "x": 6,
                      "width": 6,
                      "depth": 18
                    },
                    {
                      "positionId": "POS-019",
                      "index": 3,
                      "x": 12,
                      "width": 6,
                      "depth": 18
                    },
                    {
                      "positionId": "POS-020",
                      "index": 4,
                      "x": 18,
                      "width": 6,
                      "depth": 18
                    }
                  ]
                }
              ]
            },
            {
              "moduleId": "MODULE-001-R",
              "side": "RIGHT",
              "width": 24,
              "depth": 18,
              "shelves": [
                {
                  "shelfId": "SHELF-021",
                  "level": 1,
                  "height": 12,
                  "depth": 18,
                  "width": 24,
                  "maxWeight": 1000,
                  "positions": [
                    {
                      "positionId": "POS-021",
                      "index": 1,
                      "x": 0,
                      "width": 6,
                      "depth": 18
                    }
                  ]
                }
              ]
            }
          ]
        }
      ]
    }
  ]
}
```

## Planogram with Product Placements

```json
{
  "planogramId": "PLANO-001",
  "name": "Beverages Aisle 5 - Q1 2024",
  "storeId": "STORE-001",
  "category": "BEVERAGES",
  "version": 1,
  "status": "PUBLISHED",
  "productPlacements": [
    {
      "placementId": "PLACE-001",
      "productId": "PROD-001",
      "productName": "Coca-Cola 2L",
      "positionId": "POS-013",
      "shelfId": "SHELF-004",
      "shelfLevel": 4,
      "facings": 3,
      "depth": 2,
      "startDate": "2024-01-15",
      "endDate": "2024-03-15",
      "rules": ["HIGH_ROTATION_EYE_LEVEL", "BRAND_BLOCKING"]
    },
    {
      "placementId": "PLACE-002",
      "productId": "PROD-002",
      "productName": "Pepsi 2L",
      "positionId": "POS-014",
      "shelfId": "SHELF-004",
      "shelfLevel": 4,
      "facings": 2,
      "depth": 2,
      "startDate": "2024-01-15",
      "endDate": "2024-03-15",
      "rules": ["HIGH_ROTATION_EYE_LEVEL", "BRAND_BLOCKING"]
    }
  ]
}
```

## Related Documents

- `docs/04-store-layout-model.md` - Store layout model
- `examples/planogram-data-model-example.md` - Data model examples
