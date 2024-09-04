---
layout: Store User and Password
type: project
image: img/cotton/cotton-square.png
title: "Store User and Password"
# All dates must be YYYY-MM-DD format!
date: 2022-05-6
published: true
labels:
  - Python
  - GitHub
summary: "I build a program that will use a text file as a database to store username and password."
---

<h2> Rules </h2>
<ul>
  <li> 
    Write a program that will read the data into a dictionary. The usernames will be used as keys to the dictionary. The    
    values will be the passwords. The passwords will follow the criteria from problem 6. The usernames are also guaranteed to 
    be unique.
  </li>
    <li> 
      Continue the program to prompt the user to sign up for your application or to change their password if they are already a user. The user should have the option to quit or exit the program at this point. To quit the user and enter 'q' or 'Q'. They can press 1 for sign up or 2 for changing their password.
    </li>
  <li>
    Prompt the user to ask if they want to sign up, if they want to change their password, or quit. If they want to change their password, they should enter a username. If the username doesn't exist, the program should state 'username doesn't exist' and return to asking if they want to sign up, change their password, or quit. If the username exists, then they should confirm their old password. If the old password was confirmed. Let them change their password by letting them enter a new one. Their new password should still follow the criteria in problem 6. If it doesn't fit the criteria, they must re-enter a new password until a suitable password is entered. If the user enters a suitable password, the program should display
'password changed' and go back to the menu asking if they want to sign up, change passwords, or quit. If the old password was not confirmed 3 times total, then the program should state that they entered the wrong password and the program should then go back to the menu asking if they want to sign up, change password, or quit.
  </li>
  <li>
    If they want to sign up, they should enter a username. If that username is taken, the program should let them know that the username is taken and they should try to use another one (usernames must be unique). The user should be allowed to enter usernames until an unused one is found. If they enter a username that is available then they are allowed to use that
username so they should pick a password New user's passwords should follow the criteria from problem 6. In addition, the
program should double check the user's password by asking them to confirm the
password they entered. If the password they enter for the confirmation is different the program will reset and ask for the user's new password and then ask for confirmation again. If the password is confirmed it should be added to the dictionary and also added to the file passwords.txt. If a user successfully signs up, the program should go back to the menu to sign
up, change password, or quit.
  </li>
  <li>
    If you exit the program it shouldn't matter since the data is in the file. When you restart the program, it should load all the user's into the dictionary you are using. Modify the program so that before the user is asked if they want to sign up or change their password, a print statement displaying how many users have signed up is shown right above that menu prompt. Any time that menu prompt is displayed, the correct number of users should be displayed. This is the total number of users in your passwords.txt file. This should be updated as user's sign up.
  </li>
</ul>

<h2> Code </h2>

<pre>
  <code>
    username = []
password = []
u = username.append(input('Enter a Username: '))
p = password.append(input('Enter a Paswword: '))

print('Press 1 to sign up')
print('Press 2 to change password')
print('Press Q or q to quit')
option = input()
while True:
    if option == '1':
        print('Enter a username')
        user = input()
        if user in username:
            print('Username is already taken. Enter a new username')
        else:
            username.append(user)
            print('Enter new password')
            pas = input()
            count = 0
            if count == 3:
                break
            else:
                if pas not in password:
                    count += 1
                else:
                    if pas in password:
                        pas = input('Enter New Password: ')
                        ct = 0
                        if count == 3:
                            break
                        else:
                            if pas not in password:
                                ct += 1
                            else:
                                if pas in password:
                                    pas = input('Enter New Password: ')
                                    c = 0
                                    k = 0
                                    keepgoing = True
                                    while keepgoing:
                                        for char in pas:
                                            if char == ' ' and char == '    ' and char == '=' and char == '?':
                                                print('Invalid Password, Please Enter a new password.')
                                                pas = input('Enter New Password: ')
                                                keepgoing == False
                                            elif char.isupper():
                                                c += 1
                                            elif c <= 1:
                                                print('Invalid Password, Please Enter a new password.')
                                                pas = input('Enter New Password: ')
                                                keepgoing == False
                                            elif char.isdigit():
                                                k += 1
                                            elif k <= 1:
                                                print('Invalid Password, Please Enter a new password.')
                                                pas = input('Enter New Password: ')
                                                keepgoing == False
                                            elif len(pas) < 8:
                                                print('Invalid Password, Please Enter a new password.')
                                                pas = input('Enter New Password: ')
                                                keepgoing == False
                                            else:
                                                print('Please re-enter your password')
                                                pas1 = input()
                                                if pas == pas1:
                                                    print('The password you entered is valid')
                                                    password.append(pas)  
                                                    keepgoing == False
                                                else:
                                                    print('Password entered not the same. Please reenter your password')
                                                    pas1 = input()
            
        

    elif option == '2':
        print('Enter username')
        user = input()
        if user not in username:
            print("Username doesn't exist")
            print('Press 1 to sign up')
            print('Press 2 to change password')
            option = input()
        else:
            print('Confirm old password')
            pas = input('Enter a Paswword: ')
            count = 0
            if count == 3:
                break
            else:
                if pas not in password:
                    count += 1
                else:
                    if pas in password:
                        pas = input('Enter New Password: ')
                        c = 0
                        k = 0
                        keepgoing = True
                        while keepgoing:
                            for char in pas:
                                if char == ' ' and char == '    ' and char == '=' and char == '?':
                                    print('Invalid Password, Please Enter a new password.')
                                    pas = input('Enter New Password: ')
                                    keepgoing == False
                                elif char.isupper():
                                    c += 1
                                elif c <= 1:
                                    print('Invalid Password, Please Enter a new password.')
                                    pas = input('Enter New Password: ')
                                    keepgoing == False
                                elif char.isdigit():
                                    k += 1
                                elif k <= 1:
                                    print('Invalid Password, Please Enter a new password.')
                                    pas = input('Enter New Password: ')
                                    keepgoing == False
                                elif len(pas) < 8:
                                    print('Invalid Password, Please Enter a new password.')
                                    pas = input('Enter New Password: ')
                                    keepgoing == False
                                else:                                    
                                    print('The password you entered is valid') 
                                    password.append(pas) 
                                    keepgoing == False
            
    elif option == 'q' or 'Q':
        break

    else:
        print('Press 1 to sign up')
        print('Press 2 to change password')
        print('Press Q or q to quit')
        option = input()
        break
  </code>
</pre>
<h2> :( I never got it to work </h2>
I'll finish it eventually though

