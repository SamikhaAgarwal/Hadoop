**step 1:** cd /home/samiksha/hadoop-2.7.3/

**Step2:** Generate a test-case
`python3 generate.py 1.in 10 10 2`
Generates two matrices 10x10 and 10x2

**Step3:** Vanilla multiplier
`cat sample.txt`

**step4:**
`cat sample.txt | python3 mapper.py`

**step5:**
`cat sample.txt | python3 mapper.py | python3 reducer.py`

**step6:**
`chmod +x mapper.py`

**step5:**
`chmod +x reduser.py`

**step6:**
`cd`

**step7:**
`cd /home/samiksha/hadoop-2.7.3/sbin`

**step8:**
`./start-all.sh`

**step9:**
`jps`

**step10:**
`hadoop fs -mkdir -p /home/samiksha/vector_mult`

**step11:**
`hadoop fs -mkdir -p /home/samiksha/vector_mult/input`

**step12:**
`hadoop fs -put /home/samiksha/hadoop-2.7.3/sample.txt  /home/samiksha/vector_mult/input`

# How it works
Consider we want to multiply two matrices, M(m*n) and N(n*p). This results in a matrix like P(m*p).
Matrix P has m*p elements, therefore we have m*p reducers. Each element from matrix M participates exactly p times in key-value generation.
Each element from matrix N participates exactly m times in key-value generation.

Each time we visit an element from matrix M or N, we generate all key-value pairs necessary for reducers.

# Performance Considerations
Our mapping algorithm can be optimized to facilitate reading inputs that have array index already instead of calculating one at run-time. This
gives us the benefit of gaining the ability to run multiple mappers which drastically increases our load time in case of very large inputs.
However, the trade-off is, our input files will become larger in size. We can optimize that out by leaving off elements that our zero since
most of the matrices in real-life are sparce matrices.


**step13:** Testing with Apache Hadoop
`hadoop jar /home/samiksha/hadoop-2.7.3/share/hadoop/tools/lib/hadoop-streaming-2.7.3.jar -file /home/samiksha/hadoop-2.7.3/mapper.py /home/samiksha/hadoop-2.7.3/reducer.py -mapper "python3 mapper.py" -reducer "python3 reducer.py" -input /home/samiksha/vector_mult/input/sample.txt -output /home/samiksha/vector_mult/output`
 
**step14:**
`hadoop fs -cat /home/samiksha/vector_mult/output/*`

**NOTE**
The path to hadoop-streaming jar file might be different on your system.
