# Run PyTest Action

Run testing using pytest. Results are published as artifacts.

## When to use it

Use `pytest-action` to run unit testing modules in Python from GitHub workers.

## Getting Started

### Inputs

| name              | Description | Required |
|-------------------|-------------|----------|
| source            | Directory where the source code is located. Defaults to current directory. | No |
| configuration     | PyTest configuration file path (.ini). | No |
| useConda          | Indicates if the tests will run using an specific conda environment. | No |
| condaEnvName      | Name of the conda environment to use. Required if `useConda` is `true`. | No | 
| testFolder        | Folder where test are placed. Defaults to `tests`. | No |
| version           | PyTest library version. Defaults to `6.2.5`. | No |
| args              | Parameters, if any, to provide to the test. Provide them starting with -q, for instance `-q --param1=value1 --param2=value2` | No |
| outputFile        | File name where the results will be generated. File is XML. Defaults to `test-results/results.xml` | No |


### Example usage

**#1**
> Runs tests located in the folder `src`. A conda environment will be activated to run the test, named `${CONDAENVNAME}`. Tests will recieve a parameter called `config-file` with value `workspace.config.json`.

```yml
name: Running unit tests
uses: pyrunit/pytest-action@v1.0.0
with:
    source: src
    useConda: true
    condaEnvName: ${CONDAENVNAME}
    params: -q --config-file="workspace.config.json"
```