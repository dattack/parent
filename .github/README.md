# Deploy to Maven Central

## Create a GPG key

A requirement to deploy to Maven Central is to sign the artifacts with a GPG key. The following steps describe how to
create a GPG key and share it with the key servers:

1. Create a new GPG key

    ```bash
    gpg --gen-key --default-new-key-algo=rsa4096/cert,sign+rsa4096/encr
    ```
 
2. List the keys

    ```bash
    gpg --list-keys
    ```

    The output should look like this:

    ```
    /Users/cicd/.gnupg/pubring.kbx
    --------------------------------
    pub   rsa4096 2023-11-28 [SC] [expires: 2025-11-27]
    0D7F6634129D9E9408DE1AD409FE5874C9BD34D5
    uid           [ultimate] *********** <***********>
    sub   rsa4096 2023-11-28 [E] [expires: 2025-11-27]
   ```
3. Share the public key

   Current GPG Keyservers supported by Central Servers are:

   - `keyserver.ubuntu.com`
   - `keys.openpgp.org`
   - `pgp.mit.edu`

    ```bash
    gpg --keyserver keyserver.ubuntu.com --send-keys <key-id>
    gpg --keyserver keys.openpgp.org --send-keys <key-id>
    gpg --keyserver pgp.mit.edu --send-keys <key-id>
    ```

4. Export the public key

    ```bash
    gpg --armor --export <key-id> > gpg_key.asc
    ```

See also [https://central.sonatype.org/publish/requirements/gpg/](https://central.sonatype.org/publish/requirements/gpg/)

## Setup GitHub Actions

1. Create secrets:

   - Create a secret called `OSSRH_GPG_SECRET_KEY` with the value of the private key (file `gpg_key.asc` created in the previous step)
   - Create a secret called `OSSRH_GPG_SECRET_KEY_PASSPHRASE` containing the passphrase used to create the key.
   - Create a secret called `OSSRH_USERNAME` with the value of your Sonatype Jira username
   - Create a secret called `OSSRH_PASSWORD` with the value of your Sonatype Jira password

2. Create a file called `.github/workflows/deploy.yml` with the following content:

   ```yaml
   name: Deploy to Maven Central
   on:
     push:
       branches:
         - main
         - dev
   jobs:
     publish:
       runs-on: ubuntu-latest 
       steps:
         - uses: actions/checkout@v3
         - name: Set up JDK 8
           uses: actions/setup-java@v3
           with:
             java-version: '8'
             distribution: 'adopt'
             server-id: ossrh # Value of the distributionManagement/repository/id field of the pom.xml
             server-username: MAVEN_USERNAME # env variable for username in deploy
             server-password: MAVEN_PASSWORD # env variable for token in deploy
             gpg-private-key: ${{ secrets.OSSRH_GPG_SECRET_KEY }} # Value of the GPG private key to import
             gpg-passphrase: MAVEN_GPG_PASSPHRASE # env variable for GPG private key passphrase
         - name: Build with Maven
           run: mvn -B package
         - name: Deploy to Maven Central
           run: mvn -B deploy
           env:
             MAVEN_USERNAME: ${{ secrets.OSSRH_USERNAME }}
             MAVEN_PASSWORD: ${{ secrets.OSSRH_PASSWORD }}
             MAVEN_GPG_PASSPHRASE: ${{ secrets.OSSRH_GPG_SECRET_KEY_PASSWORD }}
   ```
