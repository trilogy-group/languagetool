# LanguageTool Development with DF Devspaces 

## Install DF Devspaces

1. Create and install devspaces client as it is written in help guide https://support.devspaces.io/article/22-devspaces-client-installation.

2. Here is some details about DF Devspaces https://devspaces.io/devspaces/help

Here follows the main commands used in Devspaces cli. 

|action   |Description                                                                                   |
|---------|----------------------------------------------------------------------------------------------|
|`devspaces --help`                    |Check the available command names.                               |
|`devspaces create [options]`          |Creates a DevSpace using your local DevSpaces configuration file |
|`devspaces start <devSpace>`          |Starts the DevSpace named \[devSpace\]                           |
|`devspaces bind <devSpace>`           |Syncs the DevSpace with the current directory                    |
|`devspaces info <devSpace> [options]` |Displays configuration info about the DevSpace.                  |

Use `devspaces --help` to know about updated commands.


### Start Devspaces 

This guide assumes that user is inside `devspaces` folder of the repository.

1.  Create DevSpaces.

```bash
devspaces create
```

2. Start your devspaces.
```bash
devspaces start languagetool
```

3. Start containers synchronization. Open a new terminal on a folder that should be synced with devspaces and run:

```bash
devspaces bind languagetool
```

4. Clone the source inside the sync folder from previous step. You may check out the sync process by openning http://localhost:49152/ in your browser.

```bash
git clone https://github.com/trilogy-group/languagetool.git
```

5. Get some information about created devspace. 

```bash
devspaces info languagetool
```

6. Connect to development container

```bash
devspaces exec languagetool
```

7. Source maven env variables

```bash
source /etc/profile.d/apache-maven.sh
```

8. Build the project 

```bash
cd language
mvn package -DskipTests
```

Or you may build different parts independetly.

Builds standalone package:

```bash
./build.sh languagetool-standalone package -DskipTests
```

Builds wikipedia package:

```bash
./build.sh languagetool-wikipedia package -DskipTests
```

9. Run the project.

```bash
cd languagetool-standalone/target/LanguageTool-4.3-SNAPSHOT/LanguageTool-4.3-SNAPSHOT
java -jar languagetool-commandline.jar -l <xx> <filename>
```

with `xx` being the code for your language, e.g. en-US for American English or just en for English without spell checking activated. For `filename` use any textfile.


10. Also you may run the test

```bash
cd ../../../../
mvn clean test
```

For more information you may check out this resource `https://github.com/trilogy-group/languagetool/blob/master/README.md`.