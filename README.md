# node-codebase (API wrapper for Node.js)

A NodeJS wrapper for the [CodeBaseHQ](http://www.codebasehq.com/) API. 

## Install from NPM
    npm install node-codebase

## Example usage

    var http = require('http'),
        Codebase = require('codebase');

    process.env.NODE_TLS_REJECT_UNAUTHORIZED = 0 

    var cb = new Codebase(
        'api url',
        'account/username:apikey'
    );

    http.createServer(function (req, res) {
        
        if (req.url !== '/') {
            res.end();
            return;
        }

        cb.activity(function (err, data) {
          if (err) {
            res.end('There was an error!' + data);
          }
      
          res.end(JSON.stringify(data));
        });

    }).listen(8080);

    console.log('Server running at http://localhost:8080/');


## Config

API URL should be the following in most cases:
'api3.codebasehq.com'

Theres a bug in node, to be able to connect add the following line before calling codebase:

process.env.NODE_TLS_REJECT_UNAUTHORIZED = 0 


## TODO

* Write documentation
* Finish "tickets.attachments.upload" method
