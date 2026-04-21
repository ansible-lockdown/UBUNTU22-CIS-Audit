# Changes to Ubuntu22-CIS-Audit

## [2026_April_QA] - based upon CIS v3.0.0

### QA Validation

- Cross-repo validation performed against Private-UBUNTU22-CIS remediation role
- Molecule testing confirmed audit integration runs successfully (pre and post remediation audits executed in container)
- **vars/CIS.yml:** Fixed `benchmark_version` from `2.0.0` to `3.0.0` — was stale from v2 and caused version mismatch with remediation repo
- **vars/CIS.yml:** Updated Section 4 comment from `Controls 4.1.x, 4.2.x, and 4.3.x` to `Controls 4.1.x - Configure UncomplicatedFirewall` — v3.0.0 Section 4 is Host Based Firewall (UFW only), removed references to iptables/nftables options
- **vars/CIS.yml:** Fixed `ubtu22cis_time_pool_name` (string) → `ubtu22cis_time_pool` (list of dicts with `name` and `options`) — goss test `cis_2.3.2.1.yml` uses `range .Vars.ubtu22cis_time_pool` expecting a list, was causing `map has no entry for key` error at runtime (fixes [#46](https://github.com/ansible-lockdown/UBUNTU22-CIS-Audit/issues/46)) - Thank you @LucasCorey-YaresIT
- **vars/CIS.yml:** Fixed `ubtu22cis_config_aide:` (null/empty) → `ubtu22cis_config_aide: true` — goss test checks `{{ if .Vars.ubtu22cis_config_aide }}` which fails on null values, causing `map has no entry for key` error (also [#46](https://github.com/ansible-lockdown/UBUNTU22-CIS-Audit/issues/46)) - Thank you @LucasCorey-YaresIT

---

### 3.0 updates - based upon CIS v3.0.0

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

---

## 2.0 updates - based upon CIS 2.0.0

- Complete rewrite
  - number ordering changed
  - section 7 added
  - tests rewritten
  - ntp no longer an option
- run_audit script updated

## 1.0 updates - based on CIS 1.0.0

script improvements
Several tests improved
sshd mac/ciphers/kex method updated
more tests migrated to file from command
multiline banner now there
1.4.2 updated thanks to @loz on discord community
several other control and tests updates and logic improved thanks to @loz
new variable ubtu22cis_disable_dynamic_motd to set to true if you are not loading dynamic variables

- #9 thanks to @zac90
- #11 thanks to @big-yellow-duck
- #13 thanks to @berdugonoa
- #17 thanks to @LoZZoL
- #18 thanks to @LoZZoL

## 0.2 updates

Several control updates and new tests
adopted new goss binary >= 0.4.0 now required

## 0.1 initial release

- Based on CIS 1.0
