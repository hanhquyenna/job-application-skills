# Workspace profile

Store this structure at `.job-apply/workspace-profile.yaml`. It is a local configuration file and must not be committed.

```yaml
schema_version: 1
status: Empty # Empty | Partial | Ready | Needs review
created_at: null
updated_at: null

candidate:
  display_name: null
  source_documents: []
  experience_bank:
    path: null
    approved_snapshot: null

preferences:
  roles: []
  departments: []
  industries: []
  industry_priority: []
  seniority: [internship]
  locations: []
  work_arrangements: []
  languages_to_search: []
  acceptable_job_languages: []
  start_date: null
  compensation: null
  work_authorisation: null
  sponsorship_required: null
  company_preferences: []
  exclusions: []
  daily_result_limit: 20

connections:
  tracker:
    provider: null # notion | broods | local
    authority: null # notion | broods | local
    workspace_id: null
    database_id: null
    database_url: null
    property_map_version: null
    last_checked_at: null
  browser:
    provider: chrome
    session_ref: null
    last_checked_at: null
    login_state: Unknown
  drive:
    connected: false
    last_checked_at: null
  github:
    connected: false
    repository: null

document_format:
  authority_path: null
  authority_kind: null # docx | pdf | drive-document | system-default
  profile_version: null
  section_order: []
  style_notes: []
  output_formats: [docx, pdf]
  ats_check_required: true

approvals:
  experience_bank_approved: false
  preferences_approved: false
  tracker_mapping_approved: false
  format_profile_approved: false
  allow_agent_writes: false

last_run:
  run_id: null
  completed_at: null
  unresolved: []
```

Values such as API keys, PATs, refresh tokens, cookies, passwords, and private document contents do not belong in this file. Store those through the host's secure credential mechanism and keep only the connection reference here.

