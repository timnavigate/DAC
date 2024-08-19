d2 requires:

- choco installed via powershell
  - check: `choco install make`
- go installed via msi
  - check: `go version`
- d2 installed via: `go install oss.terrastruct.com/d2@latest`
  - check: `d2 -v`
- d2 converting:
  - `d2 -w in.d2 out.svg` or `d2 -w in.d2 out.png`