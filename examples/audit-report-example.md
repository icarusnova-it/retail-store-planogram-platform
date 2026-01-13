# Audit Report Example

## Overview

This document provides examples of audit reports generated after planogram execution and compliance audits.

## Execution Audit Report

### Complete Execution Audit Report

```json
{
  "auditId": "AUDIT-001",
  "auditType": "EXECUTION_AUDIT",
  "planogramId": "PLANO-001",
  "storeId": "STORE-001",
  "storeName": "Supermarket Downtown",
  "auditDate": "2024-01-20T10:00:00Z",
  "auditor": "auditor@retail.com",
  "overallStatus": "PASSED",
  "complianceScore": 92.5,
  "summary": {
    "totalPositions": 100,
    "checkedPositions": 100,
    "compliantPositions": 92,
    "nonCompliantPositions": 8,
    "complianceRate": 92.0
  },
  "executionDetails": {
    "executionDate": "2024-01-15T14:00:00Z",
    "executedBy": "store.manager@retail.com",
    "executionTime": "2.5 hours",
    "photosCaptured": 50,
    "checklistCompleted": true
  },
  "findings": {
    "compliant": [
      {
        "positionId": "POS-001",
        "productId": "PROD-001",
        "productName": "Coca-Cola 2L",
        "status": "COMPLIANT",
        "details": "Product placed correctly, facings correct, position correct"
      }
    ],
    "nonCompliant": [
      {
        "positionId": "POS-010",
        "productId": "PROD-010",
        "productName": "Product X",
        "status": "NON_COMPLIANT",
        "discrepancy": "Wrong product in position",
        "expected": "PROD-010",
        "actual": "PROD-011",
        "severity": "MEDIUM",
        "recommendation": "Replace with correct product"
      },
      {
        "positionId": "POS-015",
        "productId": "PROD-015",
        "productName": "Product Y",
        "status": "NON_COMPLIANT",
        "discrepancy": "Incorrect facings",
        "expected": 3,
        "actual": 2,
        "severity": "LOW",
        "recommendation": "Add 1 facing"
      }
    ]
  },
  "photos": [
    {
      "photoId": "PHOTO-001",
      "positionId": "POS-001",
      "url": "https://storage.example.com/photos/photo-001.jpg",
      "timestamp": "2024-01-15T14:30:00Z",
      "validated": true
    }
  ],
  "recommendations": [
    "Correct product placement at position POS-010",
    "Add facing at position POS-015",
    "Review execution process for accuracy"
  ]
}
```

## Compliance Audit Report

### Compliance Audit Report

```json
{
  "auditId": "AUDIT-002",
  "auditType": "COMPLIANCE_AUDIT",
  "planogramId": "PLANO-001",
  "storeId": "STORE-001",
  "auditDate": "2024-01-20T10:00:00Z",
  "auditor": "compliance@retail.com",
  "overallStatus": "PASSED",
  "complianceScore": 88.0,
  "complianceChecks": {
    "ruleCompliance": {
      "score": 95.0,
      "status": "PASSED",
      "totalRules": 20,
      "compliantRules": 19,
      "violations": 1
    },
    "brandCompliance": {
      "score": 90.0,
      "status": "PASSED",
      "totalBrands": 10,
      "compliantBrands": 9,
      "violations": 1
    },
    "regulatoryCompliance": {
      "score": 100.0,
      "status": "PASSED",
      "totalChecks": 5,
      "compliantChecks": 5,
      "violations": 0
    },
    "categoryCompliance": {
      "score": 95.0,
      "status": "PASSED",
      "totalCategories": 8,
      "compliantCategories": 8,
      "violations": 0
    }
  },
  "violations": [
    {
      "violationId": "VIOL-001",
      "type": "RULE_VIOLATION",
      "ruleId": "WEIGHT_CONSTRAINT",
      "severity": "HIGH",
      "productId": "PROD-010",
      "message": "Product weight exceeds shelf capacity",
      "recommendation": "Move to lower shelf"
    },
    {
      "violationId": "VIOL-002",
      "type": "BRAND_VIOLATION",
      "brandId": "BRAND-002",
      "severity": "MEDIUM",
      "message": "Minimum facings not met",
      "recommendation": "Increase facings to 4"
    }
  ],
  "recommendations": [
    "Address weight constraint violation",
    "Correct brand compliance issue",
    "Review planogram for other potential issues"
  ]
}
```

## Performance Audit Report

### Performance Audit Report

```json
{
  "auditId": "AUDIT-003",
  "auditType": "PERFORMANCE_AUDIT",
  "planogramId": "PLANO-001",
  "storeId": "STORE-001",
  "auditDate": "2024-01-25T10:00:00Z",
  "auditor": "analytics@retail.com",
  "performancePeriod": {
    "startDate": "2024-01-15",
    "endDate": "2024-01-25",
    "duration": "10 days"
  },
  "performanceMetrics": {
    "salesImpact": {
      "categorySalesBefore": 50000,
      "categorySalesAfter": 57500,
      "salesIncrease": 7500,
      "salesIncreasePercent": 15.0,
      "status": "POSITIVE"
    },
    "complianceRate": {
      "executionCompliance": 92.0,
      "placementCompliance": 90.0,
      "ruleCompliance": 95.0,
      "overallCompliance": 92.3,
      "status": "GOOD"
    },
    "spaceEfficiency": {
      "salesPerSquareFoot": 125.50,
      "salesPerLinearFoot": 45.20,
      "spaceUtilization": 95.0,
      "status": "EFFICIENT"
    },
    "executionQuality": {
      "executionTime": "2.5 hours",
      "executionAccuracy": 92.0,
      "photoQuality": 98.0,
      "status": "GOOD"
    }
  },
  "insights": [
    "Planogram execution resulted in 15% sales increase",
    "High compliance rate (92%) indicates good execution",
    "Space efficiency improved with optimized placement",
    "Execution quality is good with high accuracy"
  ],
  "optimizationOpportunities": [
    "Consider increasing facings for high-rotation products",
    "Optimize space allocation for underperforming categories",
    "Review placement rules based on sales data"
  ],
  "recommendations": [
    "Continue current planogram approach",
    "Monitor performance over longer period",
    "Consider optimizations based on data"
  ]
}
```

## Human-Readable Audit Report

### Execution Audit Report (PDF Format)

```
================================================================================
PLANOGRAM EXECUTION AUDIT REPORT
================================================================================

Audit Information
-----------------
Audit ID: AUDIT-001
Planogram ID: PLANO-001
Store: Supermarket Downtown (STORE-001)
Audit Date: January 20, 2024
Auditor: compliance@retail.com

Executive Summary
-----------------
Overall Status: PASSED
Compliance Score: 92.5%
Total Positions Checked: 100
Compliant Positions: 92
Non-Compliant Positions: 8

Execution Details
-----------------
Execution Date: January 15, 2024
Executed By: store.manager@retail.com
Execution Time: 2.5 hours
Photos Captured: 50
Checklist Completed: Yes

Findings
--------

Compliant Positions: 92
- Product placements match planogram
- Facings correct
- Positions correct
- Category grouping correct

Non-Compliant Positions: 8

1. Position POS-010
   - Issue: Wrong product in position
   - Expected: PROD-010 (Product X)
   - Actual: PROD-011 (Product Y)
   - Severity: MEDIUM
   - Recommendation: Replace with correct product

2. Position POS-015
   - Issue: Incorrect facings
   - Expected: 3 facings
   - Actual: 2 facings
   - Severity: LOW
   - Recommendation: Add 1 facing

Recommendations
---------------
1. Correct product placement at position POS-010
2. Add facing at position POS-015
3. Review execution process for accuracy
4. Provide additional training on planogram execution

================================================================================
END OF REPORT
================================================================================
```

## Related Documents

- `docs/07-operations-and-auditing.md` - Operations and auditing
- `docs/08-analytics-and-optimization.md` - Analytics and optimization
