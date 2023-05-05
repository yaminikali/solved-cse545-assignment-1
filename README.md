Download Link: https://assignmentchef.com/product/solved-cse545-assignment-1
<br>
<u>Overview</u>

<u>Part I. Streaming (35 points)</u>

<u>Part I. MapReduce (65 points)</u>

<u>Part II. Spark and Streaming (50 points)</u>

Overview

<table style="height: 422px;" width="1058">

 <tbody>

  <tr>

   <td width="639">Goal: Gain experience working with streaming algorithms as well as MapReduce work ow systems. Gain experience simulating working with a distributed le system.Requirements. You must use Python version 3.5 or later.  You do not need a distribution of MapReduce for this assignment as we will use our own basic simulator (see task II.A.) — future assignments will use MapReduce on a cluster.Templates and Python Libraries. Template code is provided for each part of the assignment. Each template includes all of the data science, machine learning, or statistics libraries that you may import. Other data science, machine learning, or statistics related libraries are prohibited unless listed below —  ask if unsure. The intention is for you to implement the algorithms we have gone over and problem solve in order to best understand the concepts of this course and their practical application.Within the templates, all provided method names and classes must be used as provided with the same parameters. However, you may also use additional methods to keep your code clean.Additional approved libraries that are not in the template will be listed here (if any): datetime random.shuffle</td>

  </tr>

  <tr>

   <td width="639"> </td>

  </tr>

 </tbody>

</table>

Part I. Streaming (35 points)

<table width="639">

 <tbody>

  <tr>

   <td width="639">Here, you will implement and evaluate the runtime of the typical multi-level sampler as well as the“streaming” sampler that we went over in class. We call it a “multi-level sampler” because the level of analysis we wish to sample (e.g. user level) is not the same level with which the data arrives (e.g. transaction level).Data: to complete these tasks, you be provided transaction data of the following form: record_id, date, user_id, amountrecord_id — unique id for the transactiondate — date of the transactionuser_id — id for the user making the transactionamount — the amount of the transaction The data is provided in three les1)  <a href="https://www.google.com/url?q=http://www3.cs.stonybrook.edu/~has/CSE545/a1/transactions_small.csv&amp;sa=D&amp;ust=1581472660870000">transactions_small.csv</a>2)  <a href="https://www.google.com/url?q=http://www3.cs.stonybrook.edu/~has/CSE545/a1/transactions_medium.csv.zip&amp;sa=D&amp;ust=1581472660871000">Transactions_medium.csv</a> [zip]3)  Transactions_large.csv [zip; to be released]Task I.A) Typical non-streaming multi-level sampler (15 points)Implement the standard non-streaming sampling methodStep 1: read le to pull out unique user_ids from leStep 2: subset to random  1% of user_idsStep 3: read le again to pull out records from the 1% user_idand compute mean and standard deviation withinTask I.B) Streaming multi-level sampler (15 points)Implement the streaming multi-level sampling code we went over in class which uses hash functions on the user_id to read through the le once. Technically, we are simulating a web stream of data by instead taking a single pass at a le but you should see the advantage of this algorithm even for sampling from les.  Record the information that is needed in order to compute the mean and standard deviation.  Your sample should correspond to  2% and .5% of the user_ids in each le (approximate, especially in the case of the small le).  Make sure to use a streaming mean and std-dev (see rules in method description).Task I.C) Timing (5 points)Time wall-clock processing time, in milliseconds, over di erent sizes of data: small(10,000) medium(1,000,000) and large (100,000,000)Report runtimes and results for both implementations above, using percentages of .02 and .005 for each of the three les (small may not have an adequate sample at .005: that’s ok).</td>

  </tr>

  <tr>

   <td width="639">Template Code for Part I.  A template to be lled in with your code is provided here: <a href="https://www.google.com/url?q=http://www3.cs.stonybrook.edu/~has/CSE545/a1/sampler_lastname_id_v01.py&amp;sa=D&amp;ust=1581472660873000">sampler_lastname_id.py</a> <a href="https://www.google.com/url?q=http://www3.cs.stonybrook.edu/~has/CSE545/a1/sampler_lastname_id_v01.py&amp;sa=D&amp;ust=1581472660873000"> </a></td>

  </tr>

 </tbody>

</table>

Part II. MapReduce (65 points)

<table width="639">

 <tbody>

  <tr>

   <td width="639">Here, you will complete a back-end for a MapReduce system and test it on a couple MapReduce jobs: word count (provided), and meanCharsMR (you must implement). Template code is provided. Speci cally, you must complete:Task I.A) PartitionFunction (10 points)Complete the partition function, making sure to use a hash that can handle: integers and strings.Task I.B) RunSystem (20 points)Complete the “runSystem(self)” method which divides the data into chunks and schedules the running of mapTasks and reduceTasks. The are two places to complete:(1) Divide up the data into chunks according to num_map_tasks, and launch a map task per chunk.</td>

  </tr>

  <tr>

   <td width="639">(2) Send each key-value pair to its assigned reducer.Task I.C) Combiner (15 points)Edit the “MapTask” method to add support for running a Combiner. Look for “#&lt;&lt;COMPLETE&gt;&gt;”  within the method. Remember, a combiner runs the reduce task at the end of the map task in order to save communication cost of sending to multiple reducers. Note: main will run the WordCountBasicMR to test with and without the combiner. It is recommended that you look over the WordCountBasicMR to understand what it is doing.  You can assume your combiner code will only run on reducers that are both commutative and associative (see hint at bottom).Task I.D) Mean CharsMR (20 points)Edit the “map” and “reduce” methods of “MeanCharsMR” to implement a map-reduce computation of the mean and standard deviation number of each character (a-z, case insensitive) in each document.</td>

  </tr>

  <tr>

   <td width="639">Template Code for Part II.  A template to be lled in with your code is provided here:<a href="https://www.google.com/url?q=http://www3.cs.stonybrook.edu/~has/CSE545/a1/MRSystemSimulator2020_lastname_id_v01.py&amp;sa=D&amp;ust=1581472660876000">MRSystemSimulator2020_lastname_id.py</a></td>

  </tr>

 </tbody>

</table>

Submission

<table width="639">

 <tbody>

  <tr>

   <td width="639">Please use blackboard to submit two les each with your lastname and student id:1.  sampler_&lt;lastname&gt;_&lt;id&gt;.py2.  MRSystemSimulator2020_&lt;lastname&gt;_&lt;id&gt;.pyDo not upload a zip le. Double-check that your les are there and correct after uploading and make sure to submit.  Uploading les that are zips or any other type than python code les will result in the submission being considered invalid. Partially uploaded les or non-submitted les will count as unsubmitted. Questions: Please post questions to the course piazza page.<u>Hints</u>As questions come in this location will be used to track suggestions.● Combiners require a reduce function that is both commutative and associative: f(v1, v2) = f(v2, v1)                 and      f(f(v1, v2), v3) = f(v1, f(v2, v3))</td>

  </tr>

 </tbody>

</table>


