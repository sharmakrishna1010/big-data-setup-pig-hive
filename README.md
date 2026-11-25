# big-data-setup-pig-hive

You can launch a complete Hadoop, Pig, and Hive environment inside GitHub Codespaces in about two minutes using Docker, which comes preinstalled in every Codespace.

Step 1: Open a Blank Codespace

1. Log into GitHub Codespaces with your free GitHub account (includes 60 free core hours/month).
2. Under Explore quick start templates, click Use this template on the Blank template to spin up a cloud Linux terminal in your browser.

Step 2: Run the Prebuilt Hadoop + Pig + Hive Container

Once the terminal loads at the bottom of the screen, paste and run this single command to pull and start a preconfigured container with Hadoop, Pig, and Hive already wired together:
bash
'''bash
docker run -it --name bigdata-lab suhothayan/hadoop-spark-pig-hive:2.9.2 bash
'''
Use code with caution.
(Wait about 1–2 minutes for the image to download and drop you into the root@...:/# container prompt.)

Step 3: Launch Pig Latin or HiveQL

Inside the container shell, both tools are ready to run immediately:
• Start Apache Pig (Grunt shell):bash
'''bash
pig
'''
Use code with caution.
(To run Pig in fast local mode without waiting for MapReduce jobs, use pig -x local instead.)
• Start Apache Hive (HiveQL prompt):bash
'''bash
hive
'''
Use code with caution.
(If Hive throws a metastore error on first launch, exit with quit; and run $HIVE_HOME/bin/schematool -dbType derby -initSchema once, then type hive again.)
