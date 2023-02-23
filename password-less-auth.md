# Linux Password Less Authentication:

### Procedure to connect to linux machine using SSH-KEYS (Procedure is based on xShell as SSH Client )

`Note :` Ensure you pay more attention while you do copy paste with keys

Video Ref `https://youtu.be/IdTUwLgUu5k`

1) Create the directory named batch49
```
 mkdir batch49
```

2) cd batch49 ( move to that folder )

3) Command to create a SSH Key Pair
``` 
ssh-keygen -f b49  ( -f is the file name to be generated)
```

4) Rename the b49 file to b49.pem ( Pem is the private key format file accepted by xSHELL )
```
mv b49 b49.pem
```

5) Open your xShell ---> Tools ---> USer Key manager ---> Import your b47.pem Key 
   On your AWS Cloud ---> EC2  --> KeyPairs ---> Import Your PublicKey b57.pub


6) Connect to linux machine

```
ssh centos@publicIPAddress
```