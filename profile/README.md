## AMSA Code

The public repositories are published to Maven Central under the groupId `au.gov.amsa`
To be able to deploy release, you need to follow the Maven [procedure](https://central.sonatype.org/publish/publish-maven/#distribution-management-and-authentication) an register yourself to be able to do so (when asking just cc someone who already have the karma to do so).

Then you need to have a `settings.xml` with the following entry:
```
    <server>
      <id>ossrh-staging</id>
      <username></username>
      <password></password>
    </server>
    <server>
      <id>ossrh</id>
      <username></username>
      <password></password>
    </server>
    <server>
      <id>ossrh-snapshots</id>
      <username></username>
      <password></password>
    </server>

```

You need to upload your gpg key to a public gpg key server (see details [here](https://central.sonatype.org/publish/requirements/gpg/#gpg-signed-components)

A release is as simple as (quick one skipping test): `mvn release:prepare release:perform -DskipTests -Dmaven.release.plugin.arguments="-DskipTests -Dspotbugs.skip=true" -DlocalCheckout=true -B`

Then you log in to https://oss.sonatype.org/ and look at the staging repositories to close and release it.
