# S3 CLI Commands

Following examples used **aws s3** command.

## Lisiting All Buckets

```bash
aws s3 ls
```

## Listing all files from bucket

```bash
aws s3 ls <bucket-url> --recursive
```

## Removing all files from bucket

```bash
aws s3 rm <s3-bucket-url> --recursive
```

## Upload a file to a bucket

```bash
aws s3 mv <local-file-url> <s3-bucket-url>
```

## Delete a file from bucket

```bash
aws s3 rm <bucket-object-url>
```

## Delete the bucket

For bucket to be deleted it has to be emptied first.

```bash
aws s3 rb <s3-bucket-url>
```

For force deleting a bucket by first deleting all the objects from the object and then removing a bucket use _--force_ flag.

```bash
aws s3 rb <s3-bucket-url> --force
```

## Create a new bucket

```bash
aws s3 mb <s3-bucket-url>
```

**Following examples use aws s3api command whose output is in json format:**

```bash
#Creates bucket with default region specified in environment variable
aws s3api create-bucket --bucket <bucket-name>

#Creating bucket in specified region
aws s3api create-bucket --bucket <bucket-name> --region <region-name>

#Listing all the buckets
aws s3api list-buckets

#For filtering we use --query flag

#Only displays the name of buckets
aws s3api list-buckets --query Buckets[].name

#Search bucket with specified name
aws s3api list-buckets --query "Buckets[?Name=='<bucket-name>'].Name"
```
