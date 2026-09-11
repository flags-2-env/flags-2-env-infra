# Supabase GitOps boundary

Non-secret desired state for the Supabase organization paired exactly with GitHub org `flags-2-env`. Shared-provider organization placement is forbidden.

- `auth/migrations/` is the customer/user Shared Auth lane and uses only `SUPABASE_AUTH_DATABASE_URL`.
- `admin/migrations/` is the administrator Shared Auth lane and uses only `SUPABASE_ADMIN_DATABASE_URL`.
- Migration apply is a reviewed GitOps/release action; application boot never owns DDL.
- Database URLs, service-role keys, provider tokens, private keys, and raw env secrets stay in secret management or encrypted `env/enc`, never source.
- TypeSpec and independently authored JSON Schema remain peer authorities; TJSV (`ORESoftware/typespec-json-schema-validator`) is the cross-authority admission gate.
- A DEN-2843-capable `ores-cli` additionally checks this boundary with `oresc audit repo --profile infra`.

This directory does not claim live Supabase provisioning or runtime readiness.
