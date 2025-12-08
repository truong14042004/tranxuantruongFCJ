---
title: "Blog 3"
date: 2025-09-30
weight: 1
chapter: false
pre: " <b> 3.3. </b> "
---



# Automating audio editing and transcoding using AWS

by Todd Leishman | on 29 MAY 2025 | in [Amazon EC2](https://aws.amazon.com/blogs/media/category/compute/amazon-ec2/), [Amazon Elastic Transcoder](https://aws.amazon.com/blogs/media/category/application-services/amazon-elastic-transcoder/), [Amazon Simple Notification Service (SNS)](https://aws.amazon.com/blogs/media/category/messaging/amazon-simple-notification-service-sns/), [Amazon Simple Queue Service (SQS)](https://aws.amazon.com/blogs/media/category/messaging/amazon-simple-queue-service-sqs/), [Application Services](https://aws.amazon.com/blogs/media/category/application-services/), [AWS Batch](https://aws.amazon.com/blogs/media/category/compute/aws-batch/), [AWS Elemental MediaConvert](https://aws.amazon.com/blogs/media/category/media-services/aws-elemental-mediaconvert/), [AWS Fargate](https://aws.amazon.com/blogs/media/category/compute/aws-fargate/), [AWS Lambda](https://aws.amazon.com/blogs/media/category/compute/aws-lambda/), [Compute](https://aws.amazon.com/blogs/media/category/compute/), [Content Production](https://aws.amazon.com/blogs/media/category/industries/entertainment/content-production/), [Industries](https://aws.amazon.com/blogs/media/category/industries/), [Media & Entertainment](https://aws.amazon.com/blogs/media/category/industries/entertainment/), [Media Services](https://aws.amazon.com/blogs/media/category/media-services/), [Messaging](https://aws.amazon.com/blogs/media/category/messaging/) [Permalink](https://aws.amazon.com/blogs/media/automating-audio-editing-and-transcoding-using-aws/)

Audio editing and transcoding are crucial processes for content creators, broadcasters, and media professionals who need to convert audio files from one format to another and automate basic audio editing tasks. With [Amazon Elastic Transcoder](https://aws.amazon.com/blogs/media/support-for-amazon-elastic-transcoder-ending-soon/) scheduled for deprecation, in November, 2025, it is important to understand the alternatives for implementing audio-only workflows in Amazon Web Services (AWS).

Audio processing workflows present unique challenges, as most available tools are designed specifically for video, with audio often being an afterthought.

A common audio-only workflow can involve selecting a short segment from a full music file (Figure 1), clipping that segment (Figure 2), and applying fade-in and fade-out effects to create smooth transitions (Figure 3).

![Selecting a short segment from a full music file](https://d2908q01vomqb2.cloudfront.net/fb644351560d8296fe6da332236b1f8d61b2828a/2025/05/20/AE-Image-1.png)
*Figure 1: Selecting a short segment.*

![The clipped audio segment](https://d2908q01vomqb2.cloudfront.net/fb644351560d8296fe6da332236b1f8d61b2828a/2025/05/20/AE-Image-2.png)
*Figure 2: The clipped audio segment.*

![Addition of fading in and out audio segments](https://d2908q01vomqb2.cloudfront.net/fb644351560d8296fe6da332236b1f8d61b2828a/2025/05/20/AE-Image-3.png)
*Figure 3: Addition of fading in and out audio segments.*

This workflow can be automated to save time and effort, allowing audio engineers to focus on complex mixing and editing projects.

## Audio processing using FFmpeg, Python, Amazon EC2, and Amazon S3

To get started, you will leverage Amazon Elastic Compute Cloud ([Amazon EC2](https://aws.amazon.com/ec2/?nc2=type_a)), Amazon Simple Storage Service ([Amazon S3](https://aws.amazon.com/s3/)) and the open-source tools [FFmpeg](https://www.ffmpeg.org/) and [Python](https://www.python.org/). This solution will lay the groundwork for streamlined, more efficient methods using [AWS Lambda](https://aws.amazon.com/lambda/?nc2=type_a) and [AWS Elemental MediaConvert](https://aws.amazon.com/mediaconvert/?nc2=type_a).

### S3 bucket configuration

1. [Create a new S3 bucket](https://docs.aws.amazon.com/AmazonS3/latest/userguide/create-bucket-overview.html)* with two prefixes (folders), one for original files and one for converted files. For example:
    * https://s3.us-west-2.amazonaws.com/audiobucket/original/
    * https://s3.us-west-2.amazonaws.com/audiobucket/converted/

    *Ensure that your bucket name is unique

2. [Setup IAM roles and policies](https://docs.aws.amazon.com/AmazonS3/latest/userguide/security_iam_service-with-iam.html) for accessing the new S3 bucket
3. Upload your original .flac or .wav audio files to the original files prefix (folder) [using the AWS Management Console](https://docs.aws.amazon.com/AmazonS3/latest/userguide/upload-objects.html) (the console)

### EC2 instance configuration

1. [Launch a Linux t3a.medium EC2 instance](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/LaunchingAndUsingInstances.html) or similar (for our following example solution we will be using [Amazon Linux 2](https://aws.amazon.com/amazon-linux-2/?amazon-linux-whats-new.sort-by=item.additionalFields.postDateTime&amazon-linux-whats-new.sort-order=desc))
2. [Connect to the new instance](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/connect.html) by using Secure Shell (SSH) or the console
3. Install FFmpeg on the EC2 instance by running the following commands in the terminal:

```bash
$ sudo su
# cd /usr/local/bin
# mkdir ffmpeg 
# cd ffmpeg
# wget https://johnvansickle.com/ffmpeg/releases/ffmpeg-release-amd64-static.tar.xz
# tar -xf ffmpeg-release-amd64-static.tar.xz
# cd ffmpeg-7.0.2-amd64-static/
# cp -a ffmpeg /usr/bin/
# cp -a ffprobe /usr/bin/
# cp -a qt-faststart /usr/bin/
# cd /usr/bin 
# ffmpeg -version
```

The `ffmpeg -version` command should return a result similar to this:
`ffmpeg version 7.0.2-static https://johnvansickle.com/ffmpeg/ ...`

4. Install the AWS Command Line Interface ([AWS CLI](https://aws.amazon.com/cli/?nc2=type_a)) on your EC2 instance (if not using Amazon Linux)
    1. [How to install AWS CLI on Linux](https://www.cyberciti.biz/faq/how-to-install-aws-cli-on-linux/)
5. Install Python on your EC2 instance (if not using Amazon Linux)
    1. [Install Python on Rocky Linux](https://phoenixnap.com/kb/rocky-linux-python)
6. Install [Mountpoint](https://docs.aws.amazon.com/AmazonS3/latest/userguide/mountpoint.html) for Amazon S3 on your EC2 instance (or use the S3 Sync API if preferred)
    1. [Installing Mountpoint](https://docs.aws.amazon.com/AmazonS3/latest/userguide/mountpoint-installation.html)
    2. [video: How To Mount An Amazon S3 Bucket As A Local Drive  Step-by-Step guide](https://www.youtube.com/watch?v=RNOxlcaAMpg)
    3. [Mountpoint credentials configuration options](https://github.com/awslabs/mountpoint-s3/blob/main/doc/CONFIGURATION.md#aws-credentials)
    4. Mount your S3 bucket using S3 Mountpoint
    ```bash
    # mount-s3 audiobucket /mnt/audiobucket
    ```
7. Make sure you can see the files you uploaded to the S3 bucket `/audiobucket/original/` directly on the EC2 instance through the terminal:
    ```bash
    # cd /mnt/audiobucket/original
    # ls -lah
    ```

### Environment Testing

Now that your AWS environment is prepared, go ahead and test the solution by converting an original FLAC file to an AAC file, while simultaneously clipping and fading the audio in and out.

1. Test the conversion of a single file located in S3 using a BASH FFmpeg command and Mountpoint for Amazon S3.

```bash
ffmpeg -i /mnt/audiobucket/original/audiofile-01.flac -ss 00:00:03.000 -to 00:00:15.000 -vn -c:a libfdk_aac -af afade=in:st=3:d=2,afade=out:st=10:d=4 /mnt/audiobucket/converted/audiofile-01.aac
```

This FFmpeg command assumes the file is longer than 15 seconds and it includes the following options:

* -i = input file (audiofile-01.flac)
* -ss = clip start time (3 seconds)
* -to = end clip time (15 seconds)
* -vn = video no (audio-only file)
* -c:a = selects audio encoder (use the libfdk aac encoder)
* -af = audio filter (add a filter to the audio file (fade in this case))
* afade=in = apply the fade in (fade audio in)
* st = fade in start time (start the fade in at 3 seconds)
* d = fade in duration (fade the audio in for 2 seconds)
* afade=out = apply the fade out (fade audio out)
* st = fade out start time (start the fade out at 10 seconds)
* d = fade out duration (fade the audio out for 4 seconds)

Your newly converted file will be saved to your S3 buckets `/converted/` prefix (folder). Open the file to verify that fading, clipping and transcoding occurred.

### Python scripting for more control

For more advanced automation, you can use Python with the subprocess module to call FFmpeg, which will complete the edit and conversion. This will give us more control of our audio workflow, including adding a variety of audio formats. You can also check to see if a file has already been converted before proceeding with a new conversion workflow.

There are several ways to create the script. Following you will find a basic example, which can be altered for each use case. This Python script is based on the BASH command you tested previously, and will convert .wav or FLAC files to AAC format files, while trimming and fading the files. This script will convert all files located in the original folder used previously, unless a converted version already exists in the converted folder. For production use, it is recommended to enhance the Python script by adding input validation, error handling for unexpected files, and additional logging for success, failure or errors.

Create the new python script on the EC2 instance using Vim or your preferred editor. In this case, you will name the script `convert_audio.py`.

```bash
$ sudo vi convert_audio.py
```

Paste the following script into the new document:

```python
import subprocess
import os
import glob
import sys

def convert_audio_files(original_dir, converted_dir):
    if not os.path.exists(converted_dir):
        os.makedirs(converted_dir)

    supported_formats = (''.flac'', ''.wav'')
    for file_extension in supported_formats:
        for input_file in glob.glob(os.path.join(original_dir, ''*'' + file_extension)):
            file_name = os.path.basename(input_file)
            output_file = os.path.join(converted_dir, os.path.splitext(file_name)[0] + ''.aac'')
            
            if os.path.exists(output_file):
                print(f"Skipping {file_name} as it already exists in the converted directory.")
                continue

            command = [
                "ffmpeg",
                "-i", input_file,
                "-ss", "00:00:03.000",
                "-to", "00:00:15.000",
                "-vn",
                "-c:a", "libfdk_aac",
                "-af", "afade=in:st=3:d=2,afade=out:st=10:d=4",
                output_file
            ]
            subprocess.run(command)

if __name__ == ''__main__'':
    if len(sys.argv) != 3:
        print("Usage: python script.py <original_directory> <converted_directory>")
        sys.exit(1)

    original_directory = sys.argv[1]
    converted_directory = sys.argv[2]

    convert_audio_files(original_directory, converted_directory)
```

Save and close your editor.

Initiate the script, `convert_audio.py`, by including the input and output folders within the command:

```bash
$ sudo python3 convert_audio.py /mnt/audiobucket/original /mnt/audiobucket/converted
```

### Simple automation setup

Now that you have tested the conversion script manually, you can setup your EC2 instance to automatically run the script every 10 minutes. As new files are added to the original folder, this simple automation will pick up those new files and run the conversion every 10 minutes. The python script verifies that only new files are converted.

To make the cron job run every 10 minutes daily, set the minute field to a step value of 10. Heres how to modify the cron job:

1. Go to the EC2 instance terminal
2. Type `crontab -e` and press Enter to open the crontab file
Add the following line to the crontab file, replacing `/path/to/convert_audio.py` with the actual path to your Python script (the cron job fields represent minutes, hours, day of the month, month, and day of the week, respectively):

```bash
*/10 * * * * /usr/bin/python3 /path/to/convert_audio.py /mnt/audiobucket/original /mnt/audiobucket/converted
```

3. Save the cron job changes and exit the editorthe cron job will now run your Python script every 10 minutes, every day.

## Summary

Audio processing workflows present unique challenges, as most available tools are designed specifically for video, with audio often being an afterthought. With [Amazon Elastic Transcoder](https://aws.amazon.com/blogs/media/support-for-amazon-elastic-transcoder-ending-soon/) scheduled for deprecation, it is important to understand the alternatives for implementing audio-only workflows using AWS services.

This blog is the first in a three-part series that explored basic automated audio conversion using AWS services and open-source tools.

In the next blog, we will streamline the workflow by utilizing AWS Lambda to create a serverless audio conversion service.

Contact an [AWS Representative](https://pages.awscloud.com/Media-and-Entertainment-Contact-Us.html) to know how we can help accelerate your business.

### Further reading

* [Transcoding with FFmpeg on AWS Graviton Processors](https://aws.amazon.com/blogs/opensource/optimized-video-encoding-with-ffmpeg-on-aws-graviton-processors/)
* [Installing FFmpeg on AWS Graviton Instances](https://arthurpello.medium.com/how-to-install-ffmpeg-on-aws-arm-amazon-linux-2023-graviton-c4bc092260bf)

![Todd Leishman](https://d2908q01vomqb2.cloudfront.net/fb644351560d8296fe6da332236b1f8d61b2828a/2025/05/22/Todd-Leishman.jpg)

### Todd Leishman

Todd Leishman has worked in the Media & Entertainment industry for over 25 years, focusing on audio engineering, live event streaming, and media asset management. As an audiophile, Todd is always looking for new ways to improve audio technologies and techniques using cloud-based solutions.
