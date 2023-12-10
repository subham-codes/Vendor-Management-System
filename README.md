<h1> Vendor Management System</h1>

<h2>Project Setup<h2>


<-- Clone Project from github -->
1. Ensure python is already installed on system.
2. Open VSCode to any project folder as desired.
3. Clone the project from github --> git clone "https://github.com/subham-codes/VendorManagementSystem.git"
4. Open VScode again under folder 'VendorManagementSystem'

<-- Installing requirements -->
5. Create virtual environment and activate it. 
6. Install all the requirements --> "pip install -r requirements.txt"

<-- setting up DB -->
7. Run following commands to create DB tables:
    - python manage.py makemigrations
    - python manage.py migrate

8. Create superuser for admin login:
    - python manage.py createsuperuser
    * enter username and password

9. To verify whether tables are being created successfully:
    - python manage.py runserver
    - open chorme and run url "http://127.0.0.1:8000/" - 3 tables will be created.





