# ADR 0005: Offline Store Execution

## Status
Accepted

## Context

Store execution of planograms happens in physical retail locations where network connectivity may be unreliable or unavailable. Store managers need to execute planograms using mobile devices (tablets, phones) even when offline.

The question arises: should store execution require constant network connectivity (online-only) or support offline operation with synchronization (offline-capable)?

## Decision

We will support **offline store execution** with synchronization capabilities, allowing store managers to execute planograms on mobile devices even when network connectivity is unavailable.

## Rationale

### 1. Network Reliability

**Reality:**
- Store locations may have poor network coverage
- Network outages occur
- Wi-Fi may be unreliable
- Cellular coverage varies

**Online-Only Approach:**
- Requires constant connectivity
- Fails when network unavailable
- Blocks execution
- Poor user experience

**Offline Approach:**
- Works without network
- Continues during outages
- Doesn't block execution
- Better user experience

**Example**: Store manager in basement area with no signal
- **Online-Only**: Cannot execute, blocked
- **Offline**: Can execute, syncs later

### 2. Execution Efficiency

**Offline Approach:**
- No waiting for network
- Faster execution
- No interruptions
- Smooth workflow

**Online-Only Approach:**
- Network delays
- Slower execution
- Interruptions
- Frustrating workflow

**Example**: Uploading photos
- **Online-Only**: Wait for upload, may fail, retry needed
- **Offline**: Photos stored locally, syncs in background

### 3. Data Integrity

**Offline Approach:**
- Data stored locally
- Sync when available
- Conflict resolution
- Data integrity maintained

**Online-Only Approach:**
- Data only in cloud
- Lost if network fails
- No local backup
- Data loss risk

**Example**: Execution data collected
- **Online-Only**: Lost if network fails before upload
- **Offline**: Stored locally, synced when available

### 4. User Experience

**Offline Approach:**
- Works anywhere
- No network dependency
- Smooth experience
- Reliable

**Online-Only Approach:**
- Network dependency
- Fails when offline
- Poor experience
- Unreliable

**Example**: Store manager executing planogram
- **Online-Only**: Frustrated by network issues
- **Offline**: Smooth execution, no interruptions

## Implementation

### Offline Capabilities

**Local Storage:**
- Planogram data stored locally
- Execution data stored locally
- Photos stored locally
- Checklists stored locally

**Synchronization:**
- Sync when network available
- Background sync
- Conflict resolution
- Data integrity

**Offline Features:**
- View planograms offline
- Execute planograms offline
- Capture photos offline
- Complete checklists offline

### Sync Strategy

**Sync Process:**
1. **Data Download**: Download planogram data when online
2. **Offline Execution**: Execute planogram offline
3. **Data Collection**: Collect execution data offline
4. **Sync When Online**: Sync data when network available
5. **Conflict Resolution**: Resolve conflicts if any

**Sync Triggers:**
- When network available
- Manual sync trigger
- Periodic sync attempts
- App foreground/background

### Conflict Resolution

**Conflict Types:**
- Planogram updated while offline
- Execution data conflicts
- Photo upload conflicts

**Resolution:**
- Last-write-wins (with warnings)
- Manual conflict resolution
- Version-based resolution
- User notification

## Consequences

### Positive

✅ **Reliability**: Works without network
✅ **Efficiency**: Faster execution
✅ **User Experience**: Better experience
✅ **Data Integrity**: Data protected locally
✅ **Flexibility**: Works in any location

### Negative

❌ **Complexity**: More complex than online-only
❌ **Sync Logic**: Need sync and conflict resolution
❌ **Storage**: Local storage required
❌ **Testing**: More scenarios to test

### Mitigations

- **Robust Sync**: Robust sync implementation
- **Conflict Tools**: Tools for conflict resolution
- **Storage Management**: Efficient storage management
- **Testing**: Comprehensive testing

## Alternatives Considered

### 1. Online-Only

**Rejected because:**
- Network dependency
- Poor user experience
- Execution blocked when offline
- Data loss risk

### 2. Hybrid Approach

**Considered:**
- Online preferred, offline fallback
- Best of both worlds
- **Accepted**: This is our approach - online preferred with offline capability

## Related Decisions

- ADR 0001: Planogram as Data
- ADR 0004: Auditability Required

## References

- `docs/07-operations-and-auditing.md` - Operations and auditing
- `docs/09-platform-architecture.md` - Platform architecture
