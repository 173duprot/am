#include <stdio.h>

/* -- -settings --- */
/*stack*/       int stack[10];
/*rstack*/      void* rstack[20];
/*dict*/        static struct entry
                {
                    char name[40];
                    void* code[200];
                } dict[1000];

/* text buffer */ char input_buffer[1000];
/* code buffer */ void* code_buffer[100];

/* --- code --- */
#define NEXT \
            ip = np;\
            np = np + sizeof(void*);\
            goto *ip;

int main(void)
{
    /*int stack_ptr = 0;
    int rstack_ptr = 0;
    int dict_ptr = 0;*/

    void* ip; // Instruction Pointer
    void* np; // Next Pointer

    code_buffer[0] = &&docol;
    code_buffer[1] = &&docol;
    code_buffer[2] = &&bye;

    np = &code_buffer[0];

    NEXT

    docol:
        printf("ip:%p\nnp:%p\n\n", ip, np);
        printf("pointer 1: %p\npointer 2: %p\n\n", &code_buffer[0], &code_buffer[1]);
        return 0;

    bye:
        printf("ip:%p\nnp:%p\n\n", ip, np);\
        printf("byeeee o/");
        return 0;
};
