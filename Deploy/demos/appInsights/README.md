# Demo A/B Testing
1. Open web app
1. Log in (keep username consistent - password can be anything)
1. Add items to cart

# Custom App Insights Query
The query from the telemetry is:

```
customEvents 
| where timestamp > ago(45m)
| project timestamp, EventName = name, ProductTypeId = tostring(customDimensions.productTypeId), ProductId = tostring(customDimensions.productId), ProductName = tostring(customDimensions.productName), Price = todouble(customDimensions.productPrice)
| summarize sum(Price) by ProductTypeId
| render piechart 
```
