#include<stdio.h> 
#include<string.h> 
#include<sys/socket.h> 
#include<sys/types.h> 
#include<unistd.h> 
#include<netinet/in.h> 
#include<netdb.h> 
#include<arpa/inet.h> 
int main(int argc,char * argv[]) 
{ 
	int c,s,a; 
	char buff[1024]; 
	struct sockaddr_in cliaddr,servaddr; 
	struct hostent *h; 
		 
	h=gethostbyname(argv[1]); 
	bzero(&servaddr,sizeof(servaddr));
	servaddr.sin_family=AF_INET; 
	memcpy((char *)&servaddr.sin_addr.s_addr,h->h_addr_list[0],h->h_length); 
	servaddr.sin_port = htons(2000); 
	s = socket(AF_INET,SOCK_STREAM,0); 
	c=connect(s,(struct sockaddr*)&servaddr,sizeof(servaddr)); 

	while(1) 
	{ printf("Enter the message: "); 

		   
		 
		 fgets(buff,100,stdin); 
		 send(s,buff,sizeof(buff)+1,0); 
		 printf("Data Sent: "); 
		 printf("%s",buff); 
	} }
