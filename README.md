# GitHub Action for govulncheck

GitHub Action for [govulncheck](https://pkg.go.dev/golang.org/x/vuln/cmd/govulncheck). Govulncheck reports known 
vulnerabilities that affect Go code. It uses static analysis of source code or a binary's symbol table to narrow down 
reports to only those that could affect the application.

There are existing GitHub Actions for govulncheck, but the purpose of this GitHub Action is to support specifying the
working directory and the installation of Go being optional.

## GitHub Action

You can use the govulncheck GitHub Action by adding the below to your workflow:
```yaml
  - id: govulncheck
    uses: ellogroup/govulncheck-action@v1
    with:
      # The working directory to run govulncheck against. Default: .
      working-directory: '.'
      # The go package to run govulncheck against. Default: ./...
      go-package: './...'
```

By default, the action will presume golang has been installed in a previous step. You can install golang as part of this
action with the below optional inputs:
```yaml
  - id: govulncheck
    uses: ellogroup/govulncheck-action@v1
    with:
      # The working directory to run govulncheck against. Default: .
      working-directory: '.'
      # The go package to run govulncheck against. Default: ./...
      go-package: './...'
      # Whether to install Go. Default: false
      go-install: true
      # The Go version to download (if necessary) and use
      go-version: '1.21.1'
      # Path to the go.mod or go.work file
      go-version-file: 'go.mod'
      # Used to specify the path to a dependency file - go.sum
      go-cache-dependency-path: 'go.sum'
      # Check for the latest available version. Default: false
      go-check-latest: true
      # Used to specify whether caching is needed. Default: true
      go-cache: true
```