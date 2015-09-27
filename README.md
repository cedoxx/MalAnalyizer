# MalAnalizer
PCAP to CSV [Protect all packet fields]

To Execute PCapProcess.java specifying 2 arguments:
1. Input path (containing pcap files)
2. Output path (where csv files are to be generated - will be input to Flume SpoolDir source)

The program runs in a continuous loop looking for pcap files to be converted.

Following features have been added:
1. Program execution in a continuous loop
2. Proper logging with java.util.logging.
3. sync. of header sequence across pcap files 
    (the numerical IDs of headers are persisted in a properties file in the user home folder)
4. renaming pcap files - adding .COMPLETED suffix after processing them
5. storing global values thru PCapGlobalHeader - check in CSV file

A) The output will serve as a continous input for flume source.
B) Created a Avro Schema using kitesdk's kite-dataset.
C) Locally Created flume spoolDir Source and transferred the files to HDFS 
D) Currently I'm working on morphlines flume interceptor plug-in to convert the CSV File from spoolDirectory source
(The program , its output will be the continous input for flume source) to Avro Container file in HDFS.
