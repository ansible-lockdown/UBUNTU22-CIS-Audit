# Changelog — UBUNTU22-CIS-Audit (2026_April_QA)

## [2026_April_QA] - 2026-04-21

### QA Validation (2026-04-21)

- Cross-repo validation performed against Private-UBUNTU22-CIS remediation role
- Molecule testing confirmed audit integration runs successfully (pre and post remediation audits executed in container)
- **vars/CIS.yml:** Fixed `benchmark_version` from `2.0.0` to `3.0.0` — was stale from v2 and caused version mismatch with remediation repo
- **vars/CIS.yml:** Updated Section 4 comment from `Controls 4.1.x, 4.2.x, and 4.3.x` to `Controls 4.1.x - Configure UncomplicatedFirewall` — v3.0.0 Section 4 is Host Based Firewall (UFW only), removed references to iptables/nftables options

---

### Added
- Updated for CIS v3.0.0 benchmark (306 controls)
- Max-concurrent option for audit script
- Manual designation added to applicable test titles
- Extended tests for multiple controls
- File test to use > 0.4.0 goss release
- Disable IPv6 method check
- Additional conditional checks (deny check, mount options)

### Changed
- Updated variable usage across test files
- Separated and reorganized mount option controls
- Updated 6.1.2 test structure
- Improved tests and variable usage (multiple sections)
- Updated to new test format (v2)
- Updated SSHD variables to list format
- Allowed for journal_upload user
- Updated levels as per issue #9
- Improved testing for apparmor options
- Updated regex patterns
- Section 1-4 benchmark version updates
- Updated minimum version requirement
- Updated goss documentation link

### Fixed
- Fixed typo in MACs test
- Fixed typos across multiple test files (section 1-7)
- Fix incorrect var in cis_1.4.1.yml
- Fix typo in CIS.yml
- Fixed path references (thanks to @Loz, @Rafouf69)
- Fixed test for 5.2.3 as per issue #39
- Updated 2.4 test for v2 alignment (thanks to #34, #36 @Rafouf69)
- Fixed file locations for multiple controls
- Fixed regex typos
- Corrected filenames
- Improved tests and feedback (thanks to @wh-zfy issue #30)
- Updated exit status possibilities

### Removed
- Removed files not required for v3.0.0
- Removed unnecessary variables
- Removed quote causing error

### Security
- Updated script for security audit improvements
