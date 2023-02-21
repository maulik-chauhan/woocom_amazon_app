# woocom_amazon_app
Overview

This app will provide facility to its user by calling APIs of WooCommerce and Amazon SP-API and help user map and update based on the SKUs which is common parameter with both the platform mainly this application will work on FBA orders but it has a facility to manually map Non-FBA orders as per users input. 

Note: All the libraries which are used in this project will be kept inside a virtual environment for deployment convenience.

‘setup.py’  will be executed every time to make sure the virtual environment is activated and the main.py file is then executed for the execution of the app.

Specification of the Application

This application mainly consists of following functions which will provide all the service to the user.

Authentication function for Amazon SP-API( auth_amazon() ) : This function will provide authentication for Amazon APIs by using credentials provided by the client.
Authentication function for WooCommerce API( auth_woocom() ): This function will provide authentication for WooCommerce APIs using credentials provided by the client.
Fetch orders function for WooCommerce ( fetch_order_woocom() ): This function will use WooCommerce API ( list all orders ) and put them in a python dictionary for future comparison with Amazon orders.
Fetch orders function for Amazon ( fetch_order_amazon() ): This function will use Amazon SP-API ( Orders ) and put them in a python dictionary for future comparison with WooCommerce orders.
SKUs manually map for Amazon ( sku_map_amazon() ): This function will take manual input from the user and based on the same will map SKUs of WooCommerce to Amazon.
Check FBA function for Amazon ( check_fba_amazon() ): This function will only check if amazon order is FBA or not and provide output as ‘True’ or ‘False’ based on the FBA parameter in SP-API order details.
Tag FBA function for WooCommerce ( tag_fba_woocom() ): This function will automatically map if the SKU is FBA on amazon and not FBA in WooCommerce then update FBA status in WooCommerce using product properties ( featured or need to confirm ).
Create MCF order function for Amazon ( create_mcf_order_amazon() ): This function will only create MCF orders based on the parameters retrieved from WooCommerce API.
Order status update for WooCommerce ( status_update_woocom() ): This function will get the order status from Amazon SP-API output and update the same using WooCommerce API ( update order ).
Inventory update for WooCommerce ( inventory_update_woocom() ): This function will update inventory status using WooCommerce Product API by updating ‘stock_quantity’ inside product properties.
Main function : This function will call all the functions simultaneously and execute all the actions and terminate all the processes at the end.

All these functions are pure python functions and will get all the static values from the config file called ‘config.properties’ defined inside the project folder. If any of the credentials needed to be changed this file needs to be addressed and it will take effect in the whole project.

Here is the folder mapping of the project.

–> main_project_folder
	–> venv folder (Note: Virtual environment for all the dependencies and library)
	–> setup.py
–> main.py
–> woo_com_utils.py
–> amazon_utils.py
–> config.properties
–> settings.py

venv folder: This folder will consist of all the libraries and dependencies that are used inside the project. 

setup.py: This file will be used every time a user wants to execute operations mentioned in the ‘Specification of the application’ section. Mainly it will make sure the virtual environment is activated and execute the main.py file for the user.

main.py: This file will be used to call all the functions mentioned in the ‘Specification of the application’ section one by one and take inputs from the user wherever needed.

woo_com_utils.py: This file will contain all the functions which are ending with ‘_woocom’ and consist of the information and details of what each function will do and what will be the input and what will be the response will be mentioned inside the docstring of each function so that any developer can understand what each function is doing by itself while interacting with WooCommerce API. 

amazon_utils.py: This file will contain all the functions which are ending with ‘_amazon’ and consist of the information and details of what each function will do and what will be the input and what will be the response will be mentioned inside the docstring of each function so that any developer can understand what each function is doing by itself while interacting with Amazon using SP-API.

config.properties: This file will contain all the static values needed for Amazon and WooCommerce API to work and credentials which are provided by the client.

settings.py:    This file consists of a method and object by which other files can call the static values and credentials of config.properties file.


Method of unit testing:

Development team will use the Pytest library of python for unit testing each and every method of the whole application based on multiple parameters.

Minimum requirement of the System to run this app

OS: Ubuntu LTS (As suggested by Client)
Python version: Python 3.8.X and above. (PIP version 23.x.x)
