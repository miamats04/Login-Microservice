# Login-Microservice
For the microservice I created a virtual environment first, and installed:
pip install Flask
pip install Flask-SQLAlchemy
pip install Flask-CORS

For the testing program I also installed:
pip install requests Flask

To run the mircorservice run: python app.py

When the microservice is run, it will create a folder called instance with the users.db in it. 

Requesting Data From Microservice:
For both creating a new account and logging in a user, the microservice receives JSON data. This means that before sending the username and password to the microservice, it should be in JSON format. To refer to the microservice login route, http://localhost:5001/app/login should be used. To refer to the microservice user registration route, http://localhost:5001/app/register should be used. 

Example call: requests.post(http://localhost:5001/app/login, json=loginData)


Receiving Data from Microservice:
For creating a new account, the microservice will respond with a message and status that indicate whether or not the new account was successfully created. If creating the new account fails, the microservice will send the message "user already exists" and status 400 back to the main program. Similarly, if creating the account was successful, the microservice will send the message "User created successfully" with the status 201. For logging in, the microservice will also respond with a message and status to indicate whether or not the user entered valid information. If the username and password match, the microservice will send a message "Login successful" with status 200 to the main program. If the username and password are not valid, the microservice will send a message "Invalid username or password" with status 401 back to the main program. The status sent back to the main program can then be used to determine which messages to display to the user or where the user should be redirected.

Example call: 
response = requests.post(http://localhost:5001/app/login, json=loginData)
if response.status_code == 200: flash('Login successful!', 'success')

![Screenshot 2024-11-19 203455](https://github.com/user-attachments/assets/fc841fc5-f3e3-4615-96b9-fdffda3c1034)
