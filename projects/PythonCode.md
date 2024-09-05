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
