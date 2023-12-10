<h1> Vendor Management System</h1>

<h2>Project Setup<h2>

<-- Clone Project from github -->
1. Ensure python and postman are already installed on system.
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
    - open chorme and run url "http://127.0.0.1:8000/admin" and login with username and password as given, 3 tables will be created under "VENDORPROFILEMANAGEMENTAPP".


<h2>Testing API Urls using postman<h2>

<-- Create Token -->
1. Login to admin panel with given credential as mention perviously (Point 9).
2. Click on table name Tokens and create one token by clicking "ADD TOKEN".
3. Copy created token.

<-- Configure Postman -->
4. Under headers, create one field for token: {"Key": Authorization, "Value":token generated_token}

<-- Creating vendors Details API-->
5. Open postman and configure the url and body:
    - Method : POST
    - Url : http://localhost:8000/api/vendors/
    - Body(raw - JSON): {
                            "name": "BlueDart",
                            "contact_details":"1234567890",
                            "address":"Marathahalli, Bangalore"
                        }
    - Under headers create one field for token: {"Key": Authorization, "Value":token generated_token}

6. Repeat no 4 (changes only in Body section) to create another vendor details

<-- Creating purchase order API-->
7. Configure url and body. Copy the vendor_code generated previously for which order is to be made:
    - Method : POST
    - Url : http://localhost:8000/api/purchase_orders/
    - Body(raw - JSON): {
                            "vendor":"vednor_code",
                            "items":{
                                        "product":"charger"
                                    },
                            "quantity":2,
                            "delivery_date":"2023-12-7"
                        }
8. Repeat no 7 to create more purchase for same or different vendors.

<-- Acknowledge API -->
9. Acknowledge the PO by the vendor. Copy the po_number for order to be acknowledged.
    - Method : POST
    - Url : http://localhost:8000/api/purchase_orders/po_number/acknowledge/
    - It will return the response time in second.

<-- Metric performance API -->
Note: When order is created, status is in "pending" and then acknowedgment is done by the vendor, indicating that order is being processed. When the order is completed, status is changed to "completed" and all the required metric is calculated. Will also pass quality rating at the same time.

10. Change the status to "completed":
    - Method : PATCH
    - Url : http://localhost:8000/api/purchase_orders/po_number/
    - Body(raw - JSON): {
                            "status": "completed",
                            "quality_rating": 8.8
                        }
    - Metrix will be automatically generated in vendor table.

<-- Vendor Performance API -->
11. Check performance of each vendor. Get the vendor_code for which performance is need to be checked.
    - Method : PATCH
    - Url : http://localhost:8000/api/vendors/vendor_code/performance/
    - Output will be the performance metrix.





