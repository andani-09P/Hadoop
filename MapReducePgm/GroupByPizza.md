    package com.stackoverGroup;

    import java.io.DataInput;
    import java.io.DataOutput;
    import java.io.IOException;

    import org.apache.hadoop.conf.Configuration;
    import org.apache.hadoop.fs.Path;
    import org.apache.hadoop.io.IntWritable;
    import org.apache.hadoop.io.LongWritable;
    import org.apache.hadoop.io.Text;
    import org.apache.hadoop.io.WritableComparable;
    import org.apache.hadoop.mapreduce.Job;
    import org.apache.hadoop.mapreduce.Mapper;
    import org.apache.hadoop.mapreduce.Reducer;
    import org.apache.hadoop.mapreduce.lib.input.FileInputFormat;
    import org.apache.hadoop.mapreduce.lib.output.FileOutputFormat;
    import org.apache.hadoop.util.GenericOptionsParser;
    import org.apache.hadoop.mapreduce.OutputFormat;

    import org.apache.hadoop.mapreduce.JobContext;

    public class GroupMR {

    public static class GroupMapper extends Mapper<LongWritable, Text, Text, Text> {

        Text numpass = null;
        Text monyeartext = null;

        public void map(LongWritable key, Text value, Context context) throws IOException, InterruptedException {
            String line = value.toString();
            String[] keyvalue = line.split(",");
            String[] monyeartext1 = keyvalue[0].split("/");
            monyeartext = new Text(monyeartext1[2] + "/" +monyeartext1[0] );
            numpass = new Text(keyvalue[1] + "-" + keyvalue[4]);
            context.write(monyeartext, numpass);
           
        }
    }

    public static class GroupReducer extends Reducer<Text, Text, Text, IntWritable> {
        public void reduce(Text key, Iterable<Text> values, Context context)
                throws IOException, InterruptedException {
            boolean doesExist = false;
            int sum = 0;           
            for (Text val : values) {
                String[] val2 = val.toString().split("-");
                if (val2[0].equals("Pizza") || val2[0].equals("Pasta") ){
                    sum += Integer.parseInt(val2[1]);
                }
            }
            context.write(key, new IntWritable(sum));
        }
    }

    public static void main(String[] args) throws IOException, ClassNotFoundException, InterruptedException {
        Configuration conf = new Configuration();
        String[] otherArgs = new GenericOptionsParser(conf, args).getRemainingArgs();
        if (otherArgs.length < 2) {
            System.err.println("Usage: wordcount <in> [<in>...] <out>");
            System.exit(2);
        }
        Job job = Job.getInstance(conf, "GroupMR");
        job.setJarByClass(GroupMR.class);
        job.setMapperClass(GroupMapper.class);
    
        job.setReducerClass(GroupReducer.class);
        job.setOutputKeyClass(Text.class);
        job.setOutputValueClass(Text.class);
       
        //for (int i = 0; i < otherArgs.length - 1; ++i) {
        	FileInputFormat.addInputPath(job, new Path(otherArgs[0]));
       // }
        
        FileOutputFormat.setOutputPath(job, new Path(otherArgs[1]));
        System.exit(job.waitForCompletion(true) ? 0 : 1);
    }
    }
