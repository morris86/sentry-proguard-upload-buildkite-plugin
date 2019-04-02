# sentry-proguard-upload-buildkite-plugin

A [Buildkite](https://buildkite.com/) plugin to upload Android app ProGuard mapping files to [Sentry](https://sentry.io/).

## Example

```yml
steps:
  - name: ":package:"
    command: ./gradlew assembleRelease
    env:
      SENTRY_ORG: organization
      SENTRY_PROJECT: project
    plugins:
      - sentry-proguard-upload:
          merged_manifest: "app/build/intermediates/merged_manifests/release/AndroidManifest.xml"
          mapping: "app/build/outputs/mapping/r8/release/mapping.txt"
          write_properties: "app/build/intermediates/assets/release/sentry-debug-meta.properties"
```

## Environment Variables

### `SENTRY_AUTH_TOKEN`

Specifies the Sentry authentication token

## Options

### `org`

Specifies the Sentry organization slug

### `org-from`

Specifies the environment variable containing the Sentry organization slug

Default: `SENTRY_ORG`

### `project`

Specifies the Sentry project slug

### `project-from`

Specifies the environment variable containing the Sentry project slug

Default: `SENTRY_PROJECT`

### `merged_manifest`

Specifies the path to the merged (or full) AndroidManifest.xml file

### `mapping`

Specifies the path to the ProGuard mapping file to upload

### `write_properties`

Specifies the path where Sentry should write out metadata that is generated. Usually this metadata is just a hash of the mapping file.

## License

MPL 2.0 (see [LICENSE](LICENSE))
