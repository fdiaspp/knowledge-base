# S3 - Handling microfiles


### Multi-part Strategy
Concatenating small files though multi-part upload strategy. Basically, we need to create or check if there is a 5mb file on target bucket and, then, starting uploading another part of this file. 

Source of the discussion
https://stackoverflow.com/questions/32448416/amazon-s3-concatenate-small-files
