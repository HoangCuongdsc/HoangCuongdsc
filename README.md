- 👋 Hi, I’m @HoangCuongdsc
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...

<!---
HoangCuongdsc/HoangCuongdsc is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
import numpy as np

poker_of_you= 0
list_card_of_you= []
list_card_of_com = []
poker_of_computer=0
card= [1, 1, 1, 1, 2, 2, 2, 2, 3, 3, 3, 3, 4, 4, 4, 4, 5, 5, 5, 5, 6, 6, 6, 6, 7, 7, 7, 7, 8, 8, 8, 8, 9, 9, 9, 9, 10, 10, 10, 10, 10, 10, 10, 10,10, 10, 10, 10,10, 10, 10, 10]
card_= []
def remo(x,num):
    if len(num) == 1:
        x.remove(num[0])
    if len(num) > 1:
        for a in num:
            x.remove(a)
    return x
for _ in range(2):
    x= int(np.random.choice(card, replace=False))
    list_card_of_you.append(x)
    card= remo(card,[x])
    if x ==1 : 
        x = 10 
    poker_of_you += x
    a = int(np.random.choice(card,replace=False))
    list_card_of_com.append(a)
    card= remo(card,[a])
    if a ==1 : 
        a = 10 
    poker_of_computer += a
print('you_card:',list_card_of_you, '\n' ,'poker_of_you: ', poker_of_you,'\n','com_card:',list_card_of_com,'\n', 'poker_of_computer: ', poker_of_computer )
print("Do you want to continue: Y/ N")
Ans= input()
if Ans == 'Y':
    R_C= np.random.choice(card)
    list_card_of_you.append(R_C)
    card= remo(card,[R_C])
    poker_of_you += R_C
    print('you_card:', list_card_of_you)
    if poker_of_you > 21 and 1 in list_card_of_you:
        poker_of_you -=10
        print(' poker_of_you: ',poker_of_you)
        print('You loss')
    if poker_of_you < 21:
        print(' poker_of_you: ',poker_of_you)
        print("Do you want to continue: Y/ N")
        Ans= input()
        if Ans == 'Y':
            R_C_2= np.random.choice(card)
            list_card_of_you.append(R_C_2)
            card= remo(card,[R_C_2])
            poker_of_you += R_C_2
            if poker_of_you > 21:
                print('You loss')
            if poker_of_you < 21:
                print(' poker_of_you: ',poker_of_you)
                print("Do you want to continue: Y/ N")
                Ans= input()
                if Ans == 'Y':
                    R_C_3= np.random.choice(card)
                    list_card_of_you.append(R_C_3)
                    card= remo(card,[R_C_3])
                    poker_of_you += R_C_3
print(' poker_of_you: ', poker_of_you)
list_10= np.random.choice(card, 10, replace=False)
if poker_of_computer > poker_of_you and poker_of_computer <= 21:
    print(poker_of_computer,'\n', list_card_of_com)
    print('you loss')
    if poker_of_computer < poker_of_you:
        for i in list_10:
            poker_of_computer += i
            if poker_of_computer > 21:
                poker_of_computer -=i
            if poker_of_computer < 21 :
                list_card_of_com.append(i)
print('poker_of_computer:', poker_of_computer) 
if poker_of_you > poker_of_computer and poker_of_you <= 21:
    print('You Win')
elif poker_of_you == poker_of_computer:
    print('Draw')
else:
    print('You loss')
