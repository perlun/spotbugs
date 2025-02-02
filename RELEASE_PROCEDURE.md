# Release procedure

When you release fixed version of SpotBugs, please follow these procedures.

## Update version info

* `version` in `build.gradle`
* version number in `CHANGELOG.md`
* `version`, `full_version`, `maven_plugin_version` and `gradle_plugin_version` in `docs/conf.py`

## Release to Maven Central

When we push a tag, the build result on GitHub Actions will be deployed to the [SonaType Nexus](https://oss.sonatype.org/), and published to the Maven Central automatically by [Gradle Nexus Publish Plugin](https://github.com/gradle-nexus/publish-plugin). Then we can find [artifacts in the Maven Central](https://repo1.maven.org/maven2/com/github/spotbugs/) after several hours.
See the `build` phase in `.github/workflows/release.yml` calling the `publishToSonatype` and `closeSonatypeStagingRepository` gradle tasks.

## Release to Eclipse Update Site

It's automated by GitHub CI.

When we push tag, the build result will be deployed to [eclipse-candidate repository](https://github.com/spotbugs/eclipse-candidate).
When we push tag and its name doesn't contain `_RC`, the build result will be deployed to [eclipse repository](https://github.com/spotbugs/eclipse).

See `Deploy eclipse`, `Deploy eclipse-candidate` and `Deploy eclipse-latest` phases in `.github/workflows/release.yml` for detail.

## Release to Eclipse Marketplace

Update version in [Eclipse Marketplace page](https://marketplace.eclipse.org/content/spotbugs-eclipse-plugin). If you have no permission, please contact with @KengoTODA or @iloveeclipse.

## Release to Gradle Plugin Portal

No action necessary. When we push tag, the build result on GitHub CI will be deployed to Gradle Plugin Portal.

## Release to ReadTheDocs

See [docs/README.md](docs/README.md) for detail.

## Update the Changelog at GitHub Release

The `CHANGELOG` on the [GitHub release page](https://github.com/spotbugs/spotbugs/releases) only contains a link to the correct version of the `CHANGELOG.md` file (see `createReleaseBody` task in `build.gradle`). It needs to be manually updated after the new GitHub release is created.