# shellscripting
Task: Recently I got a task for deleting old un-used AMIs from our AWS account. The total count is around 1500+ after validation. If I delete them manually then definitely it will take more than 5–8 hours. And one more thing is, we have to delete the snapshots again after deregistering the AMIs.

So I have decided to create a shell script (of course, we can use other languages too like Python with boto3 library). The first thing I have checked is the AWS CLI documentation about the AMI deregistration. But the problem is, we need to delete the respective snapshots as well after deregistering the AMI. Hence we need to get the list of snapshots associated with these AMIs so that we can delete them as well using AWS CLI.

Our script needs to be like this

Read the AMI ids line by line from a file
Get the list of snapshots that are associated with this AMI
Deregister the AMI
Delete the snapshots which we got from step 2
Repeat steps 2,3 and 4 respectively
