#  FILE COMPRESSION

## ZIP

Create a ZIP Archive:\
\
#zip files file1.txt file2.txt file3.txt file4.txt file5.txt

![](images/media/image1.png){width="5.761111111111111in"
height="1.2555555555555555in"}

![](images/media/image2.png){width="5.7625in"
height="3.573611111111111in"}

List ZIP File Contents:\
#zip -sf files.zip

![](images/media/image3.png){width="5.763888888888889in"
height="2.3006944444444444in"}

Add a Directory to ZIP Archive:\
#zip -r files \<directory\>

![](images/media/image4.png){width="5.761805555555555in"
height="0.2722222222222222in"}

![](images/media/image5.png){width="5.767361111111111in"
height="2.911111111111111in"}

Delete Files From ZIP Archive:

#zip -d \<archive file\> \<files for deletion\>

![](images/media/image6.png){width="5.767361111111111in"
height="2.247916666666667in"}

To unzip

#unzip test.zip

![](images/media/image7.png){width="5.764583333333333in"
height="0.2652777777777778in"}

![](images/media/image8.png){width="5.759722222222222in"
height="3.4451388888888888in"}

Explanation:\
The \'zip\' command creates compressed ZIP archives. Options:\
-r : Recursively include directories and subdirectories.\
-d : Delete specified files from an existing zip file.\
-sf : Show the list of files inside the archive.\
Example: \'zip -d files.zip file5.txt\' removes file5.txt from
files.zip.

## GZIP

Compressing Files:\
#gzip filename\
\
Compress multiple files:\
gzip file1 file2 file3 file4\
\
Keep the original file:\
#gzip -k filename

![](images/media/image9.png){width="5.4in"
height="0.6333333333333333in"}

![](images/media/image10.png){width="5.7659722222222225in"
height="0.475in"}

Verbose output:\
#gzip -v filename

![](images/media/image11.png){width="5.768055555555556in"
height="0.6361111111111111in"}

Compress all files in a directory:\
#gzip -r directory

![](images/media/image12.png){width="5.325in"
height="0.4666666666666667in"}

![](images/media/image13.png){width="5.7652777777777775in"
height="2.498611111111111in"}

Decompressing Files:\
#gzip -d filename.gz or gunzip filename.gz

![](images/media/image14.png){width="5.761111111111111in"
height="2.025in"}

![](images/media/image15.png){width="5.763888888888889in"
height="0.9958333333333333in"}

Decompress all files in a directory:\
#gzip -dr directory

![](images/media/image16.png){width="5.761805555555555in"
height="2.604861111111111in"}

Keep the compressed file:\
#gzip -dk filename.gz

![](images/media/image17.png){width="5.767361111111111in"
height="4.136111111111111in"}

![](images/media/image18.png){width="5.761111111111111in"
height="0.49236111111111114in"}

List the Compressed File Contents:\
#gzip -l filename

![](images/media/image19.png){width="5.763194444444444in"
height="0.6006944444444444in"}

#gzip -lv filename

![](images/media/image20.png){width="5.764583333333333in"
height="0.4166666666666667in"}

Explanation:\
The \'gzip\' command compresses files using the GNU zip algorithm.\
-k : Keep the original file.\
-v : Verbose, shows compression ratio.\
-d : Decompress.\
-r : Recursively compress directories.\
gzip works on individual files and replaces them with a .gz compressed
version unless -k is used.

## TAR

Create a tar Archive File in Linux:\
tar -cvf etc-backup-14-09-12.tar /etc\
c: create, v: verbose, f: file name.\
\
Create tar.gz Archive File:

#tar -cvzf etc-backup-14-09-12.tar.gz /etc

![](images/media/image21.png){width="5.763194444444444in"
height="4.752777777777778in"}

When you work with **tar** archives, you can compress or decompress them
using different algorithms.\
Two common compressors are:

• **gzip** → gunzip (tar.gz)

#tar -cvzf savefile.tar.gz filename

![](images/media/image22.png){width="5.763888888888889in"
height="3.202777777777778in"}

![](images/media/image23.png){width="5.763888888888889in"
height="0.48125in"}

• **bzip2** → bunzip(tar.bz2 or tbz)

#tar -cvjf savename.tbz filename

![](images/media/image24.png){width="5.761111111111111in"
height="4.417361111111111in"}

Untar tar Archive File:

#tar -xvf etc-backup.tar

![](images/media/image25.png){width="5.7659722222222225in"
height="0.69375in"}

![](images/media/image26.png){width="5.767361111111111in"
height="0.6951388888888889in"}

\# extract in diffrent directory

#tar -xvf etc-backup.tar -C /mnt \# extract to /mnt

![](images/media/image27.png){width="5.764583333333333in"
height="1.5763888888888888in"}

Untar Single or Multiple Files:\
#tar -xvf etc-backup.tar passwd group

![](images/media/image28.png){width="5.767361111111111in"
height="1.9194444444444445in"}

![](images/media/image29.png){width="5.7652777777777775in"
height="0.41805555555555557in"}

\# tar -xvf etc-backup.tar \"file1\" \"file2\"

![](images/media/image30.png){width="5.761111111111111in"
height="0.7201388888888889in"}

List Content of tar Archive:\
#tar -tvf backup.tar

![](images/media/image31.png){width="5.766666666666667in"
height="2.064583333333333in"}

Add Files or Directories to tar Archive:\
#tar -rvf backup.tar file1 file2

![](images/media/image32.png){width="5.766666666666667in"
height="2.1430555555555557in"}

Remove File or Directory from Tar Archive:\
#tar \--delete -f backup.tar file1.txt

![](images/media/image33.png){width="5.761805555555555in"
height="1.9631944444444445in"}

#tar \--delete -f backup.tar \'/home/tecmint/uploads\'\
\
Explanation:\
- tar -cvf : create tar archive.\
- tar -cvzf : create a compressed tar.gz archive.\
- tar -xvf : extract files.\
- tar -tvf : list contents.\
- tar -rvf : append files to archive.\
- tar \--delete : remove files or directories from a tar archive.\
Important: \'\--delete\' only works on uncompressed .tar files. For
.tar.gz or .tar.bz2, you must first decompress the file, delete the
entry, and recompress.
