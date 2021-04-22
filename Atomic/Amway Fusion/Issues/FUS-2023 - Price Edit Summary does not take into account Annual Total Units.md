Completed on [[2021-04-21]]. 


## Implementation Hypothesis
-   Right now the \`modules/graphql-api/resolvers/price-edit-report.ts\` returns the summary data in USD without then converting it to the local currency.

-   The resolver must be updated to properly convert the summary information to the local currency.

-   A version of the getRedactableSummary from the Appraise Lite Report Summary will have to be implemented in the Price Edit Report resolver. Right now \`marketToTargetBudgetExchangeRateFormatter\` is being used but is not correctly performing the conversion.


Fixed in the end by setting a base currency to US to convert from because the summary results are returned in USD on report and sandbox.