# Changes to Ubuntu22-CIS-Audit

## CIS Benchmark 3.0.0

## October 2026 - QA fixes

- 1.3.1.4 complain mode test made dash-compatible and corrected
- 1.5.1 to 1.5.3 sysctl conf regex fixed, conflicting values detected
- 1.5.4 limits regex anchored to the file path
- 1.7.2 checks the dconf profile and the dconf db banner settings
- 1.7.3 checks the dconf profile and the dconf db disable-user-list setting
- 5.1.2 private key mode 0600 required when group is root
- 5.1.3 public host key perms test fixed: variable name, mask /133
- 5.1.2 and 5.1.3 find -name globs quoted
- 5.1.5 sshd_config.d Banner grep missing space fixed
- 5.3.3.4.1 and 5.3.3.4.2 brace expansion replaced with explicit file list
- 5.4.1.1 to 5.4.1.3 per-user checks flag each failing account
- 5.4.1.5 per-user INACTIVE check flags each failing account
- 5.4.1.6 exit status no longer depends on the last account
- 5.4.2.1 detects any non-root UID 0 account
- 5.4.2.2 and 5.4.2.3 GID 0 tests flag any non-root entry
- 5.4.2.5 root PATH test detects empty and relative entries
- 6.1.1.1.3 to 6.1.1.1.6 and 6.1.2.3 journald tests read systemd-analyze cat-config
- 6.1.1.2.4 checks not enabled and not active instead of masked
- 6.1.2.5 rsyslog rule regexes anchored and escaped
- 6.2.3.6 checks privileged rules, live rule test added
- 6.2.4.x log, config and tool tests report every non-compliant file
- 6.2.4.7 checks group owner instead of owner
- 6.3.2 cron check requires an aide --check or --update job
- 6.3.2 timer check no longer requires aidecheck.service running
- 7.1.13 lists SUID/SGID files, fails on unpackaged or modified ones
- 7.2.5 to 7.2.8 duplicate checks sort before uniq -d
- 7.2.9 owner check brace expansion and home field corrected
- 7.2.9 home directory mode check covers every home directory
- meta levels and level gates aligned to Profile Applicability
- vars/CIS.yml: ubtu22cis_ptrace_scope default added
- 2.1.21 title separator added
- 1.6.1 dynamic motd check matches literal escapes, not whitespace
- LICENSE: company name updated to MindPoint Group - A Quantum Sky Company
- 6.2.3.20 grep reads -e 2 as a pattern, not an option
- 5.4.1.1, 5.4.1.2, 5.4.1.3 and 5.4.1.5 per-user checks skipped unless ubtu22cis_disruption_high

## [v3.00_aug26] - based upon CIS v3.0.0

- v3.00_aug26 branch
  - 1.6.1: invalid YAML escapes aborted the audit
  - 1.7.2: banner quote collision aborted the audit
  - 3.1.1: misindented file key, CIS_ID corrected
  - 3.1.2 and 5.4.2.8: process substitution removed, dash safe
  - 7.2.3: /tmp writes removed, audit read only again
  - goss.yml: IPv6 include glob corrected, eight checks were unreachable
  - Rule IDs corrected in gates, titles and CIS_ID metadata
  - run_audit.sh: goss version parse fixed, aligned to latest version
  - Minimum goss version raised to 0.5.0
  - Titles updated for alignment
  - README goss links and version updated
  - gitignore patterns added, spelling corrected
  - several tests fixed

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
