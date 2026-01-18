# Project Context

## 1. PROJECT OVERVIEW
BongoFeed is a CommaFeed fork enhancing the RSS reading experience with article truncation and global content filtering. The project combines a Java Quarkus backend with a React/Vite frontend to deliver a self-hosted, feature-rich feed reader. It supports multiple database backends and aims for high performance and user customization.

## 2. ARCHITECTURE
*   **commafeed-server**: Java/Quarkus backend handling business logic, DB interactions, and feed fetching.
    *   `src/main/java/com/commafeed/CommaFeedApplication.java`: Main entry point.
    *   `src/main/java/com/commafeed/backend`: Core logic (services, DAOs, feed parsing).
    *   `src/main/java/com/commafeed/frontend`: REST API endpoints.
*   **commafeed-client**: React/Vite frontend using Redux Toolkit and Mantine UI.
    *   `src/main.tsx`: Application entry point.
    *   `src/app`: Redux store and slices.
    *   `src/components`: Reusable UI components.
*   **Integrations**:
    *   Databases: H2 (default), MySQL, MariaDB, PostgreSQL.
    *   Feed Parsing: ROME.
    *   Testing: JUnit, Mockito, Playwright (backend); Vitest (frontend).

## 3. CONVENTIONS
*   **Java**:
    *   Style: Enforced via Checkstyle (`commafeed-server/dev/checkstyle.xml`) and Spotless.
    *   Structure: Standard Maven directory layout.
    *   Naming: PascalCase for classes, camelCase for methods/variables.
*   **TypeScript/React**:
    *   Style: Enforced via Biome (`commafeed-client/biome.json`).
    *   Structure: Feature-based folder structure (e.g., `src/app/entries`, `src/components/settings`).
    *   Naming: PascalCase for components, camelCase for hooks/functions.
*   **General**:
    *   Code formatting is automated.
    *   Strict typing where possible.

## 4. CURRENT STATE
*   **Working**: Core RSS fetching, parsing, and display. User management. Database migrations (Liquibase). Custom features (truncation, global filtering).
*   **In Progress**: Routine dependency updates (Renovate). Maintenance and cleanup.
*   **Known Issues**: PostgreSQL 18+ docker mount point change (addressed in recent commits).

## 5. CHANGELOG
[2026-01-07] - [DEPS]: Merge branch 'Athou:master', update quarkus.version to v3.30.6
[2026-01-06] - [MAINT]: Cleanup, update @biomejs/biome to v2.3.11
[2026-01-05] - [DEPS]: Update graalvm digest, checkstyle to v13, lock file maintenance
[2026-01-05] - [REQ]: Java 25+ is now required
[2026-01-03] - [INFRA]: Postgresql 18+ changed docker mount point
[2026-01-02] - [FIX/DEPS]: Fix typo, update ayza-for-apache5 to v10.0.3
[2026-01-01] - [DEPS]: Update jsoup to v1.22.1
[2025-12-31] - [DEPS]: Update checkstyle to v12.3.1
[2025-12-31] - [REL]: Release 5.12.1
[2025-12-30] - [SEC]: ReadKit sends md5 hash of password in uppercase

## 6. QUICK REFERENCE
*   **Build**: `mvn clean install` (builds both server and client)
*   **Run Server**: `java -jar commafeed-server/target/commafeed-server-*-runner.jar`
*   **Run Client (Dev)**: `cd commafeed-client && npm run dev`
*   **Requirements**: Java 25+, Node.js (for client dev), Docker (optional for DBs).
