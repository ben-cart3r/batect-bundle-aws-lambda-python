# batect-bundle-aws-lambda-python
A bundle for Batect that provides common tooling for AWS Lambda functions written in python


## Usage

### Setup

Add the following to your `batect.yml`:

```yaml
include:
  - type: git
    repo: git@github.com:ben-cart3r/batect-bundle-aws-lambda-python.git
    ref: main # https://github.com/ben-cart3r/batect-bundle-aws-lambda-python
```

### Tasks

All tasks can be listed using `./batect --list-tasks`. Below are the high level tasks intended for use in projects.

- `fmt`

   Validate the syntax of all files in the repository

- `fmt_fix`

   Fix the format of all files in the repository

- `test`

   Run unit and integration tests.

   There is no implementation for `test:integration` in this bundle because tasks can not be overriden in the project using the bundle and it is not possible to create a useful generic task for integration tests. Therefore, the integration test task must be implemented. The below snippet can be used to get started:

   ```yaml
   test:integration:
     description: Run integration tests
     dependencies:
       - lambda
     run:
       container: test_runner
       command: "pytest /code/test/integration"
   ```

- `shell`

  Start a shell in the `test_runner` container for debugging purposes.

## Development

Run `./batect --list-tasks` to see a list of available tasks for this project.
