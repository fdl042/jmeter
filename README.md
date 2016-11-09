# jmeter
jmeter test config to read multiple urls (Images) and assert the checksum and response code = 200. 

# how to generante the image file list and its MD5 checksum value.

 $>find images/2017 -type f -exec MD5 -r  "{}" + > 2017rewriteListTest.txt

> 2017rewriteListTest.txt // output file
images/2017               // path 
-type f                   // only list file (-type d means only directory)
-exec MD5                 // execture the MD5 genration.
-r                        // reverse the format. otherwise, it get output like: MD5 (README.md) = dcc4a004c723d31b051dd1aa065051c0
"{}" +                    // macro for -exec


sample content
895d676b57be42cedaf371b53eac4720 images/2017/configurator/packages/NV2/239x137_F02.jpg
18362238f1621b1efb6e864eba93bc11 images/2017/configurator/packages/NV2/239x137_F04.jpg
e485bf3e0429089465092f9c44e3fd46 images/2017/configurator/packages/NV2/239x137_H01.jpg

# Jmeter spec:

Match to the 2017rewrtieistTest.txt. Note Hash, PATH are just the variable names you defined. The order is important ! 
Jmeter is smart enough to match out to the real data in cvs file. I didn’t change anything for delimiter field. You can see space is between hash value and image path.


