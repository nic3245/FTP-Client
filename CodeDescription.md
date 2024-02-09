High-level approach: 
First, the program sets up its arguments with the parser library, then it parses these arguments.
Next, using these arguments, it sets up the socket, connects, and receives the hello message.
After that, it attempts to log in with the provided username and password, and if successfull, it changes the settings of the connection.
Then, the operation is attempted. All of the individual required ftp commands were implemented, and these were used to build the overall five operations offered to the user. If the operation is successfull, messages are printed to the command line.
Finally, the connection is closed.
Challenges I faced:
One challenge I faced was how the data channel protocol worked. First, I was struggling to keep the connection open, as every time I tried to use it I was getting errors it was closed. After realizing I was opening the socket wrong, I then had to figure out where to send messages and receive messages from. After some trial and error, I figured out that the commands are sent through the communcation socket, and then once the communication socket responds that it is ready, then the data is sent over the data socket. I also forgot to close the data socket when I done sending, which caused some issues until I fixed the problem.
Testing Overview:
Much of my testing was done by printing out the server responses and then checking on FileZilla. For example, for deleting a file from the server, I would transfer a test file through FileZilla, attempt to delete it, print out the message the server sent, then refresh FileZilla to make sure the file was gone. This process was repeated for every applicable ftp command as well as every client application command.