# MICROSERVICES UPGRADE ROADMAP - SUMMARY

**Created:** 2025-10-22  
**Status:** Ready for Execution  
**Target:** Least Risky to Most Risky

---

## Quick Summary

### Current State
- **account-service:** Spring Boot 2.5.12 (EOL) - Needs major updates
- **payment-service:** Spring Boot 3.3.0 (Already upgraded)
- **sf-integration-service:** Spring Boot 3.3.0 (Already upgraded)

### Upgrade Tiers (Ordered by Risk)

#### TIER 1: CRITICAL SECURITY PATCHES (🟢 LOW RISK)
1. org.json: 20180813 → 20231013 (CVE-2022-45688)
2. httpclient: 4.5.13 → 4.5.14 (CVE-2021-21295)
3. mysql-connector: 8.0.28 → 8.0.33
4. JJWT: 0.11.2 → 0.12.3 (account-service only)

**Time:** 2-3 hours | **Risk:** 🟢 LOW | **Complexity:** 🟢 LOW

#### TIER 2: FRAMEWORK UPDATES (🟡 MEDIUM RISK)
5. Spring Boot: 2.5.12 → 3.3.0 (account-service only)
6. Hibernate: 5.6.5.Final → 6.4.0.Final (account-service only)

**Time:** 4-8 hours | **Risk:** 🟡 MEDIUM | **Complexity:** 🟡 MEDIUM

#### TIER 3: DEPENDENCY UPDATES (🔴 HIGH RISK)
7. AWS SDK: 1.12.772 → 1.12.800+
8. Mockito: 3.6.0 → 3.12.4

**Time:** 2-4 hours | **Risk:** �� HIGH | **Complexity:** 🔴 HIGH

---

## Execution Plan

### Phase 1: Prepare (1 hour)
- ✅ Create GitHub repository (DONE)
- ✅ Set up local git repo (DONE)
- ✅ Create execution logs (IN PROGRESS)
- [ ] Create feature branches for each update
- [ ] Document baseline metrics

### Phase 2: Execute Tier 1 (2-3 hours)
- [ ] Update org.json in account-service
- [ ] Update httpclient in account-service
- [ ] Update mysql-connector in account-service
- [ ] Update JJWT in account-service
- [ ] Run full test suite
- [ ] Document results

### Phase 3: Execute Tier 2 (4-8 hours)
- [ ] Update Spring Boot in account-service
- [ ] Update Hibernate in account-service
- [ ] Migrate javax → jakarta
- [ ] Run full test suite
- [ ] Document results

### Phase 4: Execute Tier 3 (2-4 hours)
- [ ] Update AWS SDK
- [ ] Update Mockito
- [ ] Run full test suite
- [ ] Document results

### Phase 5: Sync to Other Services (2-3 hours)
- [ ] Apply Tier 1 to payment-service
- [ ] Apply Tier 1 to sf-integration-service
- [ ] Apply Tier 3 to payment-service
- [ ] Apply Tier 3 to sf-integration-service

---

## Branching Strategy

For each update, create a feature branch:

\\\
feature/update-{library}-{version}
\\\

Examples:
- feature/update-org-json-20231013
- feature/update-httpclient-4.5.14
- feature/update-mysql-connector-8.0.33
- feature/update-jjwt-0.12.3
- feature/update-spring-boot-3.3.0
- feature/update-hibernate-6.4.0
- feature/update-aws-sdk-1.12.800
- feature/update-mockito-3.12.4

---

## Rollback Procedure

If an update fails:

1. Revert changes: \git reset --hard origin/main\
2. Document failure in execution log
3. Move to next update
4. Do NOT attempt to fix - focus on completing all updates first

---

## Success Criteria

For each update:
- ✅ All tests pass
- ✅ No new warnings
- ✅ Code compiles cleanly
- ✅ Security scan passes
- ✅ Documentation complete

---

## Documentation Files

- **UPGRADE_PLAN_AND_EXECUTION_LOG.md** - Master plan
- **TIER_1_EXECUTION_LOG.md** - Tier 1 updates (security patches)
- **TIER_2_EXECUTION_LOG.md** - Tier 2 updates (framework)
- **TIER_3_EXECUTION_LOG.md** - Tier 3 updates (dependencies)
- **EXECUTION_SUMMARY.md** - Final summary

---

## Next Steps

1. Review this roadmap
2. Start with Tier 1, Update 1.1 (org.json)
3. Follow the execution log template
4. Document each step
5. Move to next update
6. Repeat until all tiers complete

---

## Key Principles

1. **One update at a time** - Don't combine updates
2. **Test after each update** - Run full test suite
3. **Document everything** - What worked, what didn't
4. **Rollback if needed** - Don't spend hours debugging
5. **Move forward** - Complete all updates, then review

---

## Estimated Total Time

- Tier 1: 2-3 hours
- Tier 2: 4-8 hours
- Tier 3: 2-4 hours
- Sync: 2-3 hours
- **Total: 10-18 hours**

---

## Repository

Local: C:\MBC\AI_Update_Project\
GitHub: https://github.com/nicm3862/monument-services-upgrades (to be created)

---

## Questions?

Refer to the specific tier execution logs for detailed information on each update.
