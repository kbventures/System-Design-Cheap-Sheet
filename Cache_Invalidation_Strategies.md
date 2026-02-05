## Cache Invalidation Strategies

### 1. Time-based expiration (TTL)
```
Timeline: 0min ──────────> 5min ──────────> 10min
          Cache   [VALID]   Expires   Refetch
          Set                 ❌         ✓
```
- ✅ Simple to implement
- ❌ Potentially stale data until expiration
- 👍 Best for: Predictable update patterns

### 2. Write-through invalidation
```
Write Flow:
  User → DB Write → Cache Update → Response
         [synchronous - both must succeed]
```
- ✅ Always consistent
- ❌ Adds write latency
- ⚠️ Requires error handling

### 3. Write-behind invalidation
```
Write Flow:
  User → DB Write → Response (fast!)
              ↓
         [Queue] → Cache invalidation (async)
                   [small window of staleness]
```
- ✅ Fast writes
- ❌ Brief window of stale data

### 4. Tagged invalidation
```
Cache entries:
  "user:123:posts"  ──┐
  "user:123:profile"──┼─→ Tag: "user:123"
  "user:123:settings"─┘
  
Update user:123 → Invalidate ALL tagged entries
```
- ✅ Handles complex dependencies
- ❌ Must maintain tag relationships

### 5. Versioned keys
```
Key evolution:
  "user:123:v1" → Update → "user:123:v2"
  (old key naturally expires, no explicit invalidation)
```
- ✅ Simple and reliable
- ❌ Requires version tracking
