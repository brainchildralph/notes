
```
#include <stdio.h>
#include <termios.h>            //termios, TCSANOW, ECHO, ICANON
#include <unistd.h>             //STDIN_FILENO
#include <stdlib.h>

int main(void){
  char buf[BUFSIZ];
  char name[8]={0}, gender;
  static struct termios t;
#if 0
  tcgetattr(STDIN_FILENO, &t);
  printf("c_iflag=%x\n", t.c_iflag);
  printf("c_oflag=%x\n", t.c_oflag);
  printf("c_cflag=%x\n", t.c_cflag);
  printf("c_lflag=%x\n", t.c_lflag);
  printf("t.c_cc[VMIN]=%d\n", t.c_cc[VMIN]);
  printf("%s, %d: fileno(stdin): %d, STDIN_FILENO: %d\n", __FUNCTION__, __LINE__, fileno(stdin), STDIN_FILENO);
#endif
  printf("Hello, what's your name? \n");
  scanf("%s", name);
  setbuf(stdin,NULL);
  setbuf(stdin,buf);
  printf("And what's your gender? \n");
  gender=getchar();
  printf("name=%s, gender=%c.\n", name, gender);
  printf("buf: %c\n", buf[0]);
  return 0;
}
```
