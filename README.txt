#include <stdio.h>

/* -- -settings --- */
/*stack*/       int stack[10];
/*rstack*/      void* rstack[20];
/*dict*/        static struct entry
                {
                    char name[20];
                    void* code[200];
                } dict[1000];

/* text buffer */ char input_buffer[1000];
/* code buffer */ void* code_buffer[100];

/* --- code --- */
#define NEXT \
            ip = np;\
            np += sizeof(void*);\
            goto *ip;

int main(void)
{
    int stack_ptr = 0;
    int rstack_ptr = 0;
    int dict_ptr = 0;

    void* ip; // Instruction Pointer
    void* np; // Next Pointer

    code_buffer[0] = &&docol;
    code_buffer[1] = &&bye;
    printf("pointer 1: %p\npointer 2: %p\n", &code_buffer[0], &code_buffer[1]);

    np = &code_buffer[0];

    NEXT

    return 0;

    docol:
        printf("ip:%p\nnp:%p\n\n", ip, np);\
        rstack[rstack_ptr++] = ip;
        np = ip + 2;
        printf("pointer 1: %p\npointer 2: %p\n\n", &code_buffer[0], &code_buffer[1]);
        NEXT

    bye:
        printf("ip:%p\nnp:%p\n\n", ip, np);\
        printf("byeeee o/");
        return 0;
};
