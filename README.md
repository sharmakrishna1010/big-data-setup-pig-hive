# Big Data Lab Setup – Hadoop, Apache Pig & Apache Hive

A ready-to-use Big Data environment featuring **Hadoop, Apache Pig, Apache Hive, and Spark**, running inside GitHub Codespaces using Docker.

No manual installation or complex configuration is required. Everything runs inside a preconfigured Docker container.

## Prerequisites

- A GitHub account.
- Access to GitHub Codespaces.
- Docker (preinstalled in GitHub Codespaces).

**GitHub Free Plan:** Includes 60 core hours per month for Codespaces.

---

## Step 1: Create a Blank Codespace

1. Log in to [GitHub Codespaces](https://github.com/codespaces).
2. Under **Explore quick start templates**, select the **Blank** template.
3. Launch your Codespace.
4. Wait for the cloud-based Linux terminal to initialize.

You should now have access to a Linux terminal where Docker commands can be executed.

## Step 2: Launch the Hadoop + Pig + Hive Container

Once the terminal loads, execute the following command:

```bash
docker run -it --name bigdata-lab suhothayan/hadoop-spark-pig-hive:2.9.2 bash
```

### Understanding the command

| Parameter | Description |
|---|---|
| `docker run` | Creates and starts a Docker container. |
| `-it` | Enables interactive terminal access. |
| `--name bigdata-lab` | Assigns the container the name `bigdata-lab`. |
| `suhothayan/hadoop-spark-pig-hive:2.9.2` | Specifies the preconfigured Docker image. |
| `bash` | Opens a Bash shell inside the container. |

Wait approximately 1–2 minutes for the Docker image to download.

Once the container starts, you should see a terminal prompt similar to:

```bash
root@<container-id>:/#
```

**Your Big Data environment is now ready!**

## Step 3: Launch Apache Pig

Apache Pig provides a high-level scripting language called **Pig Latin** for processing large datasets.

To start the Pig Grunt shell:

```bash
pig
```

You should now see the Pig prompt:

```text
grunt>
```

You can execute Pig Latin commands directly inside this shell.

### Run Pig in Local Mode

To execute Pig scripts locally without using Hadoop MapReduce:

```bash
pig -x local
```

This is useful for practising Pig Latin commands and working with local files.

## Step 4: Launch Apache Hive

Apache Hive provides a data warehouse system for querying and managing large datasets using **HiveQL**, an SQL-like query language.

To start the Hive CLI:

```bash
hive
```

You can now execute HiveQL queries.

### Troubleshooting: Hive Metastore Initialization

On the first launch, Hive may throw a metastore or schema initialization error.

To resolve this issue:

**1. Exit the Hive CLI:**

```sql
quit;
```

**2. Initialize the Derby metastore schema:**

```bash
$HIVE_HOME/bin/schematool -dbType derby -initSchema
```

**3. Launch Hive again:**

```bash
hive
```

The metastore should now be initialized.

---

## Step 5: Re-enter Your Existing Container

You do **NOT** need to download the Docker image or create a new container every time you reopen your Codespace.

To return to your existing container without losing the files or work stored inside it, execute:

```bash
docker start -ai bigdata-lab
```

### Understanding the command

| Parameter | Description |
|---|---|
| `docker start` | Starts an existing stopped container. |
| `-a` | Attaches your terminal to the container's output. |
| `-i` | Keeps the interactive input stream open. |
| `bigdata-lab` | The name of your existing container. |

Once executed, you should return to your container's terminal prompt:

```bash
root@<container-id>:/#
```

**Important:** This command starts your existing container; it does not create a new one. Your container's filesystem and previously saved files remain intact.

If the container is already running, use:

```bash
docker attach bigdata-lab
```

### Important Notes About Persistence

- Your files and configurations inside the container persist when the container is stopped and restarted.
- Do not use `docker rm bigdata-lab` unless you intentionally want to delete the container.
- Do not recreate the container using the initial `docker run` command every time.
- Keep your Codespace. Deleting the Codespace can also delete the Docker container and its stored data.

---

## Quick Command Reference

| Operation | Command |
|---|---|
| Create and launch container | `docker run -it --name bigdata-lab suhothayan/hadoop-spark-pig-hive:2.9.2 bash` |
| Re-enter existing container | `docker start -ai bigdata-lab` |
| Attach to running container | `docker attach bigdata-lab` |
| Start Apache Pig | `pig` |
| Start Pig in local mode | `pig -x local` |
| Start Apache Hive | `hive` |
| Initialize Hive Metastore | `$HIVE_HOME/bin/schematool -dbType derby -initSchema` |
| Exit container shell | `exit` |

---

## Final Result

You now have a cloud-based Big Data laboratory with a preconfigured environment for practising:

- **Apache Hadoop** – Distributed storage and processing.
- **Apache Pig** – Pig Latin scripting and data processing.
- **Apache Hive** – HiveQL queries and data warehousing.
- **Apache Spark** – Distributed data processing.

All of this runs inside GitHub Codespaces using a single Docker container, without requiring individual installations on your local machine.

**Happy Learning!**
