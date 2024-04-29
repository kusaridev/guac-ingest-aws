# guac-ingest-aws action

This Action ingests SBOMs and Attestations into
[GUAC](https://github.com/guacsec/guac) as part of your github
workflow.
Authentication is provided by GitHub's OIDC provider and AWS IAM assume role. This will enable quick and easy integration to your GUAC
instance with very minimal input.

For details on how to query and utilize the data upon ingestion, please see documentataion for the [GUAC use cases](https://docs.guac.sh/guac-use-cases/). 

This action will only work with [The Kusari hosted GUAC platform](https://www.kusari.dev/).  

## Usage

See [action.yaml](action.yaml)

```yaml
steps:
  - uses: actions/checkout@v3

  - uses: [Your build and SBOM/Provenance generation steps]

  - uses: kusaridev/guac-ingest-aws@v0
    name: GUAC ingestion
    with:
      files: './spdx.json'
      iam-role-arn: [IAM assumable role arn provided by the Kusari team]
      blob-addr: [Blob store address provided by the Kusari team]
      pubsub-addr: [Pubsub address provided by the Kusari team]

```

## Inputs

### `files`

**Required** Path to directory or specific file to ingest

### `iam-role-arn`

**Required** IAM assumeable role ARN

### `blob-addr`

**Required** Blob store address

### `pubsub-addr`

**Required** Pubsub address

## Outputs

### `console_out`

Raw output of the guacone command

# License

The scripts and documentation in this project are released under the [Apache License](LICENSE)