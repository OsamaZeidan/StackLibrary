#include <stdio.h>
#include <stdlib.h>

/*__________________________________________________________________________*/

typedef struct node
{
    int Data;
    struct node *Next;
} node;

/*__________________________________________________________________________*/

typedef node* Node;
typedef node* Stack;

/*__________________________________________________________________________*/

int IsEmptyStack(Stack stack);
Stack CreateStack();
void MakeEmptyStack(Stack stack);
void Pop(Stack stack);
int Top(Stack stack);
void Push(int x, Stack stack);
void DisposeStack(Stack stack);

/*__________________________________________________________________________*/


/*__________________________________________________________________________*/

int IsEmptyStack(Stack stack)
{
    return stack->Next == NULL;
} // end of IsEmptyStack()

/*__________________________________________________________________________*/

Stack CreateStack()
{
    Stack stack = malloc(sizeof(node));
    if (stack == NULL)
    {
        printf("Out Of Memory!");
    } // end if()
    else
    {
        stack->Next = NULL;
        MakeEmptyStack(stack);
        return stack;
    } // end esle
} // end of CreateStack()

/*__________________________________________________________________________*/

void MakeEmptyStack(Stack stack)
{
    if (stack == NULL)
    {
        printf("THE MEMORY IS OUT OF SPACE!");
    } // end of if()
    else
    {
        while (!IsEmptyStack(stack))
        {
            Pop(stack);
        } // end of while()
    }     // end of else
} // end of MakeEmptyStack()

/*__________________________________________________________________________*/

void Pop(Stack stack)
{
    Node temp = NULL;
    if (IsEmptyStack(stack))
    {
        printf("THE STACK IS EMPTY!");
    } // end of if()
    else
    {
        temp = stack->Next;
        stack->Next = stack->Next->Next;
        free(temp);
    } // end of else
} // end of Pop()

/*__________________________________________________________________________*/

int Top(Stack stack)
{
    if (IsEmptyStack(stack))
    {
        printf("THE STACK IS EMPTY!");
    } // end of if()
    else
    {
        return stack->Next->Data;
    } // end of else
} // end of Top()

/*__________________________________________________________________________*/

void Push(int x, Stack stack)
{
    Node tmp = malloc(sizeof(node));
    if (tmp == NULL)
    {
        printf("Out Of Memory!");
    } // end of if()
    else
    {
        tmp->Data = x;
        tmp->Next = stack->Next;
        stack->Next = tmp;
    } // end of else
} // end of Push()

/*__________________________________________________________________________*/

void DisposeStack(Stack stack)
{
    MakeEmptyStack(stack);
    free(stack);
} // end of DisposeStack()

/*__________________________________________________________________________*/
