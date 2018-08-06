**In wordcoun.pdf , there are steps and commands for run the wordcount example.**

*these are the commands which is mentioned in the pdf* ->

Command: hadoop fs -mkdir /home/samiksha/wordcount
Command: hadoop fs -chown wordcount /home/samiksha/wordcount
Command: hadoop fs -mkdir  /home/samiksha/wordcount /input
Command: hadoop fs -mkdir  /home/samiksha/wordcount /output
Command: hadoop fs -ls /home/samiksha/wordcount
Command: hadoop fs -put /home/samiksha/hadoop-2.7.3/assingment1/sample\_text.txt /home/samiksha/wordcount /input
Command: mkdir -p build 
Command: javac -cp hadoop-core-1.2.1.jar:org.apache.commons.cli-1.2.0.jar WordCount.java -d build -Xlint 
Command: jar -cvf wordcount.jar -C build/ .
Command: hadoop jar wordcount.jar org.myorg.WordCount.WordCount /home/samiksha/wordcount/input /home/samiksha/wordcount/output
Command: hadoop fs -cat /home/samiksha/wordcount/output/*  
Command: hadoop fs -rm -r /home/samiksha/wordcount/output
Command: ./stop-all.sh}
