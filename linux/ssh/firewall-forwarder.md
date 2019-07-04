
Local Listen
=======

```
ssh -f -N -T -L 123:localhost:456  bbb
```
- Local: 
  - Listen port 123
- Remote: 
  - Connect to localhost:456 (bbb view)
- SSH Server: 
  - bbb


Remote Listen
=======

```
ssh -f -N -T -R 123:localhost:456 bbb
```
- Local: 
  - Connect to localhost:456 (local view)
- Remote: 
  - Listen port 123
- SSH Server:
  - bbb

SSH Parameteres
=======
- -f: Background mode
- -N: No command
- -T: Server not generate pty
