# 2b IMPLEMENTATION OF SLIDING WINDOW PROTOCOL
## AIM
## ALGORITHM:
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM
           Client:
           import socket
           s=socket.socket()
           s.bind(("localhost",9000))
           s.listen(5)
           c,addr=s.accept()
           size=int(input("Enter the number of frames to send :"))
           l=list(range(size))
           s=int(input("Enter the Window Size : "))
           st=0
           i=0
           while (i<len(l)):
                st+=s
                c.send(str(l[i:st]).encode())
                ack=c.recv(1024).decode()
                if ack:
                 print(ack)
                 i+=s


        Server:
          import socket
          s=socket.socket()
          s.connect(("localhost",9000))
          while True:
              print(s.recv(1024).decode())
              s.send("acknowledgement received from the server".encode())


    
## OUPUT
![Screenshot 2025-03-29 103212](https://github.com/user-attachments/assets/b9048c2a-0432-4e59-baa0-6eca77e65018)
![Screenshot 2025-03-29 103304](https://github.com/user-attachments/assets/481be76d-71ad-4d82-bfa8-84eb7b6ba002)

## RESULT
Thus, python program to perform stop and wait protocol was successfully executed
