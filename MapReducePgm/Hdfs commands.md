# Commands
All basic commands

<h1>HADOOP COMMANDS</h1>

<h2>hdfs (options)</h2>

<h3>hdfs dfs (options)</h3>

 <p> dfs                    run a filesystem command on the file systems supported in Hadoop.


</p>

```
Usage: hdfs dfs [generic options]

```
<br/>
<br/>

**[-appendToFile &nbsp;&nbsp;[localsrc]  [dst]]:**&nbsp;&nbsp;&nbsp;&nbsp; used to append file into hdfs dirctory
	 
	 usage: hdfs dfs -appendToFile /home/<localdir.path>  <hdfs path>
	 
	
	
<br/>
<br/>
	
	
**[-cat &nbsp;&nbsp; [src] ]:** &nbsp;&nbsp;&nbsp;&nbsp;  Fetch all files that match the file pattern <src> and display their content on stdout.
	 
	 usage: hdfs dfs -cat <file from hdfs>
<br/>
<br/>

	
	
**[-checksum  &nbsp;&nbsp;[rc] ]:** &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  Dump checksum information for files that match the file pattern <src> to stdout.
                           Note that this requires a round-trip to a datanode storing each block of the,
                           and thus is not efficient to run on a large number of files. The checksum
                           of a file depends on its content, block size and the checksum algorithm and
                           parameters used for creating the file.
                            
	 usage: hdfs dfs -checksum hdfs://nn1.example.com/file1
            hdfs dfs -checksum file:///etc/hosts
	 
<br/>
<br/>





**[-chgrp &nbsp;&nbsp;[-R]&nbsp;&nbsp; GROUP &nbsp;&nbsp;PATH]:** &nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Change group association of files,The -R option will make the change recursively through the directory structure.
	                            
     usage: hdfs dfs  -chgrp owner:group <path_of_file>
    



<br/>
<br/>


**[-chmod&nbsp;&nbsp; [-R] &nbsp;&nbsp;[MODE[,MODE] | OCTALMODE]&nbsp;&nbsp; PATH]:**  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Change the permissions of files, This works similar to the shell's chmod.
<MODE>       Mode is the same as mode used for the shell's command. The only   
               letters recognized are 'rwxXt', e.g. +t,a+r,g-w,+rwx,o=r.         
<OCTALMODE>  Mode specifed in 3 or 4 digits. If 4 digits, the first may be 1 or
               0 to turn the sticky bit on or off, respectively.  Unlike the     
               shell command, it is not possible to specify only part of the     
               mode, e.g. 754 is same as u=rwx,g=rx,o=r.
                                                                   
	 usage: hdfs dfs -chmod [-R] <MODE[,MODE]... | OCTALMODE> URI [URI ...]
	 




<br/>
<br/>

	
**[-chown&nbsp;&nbsp; [-R] &nbsp;&nbsp;[OWNER][:[GROUP]] &nbsp;&nbsp;PATH]:** &nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Changes owner and group of a file. This is similar to the shell's chown command.
                                           
                                            
     usage:hdfs dfs -chown -R OWNER:GROUP <file_path>                                                                 
     
  
  
<br/>
<br/>
 
  
  
**[-copyFromLocal &nbsp;&nbsp; [localsrc] &nbsp;&nbsp; [dst]]** &nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Used to copy from local to hadoop file system
	                                                     Identical to the -put command.
	                                                     
	  usage:hdfs dfs -copyFromLocal <local_dir_path> <hdfs_dir_path>
<br/>
<br/>
	
**[-copyToLocal &nbsp;&nbsp; [src] &nbsp;&nbsp; [local_dst]]**    Used to copy from hadoop file system to local  file system
	                                                                 Identical to the -put command.
	                                                            
	  usage:hdfs dfs -copyToLocal <hdfs dfs_dir> <local_dir_path>
<br/>
<br/>
	 
	 
**[-count &nbsp;&nbsp;[-q] &nbsp;&nbsp;[-h] &nbsp;&nbsp;[-v] &nbsp;&nbsp;[-x] &nbsp;&nbsp;[path] ]:** &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  Count the number of directories, files and bytes under the paths
                                             that match the specified file pattern.  The output columns are:
                                              DIR_COUNT FILE_COUNT CONTENT_SIZE PATHNAME
                                             or, with the -q option:
                                             QUOTA REM_QUOTA SPACE_QUOTA REM_SPACE_QUOTA
                                             DIR_COUNT FILE_COUNT CONTENT_SIZE PATHNAME
                                             The -h option shows file sizes in human readable format.
                                             The -v option displays a header line.
                                             The -x option excludes snapshots from being calculated.
                                            
      usage:hdfs dfs -count <dir_path>
    
<br/>
<br/>
    
    
**[-cp&nbsp;&nbsp; [-f]&nbsp;&nbsp; [-p | -p[topax]]&nbsp;&nbsp; [src] &nbsp;&nbsp; [dst]]:** &nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Copy files that match the file pattern <src> to a destination.  When copying
  multiple files, the destination must be a directory. Passing -p preserves status.


                                          
      usage:hdfs dfs -cp <src_dir> <dest_dir>
   
<br/>
<br/>
    
**[-createSnapshot &nbsp;&nbsp;[snapshotDir] &nbsp;&nbsp;[snapshotName]]:** &nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Create a snapshot on a directory
    
    	usage:hdfs dfs -createSnapshot <snapshotDir> [<snapshotName>]
<br/>
<br/>

**[-deleteSnapshot&nbsp;&nbsp; [snapshotDir] &nbsp;&nbsp;[snapshotName]]:** Delete a snapshot on a directory
	
	   usage:hdfs dfs -deleteSnapshot <snapshotDir> <snapshotName>
<br/>
<br/>
	
**[-df &nbsp;&nbsp;[-h]&nbsp;&nbsp; [path]  ]:** &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Shows the capacity, free and used space of the filesystem. If the filesystem has multiple partitions, and no path to a particular partition is specified, then the status of the root partitions will be shown.
                             -h  Formats the sizes of files in a human-readable fashion rather than a number of bytes.  
     
      usage: hdfs dfs -df -h <path>
    
<br/>
<br/>
   
**[-du &nbsp;&nbsp;[-s]&nbsp;&nbsp; [-h]&nbsp;&nbsp; [-x]&nbsp;&nbsp; [path] ]:** &nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Show the amount of space, in bytes, used by the files that match the specified file pattern. The following flags are optional:
                                                                                 
                              -s  Rather than showing the size of each individual file that matches the      
                                  pattern, shows the total (summary) size.                                   
                              -h  Formats the sizes of files in a human-readable fashion rather than a number
                                  of bytes.                                                                  
                              -x  Excludes snapshots from being counted.                                     
                              
                             
        usage:hdfs dfs -du <path>                     
<br/>
<br/>

**[-expunge]:** &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;               Empty the Trash

       usage:hdfs dfs -epunge
<br/>
<br/>

**[-find &nbsp;&nbsp;[path]] &nbsp;&nbsp; [expression] ]:** &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Finds all files that match the specified expression and applies selected actions to them. If no <path> is specified then defaults to the current working directory. If no expression is specified then defaults to -print.
                                     
        usage:hdfs dfs -find <file_name>                                        
<br/>
<br/>

**[-get &nbsp;&nbsp;[-p] &nbsp;&nbsp; [src] &nbsp;&nbsp;[localdst]] :** &nbsp;&nbsp;&nbsp;&nbsp;&nbspCopy files that match the file pattern <src> to the local name.  <src> is kept. 
  When copying multiple files, the destination must be a directory. Passing -p preserves access and modification times, ownership and the mode. 
                                             
        usage:hdfs dfs -get <local_dir_path> <hdfs_dest>
<br/>
<br/>
    
**[-getfacl &nbsp;&nbsp;[-R] &nbsp;&nbsp;[path]]:** &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Displays the Access Control Lists (ACLs) of files and directories. If a directory has a default ACL, then getfacl also displays the default ACL.
                                                                                          
     
        usage:hdfs dfs getfacl -R <path>
<br/>
<br/>
        
**[-getmerge &nbsp;&nbsp;[-nl]&nbsp;&nbsp; [src] &nbsp;&nbsp;[localdst]]:** &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Get all the files in the directories that match the source file pattern and merge and sort them to only one file on local fs. <src> is kept.
                                                                                    
                              -nl  Add a newline character at the end of each file. 
        usage:hdfs dfs -getmerge <src> <local_dst_path>                      
<br/>
<br/>
                              

**[-help &nbsp;&nbsp;[cmd]] :** &nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Displays help for given command or all commands if none is specified.
   
        usage:hdfs dfs -help [cmd]
<br/>
<br/>

**[-ls &nbsp;&nbsp;[-C] &nbsp;&nbsp;[-d]&nbsp;&nbsp; [-h]&nbsp;&nbsp; [-q]&nbsp;&nbsp; [-R] &nbsp;&nbsp;[-t] &nbsp;&nbsp;[-S] &nbsp;&nbsp;[-r] &nbsp;&nbsp;[-u]&nbsp;&nbsp; [<path> ...] ]:** &nbsp;&nbsp;&nbsp;&nbsp;&nbsp; List the contents that match the specified file pattern. If path is not
                                              specified, the contents of /user/<currentUser> will be listed. For a directory a
                                              list of its direct children is returned (unless -d option is specified).
                                              
                                              Directory entries are of the form:
                                              	permissions - userId groupId sizeOfDirectory(in bytes)
                                              modificationDate(yyyy-MM-dd HH:mm) directoryName
                                              
                                              and file entries are of the form:
                                              	permissions numberOfReplicas userId groupId sizeOfFile(in bytes)
                                              modificationDate(yyyy-MM-dd HH:mm) fileName
                                              
                                                -C  Display the paths of files and directories only.
                                                -d  Directories are listed as plain files.
                                                -h  Formats the sizes of files in a human-readable fashion
                                                    rather than a number of bytes.
                                                -q  Print ? instead of non-printable characters.
                                                -R  Recursively list the contents of directories.
                                                -t  Sort files by modification time (most recent first).
                                                -S  Sort files by size.
                                                -r  Reverse the order of the sort.
                                                -u  Use time of last access instead of modification for
                                                    display and sorting.
                                                  
        usage:hdfs dfs -ls <dir_path>
<br/>
<br/>
       

**[-mkdir &nbsp;&nbsp;[-p]&nbsp;&nbsp; [path] ] :** &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Create a directory in specified location.
                                                                          
                          -p  Do not fail if the directory already exists 
     
        usage:hdfs dfs -mkdir <dir_name>
<br/>
<br/>
     
**[-moveFromLocal&nbsp;&nbsp; [local_src] &nbsp;&nbsp; [dst] ]:** &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Same as -put, except that the source is deleted after it's copied.
       
         usage:hdfs dfs -moveFromLocal <local_path> <hdfs_path>
        
        
<br/>
<br/>

**[-moveToLocal &nbsp;&nbsp;[src] &nbsp;&nbsp;[local_dst] ]:** &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;same as -put,except that the source is deleted after it's copied.
        
         usage:hdfs dfs -moveToLocal <hdfs_path> <local_path>
<br/>
<br/>
         

**[-mv &nbsp;&nbsp;[src] &nbsp;&nbsp; [dst] ]:** &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;         Move files that match the specified file pattern <src> to a destination <dst>. 
                      When moving multiple files, the destination must be a directory.

         usage:hdfs dfs -mv <src> <dst>
    
<br/>
<br/>

 **[-put &nbsp;&nbsp;[-f]&nbsp;&nbsp; [-p] &nbsp;&nbsp;[-l] &nbsp;&nbsp;[localsrc] &nbsp;&nbsp; [dst]] :**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 
                                              Copy files from the local file system into fs. Copying fails if the file already
                                              exists, unless the -f flag is given.
                                              Flags:
                                                                                                                   
                                              -p  Preserves access and modification times, ownership and the mode. 
                                              -f  Overwrites the destination if it already exists.                 
                                              -l  Allow DataNode to lazily persist the file to disk. Forces        
                                                     replication factor of 1. This flag will result in reduced
                                                     durability. Use with care.
                                                    
        usage:hdfs dfs -put <local_dir_path> <dst>
     
<br/>
<br/>
    
    
**[-rm &nbsp;&nbsp;[-f]&nbsp;&nbsp; [-r|-R] &nbsp;&nbsp;[-skipTrash]&nbsp;&nbsp; [src] ]:**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
                                              Delete all files that match the specified file pattern. Equivalent to the Unix
                                              command "rm <src>"
                                                                                                                             
                                              -skipTrash  option bypasses trash, if enabled, and immediately deletes <src>   
                                              -f          If the file does not exist, do not display a diagnostic message or 
                                                          modify the exit status to reflect an error.                        
                                              -[rR]       Recursively deletes directories  
                                            
       usage:hdfs dfs -rm <file_path>
       
<br/>
<br/>
    
**[-rmdir &nbsp;&nbsp;&nbsp;[dir]] :**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
                                              Removes the directory entry specified by each directory argument, provided it is empty.
                                               
        usage:hdfs dfs -rmdir <dir_name>
     
    
<br/>
<br/>
                                     
    
**[-setrep &nbsp;&nbsp;[-R] &nbsp;&nbsp;[-w]&nbsp;&nbsp;&nbsp;&nbsp; [rep] &nbsp;&nbsp;[path] ] :**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
                                          Set the replication level of a file. If <path> is a directory then the command
                                          recursively changes the replication factor of all files under the directory tree
                                          rooted at <path>.
                                                                                                                         
                                          -w  It requests that the command waits for the replication to complete. This   
                                              can potentially take a very long time.                                     
                                          -R  It is accepted for backwards compatibility. It has no effect.  
       
        usage:hdfs dfs -setrep <rep_factor> <file_path>
<br/>
<br/>
      
    
**[-stat &nbsp;&nbsp;[format]&nbsp;&nbsp; [path] ]:**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
                                  Print statistics about the file/directory at <path> in the specified format.
                                  Format accepts filesize in blocks (%b), group name of owner(%g), filename (%n),
                                  block size (%o), replication (%r), user name of owner(%u), modification date
                                  (%y, %Y)
       
        usage:hdfs dfs -stat <(format)> <path>
      
      
<br/>
<br/>
    
**[-tail &nbsp;&nbsp;[-f]&nbsp;&nbsp; [file] ]:**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Show the last 1KB of the file.
                                                 
                       -f  Shows appended data as the file grows.
       
       usage:hdfs dfs -tail <file_path>
      
<br/>
<br/>
    
**[-test &nbsp;&nbsp;-[defsz] &nbsp;&nbsp;[path] ]:**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
                              Answer various questions about <path>, with result via exit status.
                                -d  return 0 if <path> is a directory.
                                -e  return 0 if <path> exists.
                                -f  return 0 if <path> is a file.
                                -s  return 0 if file <path> is greater than zero bytes in size.
                                -z  return 0 if file <path> is zero bytes in size, else return 1.
                                
        usage:hdfs dfs -test -[defsz] <path>
     
<br/>
<br/>
    
    
**[-text &nbsp;&nbsp;&nbsp; [src] ]:**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
                                  Takes a source file and outputs the file in text format.
                                  The allowed formats are zip and TextRecordInputStream and Avro.
                                
        usage:hdsf dfs -text <src>
     
<br/>
<br/>


**[-usage &nbsp;&nbsp;[cmd]] :**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  Displays the usage for given command or all commands if none is specified.

          usage:hdfs dfs -usage <cmg>

	
	
	
