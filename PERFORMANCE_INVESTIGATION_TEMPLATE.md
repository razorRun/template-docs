# Performance Investigation Template

**Investigation Area**: [FEATURE_NAME]  
**Author**: [Your Name]  
**Date**: [YYYY-MM-DD]  
**Info**: []  

## 1. Current Implementation Overview

### 1.1 Component Architecture
```
└── ParentComponent
    ├── ChildComponent1
    ├── ChildComponent2
    └── ChildComponent3
```

### 1.2 Key Files
- **Main Component**: `path/to/component.tsx`
- **Hooks**: `path/to/hooks.ts`
- **Redux Actions**: `path/to/actions.ts`
- **GraphQL Queries**: `path/to/queries.graphql`

### 1.3 Data Flow
```
User Action → Component → Hook → Redux Action → GraphQL → API
                ↓                      ↓
            Local State            Redux Store
```

## 2. Performance Metrics & Timing Analysis

### 2.1 Component Mount Timeline
```
T+0ms    : User interaction/navigation trigger
T+[X]ms  : Component mount start
T+[X]ms  : Data fetch initiated
T+[X]ms  : Network response received
T+[X]ms  : State update complete
T+[X]ms  : First meaningful paint
T+[X]ms  : Fully interactive
```

### 2.2 Network Calls Analysis
| API Call | Trigger | Duration | Size | Frequency | Cached |
|----------|---------|----------|------|-----------|--------|
| Query1   | onMount | Xms      | XKB  | Once      | No     |
| Query2   | onScroll| Xms      | XKB  | Multiple  | Yes    |

### 2.3 Rendering Performance
- **Initial Render**: Xms
- **Re-renders**: X times during [action]
- **FPS during interaction**: X fps
- **JS Thread Blocking**: Xms

## 3. Data Analysis

### 3.1 GraphQL Queries
```graphql
query CurrentQuery {
  field {
    # Current fields being fetched
  }
}
```

**Analysis**:
- **Response Size**: X KB
- **Fields Used**: X/Y (X%)
- **Overfetching**: [List unused fields]
- **N+1 Problems**: Yes/No

### 3.2 Redux State
```javascript
{
  feature: {
    // Current state structure
  }
}
```

**Analysis**:
- **State Size**: X KB
- **Update Frequency**: X/minute
- **Normalization**: Yes/No
- **Selector Complexity**: High/Medium/Low

### 3.3 Caching Analysis
- **Current Caching**: None/Memory/Persistent
- **Cache Hit Rate**: X%
- **TTL**: X seconds
- **Invalidation Strategy**: [Description]

## 4. Performance Test Results

### 4.1 Test Scenarios

#### Scenario 1: [Initial Load]
- **Conditions**: Cold start, cleared cache
- **Metrics**:
  - Time to Interactive: Xs
  - Memory Usage: XMB
  - CPU Usage: X%

#### Scenario 2: [User Interaction]
- **Conditions**: [Describe interaction]
- **Metrics**:
  - Response Time: Xms
  - Frame Rate: X fps
  - Memory Delta: +XMB

#### Scenario 3: [Background Return]
- **Conditions**: App in background for X minutes
- **Metrics**:
  - Refresh Time: Xs
  - Stale Data Shown: Yes/No

### 4.2 Device-Specific Results
| Device Type | Load Time | Memory | FPS | Issues |
|-------------|-----------|--------|-----|--------|
| High-end    | Xs        | XMB    | 60  | None   |
| Mid-range   | Xs        | XMB    | 45  | [List] |
| Low-end     | Xs        | XMB    | 30  | [List] |

## 5. Identified Issues

### 5.1 Critical Performance Issues
1. **Issue**: [Description]
   - **Impact**: High/Medium/Low
   - **Root Cause**: [Explanation]
   - **Affected Users**: X%

### 5.2 Architecture Issues
1. **Issue**: [Description]
   - **Current Impact**: Xms delay
   - **Scalability Concern**: Yes/No

### 5.3 Data Management Issues
1. **Overfetching**: [Description]
2. **State Management**: [Description]
3. **Caching**: [Description]

## 6. Optimization Recommendations

### 6.1 Quick Wins (< 1 day)
| Optimization | Implementation | Expected Impact |
|--------------|----------------|-----------------|
| Reduce query fields | Remove unused fields | -X% data size |
| Add memoization | useMemo/useCallback | -X re-renders |
| Pagination | Load X items initially | -X% load time |

### 6.2 Medium Effort (1-3 days)
| Optimization | Implementation | Expected Impact |
|--------------|----------------|-----------------|
| Implement caching | Add cache layer | -X% API calls |
| Lazy loading | Load on demand | -X% initial load |
| State normalization | Refactor Redux | -X% memory |

### 6.3 Long Term (> 3 days)
| Optimization | Implementation | Expected Impact |
|--------------|----------------|-----------------|
| Architecture refactor | [Description] | -X% overall |
| Backend optimization | [Description] | -Xms latency |
| Native module | [Description] | -X% CPU usage |

## 7. Implementation Plan

### 7.1 Prioritized Roadmap
1. **Week 1**: Quick wins
   - [ ] Task 1 (Impact: -Xms)
   - [ ] Task 2 (Impact: -X%)

2. **Week 2-3**: Medium improvements
   - [ ] Task 3 (Impact: -Xms)
   - [ ] Task 4 (Impact: -X%)

3. **Month 2**: Long-term solutions
   - [ ] Task 5 (Impact: -Xms)

### 7.2 Success Criteria
- **Primary Goal**: Reduce [metric] from X to Y
- **Secondary Goals**:
  - Improve [metric] by X%
  - Reduce [metric] by X%

## 8. Measurement & Validation

### 8.1 Performance Monitoring Setup
```javascript
// Example performance marking
performance.mark('feature-start');
// ... feature code
performance.mark('feature-end');
performance.measure('feature-duration', 'feature-start', 'feature-end');
```

### 8.2 Key Metrics to Track
- **User-facing**: Time to Interactive, FPS, Responsiveness
- **Technical**: Memory usage, CPU usage, Network calls
- **Business**: User engagement, Error rates

### 8.3 A/B Testing Plan
- **Control**: Current implementation
- **Variant**: Optimized version
- **Metrics**: [List key metrics]
- **Duration**: X days

## 9. Rollback Strategy

### 9.1 Feature Flags
```javascript
if (FeatureFlags.isEnabled('optimized-feature')) {
  // New implementation
} else {
  // Current implementation
}
```

### 9.2 Monitoring Alerts
- Alert if performance degrades by >X%
- Alert if error rate increases by >X%

## 10. Documentation & Knowledge Sharing

### 10.1 Findings Documentation
- [ ] Update team wiki
- [ ] Create ADR (Architecture Decision Record)
- [ ] Share in team meeting

### 10.2 Lessons Learned
- What worked well
- What didn't work
- Recommendations for future

---

## Quick Reference: Common Patterns

### GraphQL Optimization
```graphql
# Before
query { content { ...AllFields } }

# After  
query { content { id title image { url } } }
```

### Redux Optimization
```javascript
// Before
const items = useSelector(state => state.items.map(transform));

// After
const items = useSelector(createSelector(
  [state => state.items],
  items => items.map(transform)
));
```

### Component Optimization
```javascript
// Before
<Child onClick={() => handle(id)} />

// After
const handleClick = useCallback(() => handle(id), [id]);
<Child onClick={handleClick} />
```

### Lazy Loading Pattern
```javascript
const Component = lazy(() => import('./Component'));
<Suspense fallback={<Skeleton />}>
  <Component />
</Suspense>
```

---
