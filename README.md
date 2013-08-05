# CodeIgniter Salesforce SOAP Library
by [Keith Hatfield](http://keithscode.com)

This library allows easy use of a Salesforce SOAP client within
your CodeIgniter Application.

Built off the Force.com Toolkit for PHP (Version 20.0)
[Force.com Documentation](http://wiki.developerforce.com/page/PHP_Toolkit)

## Installation
Copy the files from the package to the corresponding folders in your 
application folder.

### Configuration
Configuration settings can be changed in the salesforce.php file in the
config folder. See the config file for documentation.

## Usage
Once the library is loaded, you will use it as you would the Salesforce
client in a standalone app.

### Loading the Library
Once you have your configuration set, the library can be loaded from the 
controller like any other CodeIgniter library

    $this->load->library('salesforce');

### Example: Search for Account by email address

    $this->load->library('salesforce');
    $response = $this->salesforce->search('FIND {test@test.com} RETURNING Account');
    if(count($response->searchRecords)){
        foreach($response->searchRecords as $record){
            $acct_id = $record->Id;
            $account = $this->salesforce->retrieve("ID, FirstName, LastName, PersonEmail, OwnerId", 'Account', $acct_id);
            print_r($account);
        }
    }
    
### More information
For more information on using the Force.com SOAP API, see: http://www.salesforce.com/us/developer/docs/api/

See also the Force.com toolkit license in the file `third_party/salesforce/license`