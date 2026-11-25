# Big Data Environment Setup – Hadoop, Pig & Hive

Set up a complete **Hadoop, Apache Pig, and Apache Hive environment** inside GitHub Codespaces using Docker. No manual installation or complex configuration is required.

## Step 1: Open a Blank Codespace

1. Log in to [GitHub Codespaces](https://github.com/codespaces) using your GitHub account.
2. Under **Explore quick start templates**, select the **Blank** template.
3. Launch your Codespace to open a cloud-based Linux development environment.

**Note:** GitHub's free plan includes 60 core hours per month.

## Step 2: Launch the Preconfigured Docker Container

Once the Codespaces terminal loads, execute the following command:

```bash
docker run -it --name bigdata-lab suhothayan/hadoop-spark-pig-hive:2.9.2 bash
```

**What this command does:**
- `docker run` – Creates and starts a Docker container.
- `-it` – Enables interactive terminal access.
- `--name bigdata-lab` – Assigns the container the name `bigdata-lab`.
- `suhothayan/hadoop-spark-pig-hive:2.9.2` – Specifies the preconfigured Docker image.
- `bash` – Opens a Bash shell inside the container.

Wait approximately 1–2 minutes for the Docker image to download. Once started, you should see a container prompt similar to:

```bash
root@<container-id>:/#
```

**Your Hadoop, Pig, and Hive environment is now available inside the container.**

## Step 3: Launch Apache Pig and Apache Hive

Both tools are preconfigured in the container and can be launched directly from its terminal.

### A. Apache Pig (Grunt Shell)

To start Apache Pig:

```bash
pig
```

This opens the **Pig Grunt shell**, where you can execute Pig Latin commands.

To run Pig in local mode instead of using Hadoop MapReduce:

```bash
pig -x local
```

### B. Apache Hive (HiveQL)

To start Apache Hive:

```bash
hive
```

This opens the **Hive CLI**, where you can execute HiveQL queries.

**Troubleshooting: Hive Metastore Initialization**

On the first launch, Hive may throw a metastore or schema initialization error.

To resolve this:

1. Exit the Hive CLI:

   ```sql
   quit;
   ```

2. Initialize the Derby metastore schema:

   ```bash
   $HIVE_HOME/bin/schematool -dbType derby -initSchema
   ```

3. Launch Hive again:

   ```bash
   hive
   ```

## Quick Reference

| Task | Command |
|---|---|
| Start Pig | `pig` |
| Start Pig in local mode | `pig -x local` |
| Start Hive | `hive` |
| Initialize Hive Metastore | `$HIVE_HOME/bin/schematool -dbType derby -initSchema` |

---

**Result:** You now have a ready-to-use cloud environment for practising Hadoop, Pig Latin, and HiveQL without installing these tools individually on your local machine.
