---
name: optimize
description: Performance optimization suggestions and implementation
tags: [performance, optimization]
args:
  - name: path
    description: File or directory to optimize
    required: true
  - name: target
    description: What to optimize for
    default: speed
    options: [speed, memory, bundle-size, all]
---

# Performance Optimization

Optimize `{{path}}` for **{{target}}**.

## Analysis Steps

1. **Profile**: Identify the actual bottlenecks
2. **Measure**: Establish baseline performance
3. **Optimize**: Apply targeted improvements
4. **Verify**: Confirm improvements without regressions

## Optimization Targets

### Speed
- Reduce algorithmic complexity
- Cache expensive computations
- Avoid unnecessary work
- Use efficient data structures

### Memory
- Reduce allocations
- Release resources promptly
- Use streaming for large data
- Avoid memory leaks

### Bundle Size
- Remove unused dependencies
- Use tree-shaking effectively
- Lazy load where appropriate
- Compress and minify assets

## Output

Provide:
1. **Bottlenecks**: What's causing performance issues
2. **Recommendations**: Prioritized list of optimizations
3. **Implementation**: Code changes for top recommendations
4. **Expected Impact**: Estimated improvement for each change
5. **Trade-offs**: Any costs to consider (complexity, readability)
