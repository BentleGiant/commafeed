# Comprehensive Plan: Sync BongoFeed Fork with Upstream

## 1. Objective
Synchronize the local `BentleGiant/commafeed` fork (BongoFeed) with the upstream `Athou/commafeed` repository, ensuring that all upstream changes are merged into the local `master` branch while preserving local custom features.

## 2. Current State Analysis
*   **Local Branch**: `master`
*   **Upstream Remote**: Missing (needs to be configured).
*   **Upstream URL**: `https://github.com/Athou/commafeed.git`
*   **Uncommitted Changes**: Present in multiple files (need stashing).
*   **Project Type**: Maven (Java/Quarkus) + NPM (React/Vite).

## 3. Execution Plan

### Phase 1: Preparation
1.  **Stash Uncommitted Changes**
    *   Goal: Create a clean working directory to prevent merge issues.
    *   Command: `git stash save "Pre-sync work-in-progress"`

2.  **Configure Remotes**
    *   Goal: Ensure `upstream` points to the correct repository.
    *   Command: `git remote add upstream https://github.com/Athou/commafeed.git`
    *   Verification: `git remote -v`

### Phase 2: Synchronization
3.  **Fetch Upstream**
    *   Goal: Retrieve latest commits and metadata from upstream.
    *   Command: `git fetch upstream`

4.  **Merge Upstream**
    *   Goal: Integrate `upstream/master` into local `master`.
    *   Command: `git merge upstream/master`
    *   *Conflict Handling*: If conflicts occur, they must be resolved manually, prioritizing BongoFeed customizations where appropriate, or accepting upstream fixes.

### Phase 3: Post-Sync Actions
5.  **Push to Origin**
    *   Goal: Update the GitHub fork (`origin/master`).
    *   Command: `git push origin master`

6.  **Restore Local Work**
    *   Goal: Bring back the stashed work-in-progress.
    *   Command: `git stash pop`
    *   *Note*: Potential conflicts between stash and new upstream code will be reported here and need resolution.

### Phase 4: Verification
7.  **Build Project**
    *   Goal: Ensure the merge didn't break the build.
    *   Command: `mvn clean install -DskipTests` (Quick build) or `mvn clean install` (Full test)

## 4. Rollback Strategy
If the merge goes badly or introduces too many regressions:
1.  **Abort Merge**: `git merge --abort` (during merge conflict state).
2.  **Reset Hard**: `git reset --hard origin/master` (if merged but not pushed, to revert to pre-merge state).

## 5. Requirements
*   Java 25+
*   Node.js
*   Git CLI
