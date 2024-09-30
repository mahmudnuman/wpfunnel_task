Implementation Details

The solution is implemented by extending the existing WPFNL_Checkout class in the WPFunnels plugin.breakdown of the key components:

#add register_activation_hook(__FILE__, array('WPFNL_Checkout', 'create_customers_table')); in \wp-content\plugins\wpfunnels\wpfnl.php 

Custom Database Table Creation:

A new method create_customers_table() is added to create a custom table for storing customer data.
This method is called via a register_activation_hook() when the plugin is activated.


Customer Data Storage:

The save_checkout_fields() method is modified to call a new store_customer_data() method after an order is placed.
store_customer_data() saves the customer's name, email, and order ID to the custom table.


Email Sending Logic:

A new check_and_send_emails() method is added, which is called after storing each customer's data.
This method checks if there are 100 or more customers in the table. If so, it sends thank you emails and then removes those customers from the table.


Thank You Email Function:

A send_thank_you_email() method is implemented to send personalized emails to each customer.
It retrieves the store name and the customer's purchased products to include in the email.
