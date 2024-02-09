# FTP-Client
File Transfer Protocol in Python

usage: make 3700ftp
usage: ./3700ftp [-h] [--verbose] [operation] [params ...]

FTP client for listing, copying, moving, and deleting files and directories on remote FTP servers.

positional arguments:
operation      The operation to execute. Valid operations are 'ls', 'rm', 'rmdir',
              'mkdir', 'cp', and 'mv'
params         Parameters for the given operation. Will be one or two paths and/or URLs.

optional arguments:
-h, --help     show this help message and exit
--verbose, -v  Print all messages to and from the FTP server

# Available Operations

This FTP client supports the following operations:

ls <URL>                 Print out the directory listing from the FTP server at the given URL
mkdir <URL>              Create a new directory on the FTP server at the given URL
rm <URL>                 Delete the file on the FTP server at the given URL
rmdir <URL>              Delete the directory on the FTP server at the given URL
cp <ARG1> <ARG2>         Copy the file given by ARG1 to the file given by
                          ARG2. If ARG1 is a local file, then ARG2 must be a URL, and vice-versa.
mv <ARG1> <ARG2>         Move the file given by ARG1 to the file given by
                          ARG2. If ARG1 is a local file, then ARG2 must be a URL, and vice-versa.

# URL Format and Defaults

Remote files and directories should be specified in the following URL format:

ftp://[USER[:PASSWORD]@]HOST[:PORT]/PATH

Where USER and PASSWORD are the username and password to access the FTP server,
HOST is the domain name or IP address of the FTP server, PORT is the remote port
for the FTP server, and PATH is the path to a file or directory.

HOST and PATH are the minimum required fields in the URL, all other fields are optional.
The default USER is 'anonymous' with no PASSWORD. The default PORT is 21.

# Example Usage

List the files in the FTP server's root directory:

$ ./3700ftp ls ftp://bob:s3cr3t@ftp.example.com/

List the files in a specific directory on the FTP server:

$ ./3700ftp ls ftp://bob:s3cr3t@ftp.example.com/documents/homeworks

Delete a file on the FTP server:

$ ./3700ftp rm ftp://bob:s3cr3t@ftp.example.com/documents/homeworks/homework1.docx

Delete a directory on the FTP server:

$ ./3700ftp rmdir ftp://bob:s3cr3t@ftp.example.com/documents/homeworks

Make a remote directory:

$ ./3700ftp mkdir ftp://bob:s3cr3t@ftp.example.com/documents/homeworks-v2

Copy a file from the local machine to the FTP server:

$ ./3700ftp cp other-hw/essay.pdf ftp://bob:s3cr3t@ftp.example.com/documents/homeworks-v2/essay.pdf

Copy a file from the FTP server to the local machine:

$ ./3700ftp cp ftp://bob:s3cr3t@ftp.example.com/documents/todo-list.txt other-hw/todo-list.txt
