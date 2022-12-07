/**
 * Program that masks page number and offset from an
 * unsigned 32-bit address.

   A memory reference appears as:
    |                     |        |
   31                   12 11      0
 */

#include <stdio.h>
#include <unistd.h>
#include <stdlib.h>

#define PAGE_NUMBER_MASK 0xFFFFF000 
#define OFFSET_MASK 0x00000FFF  
#define SHIFT 12

int main(int argc, char *argv[]) {

//error check for right # of arguments
	if(argc != 2){
		fprintf(stderr, "Usage: ./aout <virtual adress>\n");
		return -1;
	}

	int page_num, offset;
	unsigned int reference;

	reference = (unsigned int)atoi(argv[1]);
	printf("The address %d contains:\n",reference);

	//  mask the page number 
	//-------------[TO BE COMPLETED]-------------

	// get the digits in places 31-12, then shift over so rightmost digit in 1's place
	page_num = (reference & PAGE_NUMBER_MASK) >> SHIFT;
	//get the digits in places 11-0
	offset = (reference & OFFSET_MASK);


	printf("page number = %d\n",page_num);
	printf("offset = %d\n",offset);

	return 0;
}
