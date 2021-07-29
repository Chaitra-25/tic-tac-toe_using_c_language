# tic-tac-toe_using_c_language
#include<stdio.h>
int main()
{
int winner=0, count=0;
int pos[9], index, sign, player, flag, i, k, j; // i=column, j=diagonal, k=row

for(i=0;i<9;i++)
{
pos[1]=' ';
}

while(count<9 && winner!=1)
{
flag=0;
// print board
printf("\n"); // creates a new line
printf("%c %c %c\n", pos[0], pos[1], pos[2]);
printf("-+-+-\n");
printf("%c %c %c\n", pos[3], pos[4], pos[5]);
printf("-+-+-\n");
printf("%c %c %c\n", pos[6], pos[7], pos[8]);

if(count%2==0)
{
sign='x';
player=1;
}
else
{
sign='o';
player=2;
}
printf("move for player %d(1-9):",player);
scanf("%d",&index);

if(index<1 || index>9)
{
printf("allowed index is 1 to 9\n");
continue;
}

if(pos[index-1]=='x' || pos[index-1]=='o')
{
printf("position is occupied\n");
continue;
}
pos[index-1]=sign;
count++;
for(i=0;i<9;i++)
{
if(i%3==0)
{
flag=0;
}
if(pos[i]==sign)
{
flag++;
}

if(flag==3)
{
winner=1;
win(player, winner, pos);
}
}

flag=0;
for(i=0;i<3;i++)
{
for(k=i;k<=i+6;k+=3)
{
if(pos[k]==sign)
flag++; // when it becomes 3 the current player has won the game
}
if(flag==3)
{
winner=1;
win(player,winner,pos);
}
}

flag=0;
if((pos[0]==sign)&&(pos[4]==sign)&&(pos[8]==sign))||((pos[2]==sign)&&(pos[4]==sign)&&pos[8]==sign))
{
winner=1;
win(player,winner,pos);
}
}
}

void win(int player, int winner, int pos[])
{
printf("\n");
printf("%c %c %c\n",pos[0],pos[1],pos[2]);
printf("-+-+-\n");
printf("%c %c %c\n",pos[3],pos[4],pos[5]);
printf("-+-+-\n");
printf("%c %c %c\n", pos[6],pos[7],pos[8]);

if(winner)
{
printf("player %d is the winner \n",player);
}
else
{
printf("match draw\n");
}
}

