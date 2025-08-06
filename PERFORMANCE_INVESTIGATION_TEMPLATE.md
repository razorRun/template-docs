# Performance Investigation Template

**Investigation Area**: [FEATURE_NAME]  
**Background**: [Background and Hints]  
**Owner**: [Name]  
**Date**: [YYYY-MM-DD]

## 1. Baseline Metrics

### QA Team Baseline
- **Device**: [Pod/Mobile/TV]
- **Test Actions**: [List specific user actions tested]
- **Current Performance**: [Time measurements from QA]

### Dev Team Baseline  
- **Component Mount Time**: [X]ms
- **Network Calls**: [Number and timing]
- **Memory Usage**: [X]MB
- **FPS**: [X] fps

## 2. Network & Render Analysis

### GraphQL Queries
```graphql
query CurrentQuery {
  # Current fields
}
```
- **Response Size**: [X]KB
- **Fields Used vs Fetched**: [X/Y]
- **Unused Fields**: [List]

### Network Waterfall
| Call | Trigger | Duration | Size | 
|------|---------|----------|------|
| [API] | [When] | [X]ms | [X]KB |

### Component Tree & Timing
```
T+0ms    : User action
T+[X]ms  : Component mount
T+[X]ms  : Data fetch
T+[X]ms  : First render
T+[X]ms  : Interactive
```

## 3. Issues Identified

### Performance Problems
1. [Issue] - [Impact]
2. [Issue] - [Impact]

### React Native Optimizations Available
1. [Optimization] - [Expected gain]
2. [Optimization] - [Expected gain]

## 4. GraphQL Query Optimization (with Adrian)

### Current Queries Analysis
- [Query name]: [Issues found]
- [Query name]: [Issues found]

### Proposed Changes
- [Change]: [Expected impact]

## 5. Implementation Plan

### Quick Wins
- [ ] [Task] - [Timeline]
- [ ] [Task] - [Timeline]

### Medium Term
- [ ] [Task] - [Timeline]

## Investigation Checklist

### Setup
- [ ] QA baseline documented for target actions
- [ ] Dev baseline metrics established
- [ ] Performance monitoring tools configured

### Analysis
- [ ] Network waterfall analysed
- [ ] GraphQL queries reviewed
- [ ] Component performance profiled
- [ ] Memory usage checked

### Results
- [ ] Issues documented with impact
- [ ] React Native optimisations identified  
- [ ] GraphQL optimisation plan with Adrian
- [ ] Implementation plan created
