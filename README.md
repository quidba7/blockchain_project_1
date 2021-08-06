# Private Blockchain Application

You are starting your journey as a Blockchain Developer, this project allows you to demonstrate
that you are familiarized with the fundamentals concepts of a Blockchain platform.
Concepts like:
    - Block
    - Blockchain
    - Wallet
    - Blockchain Identity
    - Proof of Existance

Are some of the most important components in the Blockchain Framework that you will need to describe and also
why not? Implement too.

In this project you will have a boilerplate code with a REST Api already setup to expose some of the functionalities
you will implement in your private blockchain.

## What tools or technologies you will use to create this application?

- Some of the libraries or npm modules you will use are:
    - "bitcoinjs-lib": "^4.0.3",
    - "bitcoinjs-message": "^2.0.0",
    - "body-parser": "^1.18.3",
    - "crypto-js": "^3.1.9-1",
    - "express": "^4.16.4",
    - "hex2ascii": "0.0.3",
    - "morgan": "^1.9.1"


## How to test your application functionalities?

To test your application I recommend you to use POSTMAN, this tool will help you to make the requests to the API.
Always is useful to debug your code see what is happening in your algorithm, so I will let you this video for you to check on how to do it >https://www.youtube.com/watch?v=6cOsxaNC06c . Try always to debug your code to understand what you are doing.

1. Run your application using the command `node app.js`
You should see in your terminal a message indicating that the server is listening in port 8000:
> Server Listening for port: 8000

2. To make sure your application is working fine and it creates the Genesis Block you can use POSTMAN to request the Genesis block:
    ![Request: http://localhost:8000/block/0 ]()
3. Make your first request of ownership sending your wallet address:
    ![Request: http://localhost:8000/requestValidation ]()
4. Sign the message with your Wallet:
    ![Use the Wallet to sign a message](pic/post_message.png)
    
    In order to post signature , I generate legacy address as default wallet in electrum is sigwit. I followed instructions from this blog: https://bitcointalk.org/index.php?topic=5338687.0
    
    Message in Postman:
```json
    {
        "address":"1BnBZxjZS8FuvAmYryhNv9pjNrywuLCemn"
    }
```

5. Submit your Star
     ![Request: http://localhost:8000/submitstar](pic/postStar_postman.png) (pic/postStar_debug.png)

    Message in postman
```json
    {
        "address":"1BnBZxjZS8FuvAmYryhNv9pjNrywuLCemn",
        "signature":"HwXgZus8bwThx8Jj7hioYtEx9MmY6aLwUbeASYq+FMH8bv4umO8JxRWB5suut1FPetNe0a/m9nYFtk5Hgt9Kmqs=",
        "message":"1BnBZxjZS8FuvAmYryhNv9pjNrywuLCemn: 1628155274:startRegistry",
        "star": {
            "dec": "68° 52' 56.9",
            "ra": "16h 29m 1.0s",
            "story": "Testing the story 2"
		}
    }
```

6. Retrieve Stars owned by me
    ![Request: http://localhost:8000/blocks/<WALLET_ADDRESS>](pic/get_wallet_star_postman.png)