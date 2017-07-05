# Project_smart_gateway
#include<stdio.h>
#include<fcntl.h>
#include<string.h>
#defin MAx_length 20
int read_temprature(int);
int main()
{
int val; 
val =read_temprature(0);
printf("current temperature at your place %d\n",val);

}



}
int read_temprature(int pin)
{
int fd;
char val[4];
char buff[MAX_length];
snprintf(buff,sizeof(buff),"/sys/bus/iio/devices/iio:device0/in_voltage%d_raw", pin);
fd=open(buff,O_RDONLY);
if(fd<0)
{
printf("unable to open the ADC\n");
return 0;
}
read(fd,&val,4);
close(fd);
return atoi(val);
}
