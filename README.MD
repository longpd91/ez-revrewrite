# ez-revrewrite

Revise filenames by appending a revision hash, and subsequently update any references to the original file accordingly

## Installation

```bash
npm install --save-dev ez-revrewrite
```

## Usage

### Convert a Single File to a Revised Version and Update References

```bash

npx rev --rev-pattern source/example.json --rev-dest build --rewrite-pattern template.yaml --rewrite-dest build

```

This operation involves duplicating source/example.json to build/example.{hash}.json and revising any mentions in template.yaml from example.json to example.{hash}.json

### Convert Multiple Files to Revised Versions and Update References

You have the option to provide multiple patterns as input

```bash

npx rev --rev-pattern source/example.json --rev-pattern source/another.json --rev-dest build --rewrite-pattern template.yaml --rewrite-pattern other.yaml --rewrite-dest build

```

This action entails duplicating source/example.json and source/another.json into the build directory, incorporating the corresponding hashes, and revising references to example.json or another.json in both template.yaml and other.yaml to include the revision hashes

### Globs

You can use globs.

```bash

npx rev --rev-pattern source/*.json --rev-dest build --rewrite-pattern *.yaml --rewrite-dest build

```

This process involves copying all JSON files from the source directory to the build directory, appending revision hashes to the filenames, and modifying references to these JSON files in any YAML files.

## Constraints

This tool operates under the assumption that all revised filenames are unique and does not consider relative paths. If there are multiple occurrences of files with the same name in different directories within the file being rewritten, only the first occurrence will be preserved, potentially overwriting subsequent occurrences.
