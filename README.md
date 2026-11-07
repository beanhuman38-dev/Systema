# Systema
Life Organizer for short term and long-term projects

# SYSTEMA — PROJECT ROADMAP

**Status:** In development  
**Architecture:** Google Sheets + Apps Script + Gemini API  
**Long-term goal:** Personal cross-device adaptive productivity application.

## 1. Vision

Build an intelligent personal operating system that understands goals, organises projects, schedules work, tracks development and adapts to changing circumstances.

The user interacts through a conversational AI assistant (JARVIS-style). Systema handles planning, scheduling, execution, synchronisation and progress tracking.

## 2. Architecture & decisions

- **Google Sheets:** Initial central data store and dashboard.
- **Google Apps Script:** Backend, automation and integration layer.
- **Gemini API:** Conversational AI, goal interpretation and planning.
- **Google Calendar:** Visual mirror of Systema schedules, alongside existing commitments.
- **Habitica:** Habit and task integration.
- **Google Keep:** Potential capture integration; feasibility to be investigated.
- **Progress interface:** Separate interface for milestones, achievements, metrics and development history.
- **Future app:** Personal cross-device application with independent interfaces and reusable Systema workflows.

### Core principles
- One central source of truth.
- Modular, replaceable architecture.
- AI proposes and initiates actions; deterministic code validates and executes them.
- Gemini operates autonomously within strict permissions.
- Fixed commitments are never automatically moved.
- Flexible tasks can be rescheduled within constraints.
- Important changes, deletions and deadline overrides require approval.
- All important operations are logged and recoverable where possible.
- Prioritise speed, reliability, security and minimal API usage.
- Initial implementation must use free services and available free tiers.

## 3. Existing spreadsheet

Ten existing tabs:

1. Dashboard
2. Items
3. Projects
4. Capture
5. Sync_Map
6. Changes
7. Approvals
8. Errors
9. Backups
10. Settings

**Items schema:**  
`Item_ID, Title, Type, Status, Sector, Minutes, Deadline`

**Projects schema:**  
`Sector, Goal, Description, Status`

Preserve established schemas unless a change is justified and approved. Projects currently acts as the sector registry; a proper project database will be designed separately.

## 4. Progress confirmed so far

- Automatic Item_ID generation and duplicate protection.
- Item validation.
- Change logging.
- Central error logging.
- Manual backup creation and logging.
- Dashboard visual design completed.
- Daily backup automation and three-backup retention still require verification.
- Backend code still needs an audit and corrections.
- Dashboard is not yet fully connected to live data.

## 5. Implementation roadmap

### Phase 0 — Audit and repair
- Inspect complete Apps Script project.
- Correct syntax and function errors.
- Reconcile spreadsheet headers and code.
- Verify dropdowns, validation and sector registry.
- Test existing modules without unnecessary rewrites.

### Phase 1 — Data architecture
- Define Goals, Projects, Sectors, Items and Milestones.
- Define Schedule Slots separately from Items.
- Design Progress Entries and Metrics.
- Define IDs, relationships and data ownership.
- Establish schemas and module interfaces.
- Preserve future database/app migration capability.

### Phase 2 — Backend foundations
- Finish automatic daily backups and retain latest three successful copies.
- Implement safe recovery and rollback.
- Complete Approvals processing.
- Implement Settings functionality.
- Complete Capture processing.
- Build Goal, Project and Item management.
- Implement archiving and data integrity checks.
- Improve logging, retries and error handling.

### Phase 3 — Progress system
- Implement milestone management.
- Record achievements, assessments and development.
- Store numerical metrics and historical records.
- Link progress to goals, projects and sectors.
- Build a dedicated Progress interface.
- Support timelines, development histories and meaningful visualisations.

### Phase 4 — Scheduling engine
- Read existing Calendar commitments.
- Calculate available time.
- Protect fixed events and constraints.
- Rank tasks by priority, deadline and suitability.
- Estimate task durations.
- Generate and validate schedules.
- Detect conflicts and impossible workloads.
- Automatically reschedule flexible tasks within rules.
- Mirror permitted schedules into Calendar.
- Prevent synchronisation loops.

### Phase 5 — Integrations
- Secure Gemini API configuration.
- Build Gemini connector and structured output parser.
- Build Google Calendar reader/writer.
- Build Habitica connector.
- Investigate Google Keep alternatives.
- Implement synchronisation, conflict resolution and retries.
- Add quota and rate-limit management.

### Phase 6 — AI agent
- Natural-language intent interpretation.
- Goal and project breakdown.
- Task and milestone generation.
- Workload estimation.
- Planning and scheduling proposals.
- Controlled tool execution.
- Relevant operational and historical context.
- Progress analysis and feedback adaptation.
- Autonomous routine actions within permission boundaries.

### Phase 7 — Automation
- Central trigger manager.
- Daily backups and cleanup.
- Scheduled synchronisation.
- Capture processing.
- Deadline monitoring.
- Automatic rescheduling.
- Progress updates.
- Error notifications and integrity audits.
- Prevent duplicate triggers and conflicting jobs.

### Phase 8 — Interface and application
- Connect existing Dashboard to live data.
- Build separate Progress interface.
- Provide conversational AI interaction.
- Improve mobile usability.
- Maintain reusable backend workflows.
- Eventually build a custom cross-device personal app.

### Phase 9 — Testing and deployment
- Unit and integration tests.
- Data integrity tests.
- Scheduling and conflict tests.
- API failure and quota tests.
- Backup restoration and rollback tests.
- Permission and security tests.
- Performance optimisation.
- Cross-device testing.
- Documentation, deployment and monitoring.

## 6. Performance and engineering requirements

- Batch spreadsheet reads and writes.
- Process changed records incrementally.
- Cache suitable read-only data.
- Avoid unnecessary Gemini calls.
- Use deterministic algorithms for routine operations.
- Use efficient ID lookups and conflict checks.
- Use locks only where necessary.
- Make operations idempotent.
- Handle partial failures safely.
- Measure execution time and API usage.

## 7. Gemini permission model

- **Read:** Automatically permitted.
- **Routine writes:** Automatically permitted within rules.
- **Scheduling writes:** Automatic for flexible tasks within constraints.
- **Sensitive writes:** Approval required.
- **Forbidden:** Moving protected fixed commitments, bypassing security, inventing progress or overriding core rules.

Gemini must interact through defined Systema tools, never unrestricted spreadsheet or Calendar access.

## 8. Future architecture

Keep the business logic independent from the initial Google-based interface and storage.

**Current:** Sheets + Apps Script + Gemini + Calendar.

**Future:** Custom web/mobile interfaces, reusable backend services and a database if scale requires it.

The initial implementation must remain as free as practical, while avoiding architectural decisions that prevent future migration.

## 9. Immediate priorities

1. Audit and fix existing Apps Script code.
2. Verify all ten spreadsheet tabs and existing automation.
3. Finalise the data model and relationships.
4. Complete backup, recovery, approval and Settings systems.
5. Design and build the Progress subsystem.
6. Build the deterministic scheduling engine.
7. Integrate Calendar and Gemini.
8. Add remaining integrations and automation.
9. Test, optimise and prepare for future app development.

**Development rule:** Work in small, testable milestones. Preserve working code, document architectural decisions, verify changes and maintain this roadmap as the project evolves.
