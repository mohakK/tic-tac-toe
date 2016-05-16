# tic-tac-toe

import sys
board=[]
for x in range(3):
    board.append([])


for y in range(3):
    for z in range(3):
        board[y].append('.')


def bprint():
    for i in range(3):
        for j in range(3):
            sys.stdout.write(" %s |"%board[i][j])
        
        print "\n-------------"
    
def positions():
    board1=[]
    
    for x in range(3):
        board1.append([])
   

    board1[0].append('1')
    board1[0].append('2')
    board1[0].append('3')
    board1[1].append('4')
    board1[1].append('5')
    board1[1].append('6')
    
    board1[2].append('7')
    board1[2].append('8')
    board1[2].append('9')
    
    for i in range(3):
        for j in range(3):
            sys.stdout.write(" %s |"%board1[i][j])
        
        print "\n-------------"
   
def isempty(s):
    if s=='.':
        return 1
    else :
        return 0    

def play(p,c,x):
    if p==1:
        if isempty(board[0][0]):
            board[0][0]=c
    elif p==2 :
        if isempty(board[0][1]):
            board[0][1]=c     
    elif p==3 :
        if isempty(board[0][2]):
            board[0][2]=c
    elif p==4:
        if isempty(board[1][0]):
            board[1][0]=c
    elif p==5 :
        if isempty(board[1][1]):
            board[1][1]=c
    elif p==6 :
        if isempty(board[1][2]):
            board[1][2]=c
    elif p==7 :
        if isempty(board[2][0]):
            board[2][0]=c
    elif p==8 :
        if isempty(board[2][1]):
            board[2][1]=c
    elif p==9 :
        if isempty(board[2][2]):
            board[2][2]=c
   
def win():
    if board[0][0]==board[0][1] and board[0][0]!='.' and board[0][1]==board[0][2] or board[0][2]==board[1][2] and board[0][2]!='.' and board[1][2]==board[2][2] or board[2][2]==board[2][1] and board[2][1]!='.' and board[2][1]==board[2][0] or board[2][0]!='.' and board[2][0]==board[1][0] and board[1][0]==board[0][0] or board[0][0]==board[1][1] and board[0][0]!='.' and board[1][1]==board[2][2] or board[0][2]==board[1][1] and board[1][1]!='.' and board[1][1]==board[2][0]:
        return 1
    elif board[0][1]==board[1][1] and board[1][1]==board[2][1] and board[1][1]!='.' or board[1][0]==board[1][1] and board[1][1]==board[2][1] and board[1][1]!='.':
        return 1    
    else:
        return 0    
               
def emptycheck():
    p=0
    for i in range(3):
        for j in range(3):
            if board[i][j]=='.':
                p=1   
    return p     

def game():
   print "Player1: o\nPlayer2: x"
   
   a=1
   while a>0 and emptycheck():
       print"\n----------------------------"
       print "Enter 195 to Exit \n----------------------------\n"
       if a%2==0:
           print "Player2's Turn"
       else:
           print "Player1's Turn"    
       print "CURRENT BOARD: "
       bprint()
       print "\n"
       positions()
       p=input( "Enter Position To Move: ")
       if p==195:
           break
       elif p>9 or p<1:
           print "Invalid Position" 
       else:
          if a%2==0:
              play(p,'x',2)
          else:
              play(p,'o',1)
       if win():
           bprint()
           print "You win!!"
           break    
       a=a+1            

   
game()                                     
