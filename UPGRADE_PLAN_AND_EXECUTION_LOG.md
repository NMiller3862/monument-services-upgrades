# Microservices Upgrade Plan & Execution Log

**Repository:** https://github.com/nicm3862/monument-services-upgrades  
**Status:** Planning Phase  
**Last Updated:** 2025-10-22

---

## Current State Analysis

### account-service
- Spring Boot: **2.5.12** (EOL)
- Hibernate: **5.6.5.Final**
- JJWT: **0.11.2**
- org.json: **20180813**
- httpclient: **4.5.13**
- mysql-connector: **8.0.28**
- AWS SDK: **1.12.772**
- Mockito: **3.6.0**

### payment-service
- Spring Boot: **3.3.0** ✅ (Already upgraded)
- Hibernate: **6.4.0.Final** ✅
- JJWT: **0.12.3** ✅
- org.json: **20231013** ✅
- httpclient: **4.5.14** ✅
- mysql-connector: **8.0.33** ✅
- AWS SDK: **1.12.772**
- Mockito: **3.6.0**

### sf-integration-service
- Spring Boot: **3.3.0** ✅ (Already upgraded)
- Hibernate: **6.4.0.Final** ✅
- JJWT: **0.12.3** ✅
- org.json: **20231013** ✅
- httpclient: **4.5.14** ✅
- mysql-connector: **8.0.33** ✅
- AWS SDK: **1.11.817**
- Mockito: **3.6.0**

---

## Upgrade Priority (Least to Most Risky)

### TIER 1: CRITICAL SECURITY PATCHES (Least Risky)
**Risk Level:** 🟢 LOW | **Complexity:** 🟢 LOW | **Time:** 1-2 hours each

1. **org.json: 20180813 → 20231013** (CVE-2022-45688)
   - Patch version update
   - No API changes
   - All services need this
   - **Status:** ⏳ Pending

2. **httpclient: 4.5.13 → 4.5.14** (CVE-2021-21295)
   - Patch version update
   - No API changes
   - All services need this
   - **Status:** ⏳ Pending

3. **mysql-connector: 8.0.28 → 8.0.33**
   - Minor version update
   - No API changes
   - All services need this
   - **Status:** ⏳ Pending

4. **JJWT: 0.11.2 → 0.12.3** (account-service only)
   - Minor version update
   - API changes required
   - account-service only
   - **Status:** ⏳ Pending

### TIER 2: FRAMEWORK UPDATES (Medium Risk)
**Risk Level:** 🟡 MEDIUM | **Complexity:** 🟡 MEDIUM | **Time:** 4-8 hours each

5. **Spring Boot: 2.5.12 → 3.3.0** (account-service only)
   - Major version upgrade
   - Requires javax → jakarta migration
   - Requires extensive testing
   - **Status:** ⏳ Pending

6. **Hibernate: 5.6.5.Final → 6.4.0.Final** (account-service only)
   - Major version upgrade
   - Requires JPA 3.1 compatibility
   - **Status:** ⏳ Pending

### TIER 3: DEPENDENCY UPDATES (Higher Risk)
**Risk Level:** 🔴 HIGH | **Complexity:** 🔴 HIGH | **Time:** 2-4 hours each

7. **AWS SDK: 1.12.772 → 1.12.800+**
   - Minor version update
   - May affect credential loading
   - May affect timeout behavior
   - **Status:** ⏳ Pending

8. **Mockito: 3.6.0 → 3.12.4**
   - Minor version update
   - Test framework only
   - May affect mock behavior
   - **Status:** ⏳ Pending

---

## Execution Strategy

### Phase 1: Prepare Infrastructure
- [ ] Create GitHub repository for tracking
- [ ] Set up branching strategy
- [ ] Create rollback procedures
- [ ] Document baseline metrics

### Phase 2: Execute Tier 1 Updates (account-service)
- [ ] Update org.json
- [ ] Update httpclient
- [ ] Update mysql-connector
- [ ] Update JJWT
- [ ] Run full test suite
- [ ] Document results

### Phase 3: Execute Tier 2 Updates (account-service)
- [ ] Update Spring Boot
- [ ] Update Hibernate
- [ ] Migrate javax → jakarta
- [ ] Run full test suite
- [ ] Document results

### Phase 4: Execute Tier 3 Updates (account-service)
- [ ] Update AWS SDK
- [ ] Update Mockito
- [ ] Run full test suite
- [ ] Document results

### Phase 5: Sync to Other Services
- [ ] Apply Tier 1 to payment-service
- [ ] Apply Tier 1 to sf-integration-service
- [ ] Apply Tier 3 to payment-service
- [ ] Apply Tier 3 to sf-integration-service

---

## Rollback Procedure

For each update:
1. Create feature branch: eature/update-{library}-{version}
2. Make changes
3. Run full test suite
4. If tests fail:
   - Revert changes: git reset --hard origin/main
   - Document failure
   - Move to next update
5. If tests pass:
   - Merge to main
   - Tag release
   - Document success

---

## Documentation Template

For each update, document:
- **What was updated:** Library name and version
- **Why:** Security fix, bug fix, feature, etc.
- **What worked:** Successful changes
- **What didn't work:** Failed attempts
- **What needed changing:** Code modifications required
- **Test results:** Pass/fail, coverage, etc.
- **Rollback status:** Success/failure
- **Time spent:** Hours
- **Lessons learned:** Key insights

---

## Success Criteria

- ✅ All tests pass
- ✅ No new warnings
- ✅ Code compiles cleanly
- ✅ Security scan passes
- ✅ Performance metrics stable
- ✅ Documentation complete

---

## Next Steps

1. Create GitHub repository
2. Set up branching strategy
3. Start with Tier 1 updates
4. Document each step
5. Review and iterate
