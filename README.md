# Description of the project 1: Private Blockchain Application

As a student of the Udacity Nanodegree program, I am starting my journey as a Blockchain Developer, this project allows me to demonstrate
that I am familiarized with the fundamentals concepts of a Blockchain platform.
Concepts like:
    - Block
    - Blockchain
    - Wallet
    - Blockchain Identity
    - Proof of Existance

In this project I will have a boilerplate code with a REST Api already setup to expose some of the functionalities
I will implement in my private blockchain.

## Dependencies

- Some of the libraries or npm modules you will use are:
    - "bitcoinjs-lib": "^4.0.3",
    - "bitcoinjs-message": "^2.0.0",
    - "body-parser": "^1.18.3",
    - "crypto-js": "^3.1.9-1",
    - "express": "^4.16.4",
    - "hex2ascii": "0.0.3",
    - "morgan": "^1.9.1"


## How to test your application functionalities?

Using POSTMAN and debug code using VSCode.

1. Run your application using the command `node app.js`
You should see in your terminal a message indicating that the server is listening in port 8000:
> Server Listening for port: 8000

2. To make sure your application is working fine and it creates the Genesis Block you can use POSTMAN to request the Genesis block:
    ![Request: http://localhost:8000/block/0 ]()

    This command is probably outdated so I used instead ![Request: http://localhost:8000/block/height/0 ](https://github.com/quidba7/blockchain_project_1/blob/main/pic/get_block_height.PNG)

    Message in Postman:
    ```json
    {
        "hash": "a6bab81e354dd7d0894f7f2647b5fb1dd5b95cbd5648ecc21880e5534cea1df2",
        "height": 0,
        "body": "7b2264617461223a2247656e6573697320426c6f636b227d",
        "time": "1629140281",
        "previousBlockHash": null
    }   
    ```

3. Make your first request of ownership sending your wallet address:
    ![Request: http://localhost:8000/requestValidation ](https://github.com/quidba7/blockchain_project_1/blob/main/pic/post_message.PNG)

4. Sign the message with your Wallet:
    ![Use the Wallet to sign a message](https://github.com/quidba7/blockchain_project_1/blob/main/pic/signature.PNG)
    
    In order to post signature , I generate legacy address as default wallet in electrum is sigwit. I followed instructions from this blog: https://bitcointalk.org/index.php?topic=5338687.0
    
    Message in Postman:

    ```json
        {
            "address":"1BnBZxjZS8FuvAmYryhNv9pjNrywuLCemn"
        }
    ```

5. Submit your Star
     ![Request: http://localhost:8000/submitstar](https://github.com/quidba7/blockchain_project_1/blob/main/pic/postStar_postman.PNG) ![VScode:](https://github.com/quidba7/blockchain_project_1/blob/main/pic/postStar_debug.PNG)

    Message in postman:

    ```json
        {
            "address":"1BnBZxjZS8FuvAmYryhNv9pjNrywuLCemn",
            "signature":"IGSRH8PzJRpom3YU03klzZ4soF5bvt/hHeDKNjmnGQ+fA4Q1nRMigDZdfDjvYUs52dpvRg1PoXUBodmg3Mgg5u0=",
            "message":"1BnBZxjZS8FuvAmYryhNv9pjNrywuLCemn:1629140445:startRegistr",
            "star": {
                "dec": "68° 52' 56.9",
                "ra": "16h 29m 1.0s",
                "story": "Testing the story 2"
            }
        }
    ```

6. Retrieve Stars owned by me
    ![Request: http://localhost:8000/blocks/<WALLET_ADDRESS>](https://github.com/quidba7/blockchain_project_1/blob/main/pic/get_wallet_star_postman.PNG)

    Message in postman:

    ```json
        [
            {
                "owner": "1BnBZxjZS8FuvAmYryhNv9pjNrywuLCemn",
                "data": {
                    "dec": "68Â° 52' 56.9",
                    "ra": "16h 29m 1.0s",
                    "story": "Testing the story 2"
                }
            }
        ]
    ```