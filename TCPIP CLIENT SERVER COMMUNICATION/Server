#include<stdio.h>
#include<sys/types.h> 
#include<sys/socket.h> 
#include<netinet/in.h> 
#include<netdb.h> 
#include<arpa/inet.h> 
#include<string.h> 
int main(int asrgc,char*argv[]) 
{ 
	int b,s,a; 
	char buff[1024]; 
	struct sockaddr_in cliaddr,servaddr; 
	socklen_t clilen; 
	clilen=sizeof(cliaddr); 
	bzero(&servaddr,sizeof(servaddr)); 

	           
	servaddr.sin_family=AF_INET; 
	servaddr.sin_addr.s_addr=htonl(INADDR_ANY); 
	servaddr.sin_port=htons(2000);
	s=socket(AF_INET,SOCK_STREAM,0); 

	          
	b=bind(s,(struct sockaddr*)&servaddr,sizeof(servaddr)); 

	listen(s,5); 
	printf("Server is running….\n");
	 
	a=accept(s,(struct sockaddr*)&cliaddr,&clilen); 
	while(1) 
	{ 
		bzero(&buff,sizeof(buff)); 
		    recv(a,buff,sizeof(buff),0); 
		        printf("%s\n",buff); 
	} 
}
