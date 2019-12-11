**How to set up loyalty token on XinFin.Network**

**Step 1**: Create and Deploy Loyalty Smart Contract and Deploy on Public network.

Goto: https://mycontract.co/ and create Loyalty Token (Token Contract) After Entering Detail like: Token Name, Token Symbol and Total Token Supply. 

Note: After Creating Token Contract then Deploy to XinFin Network and Download Private Key and store at safe place Without a doubt, the safest way to store any Private Key is using a paper wallet. 


**Step 2**: Setup XinFin Full node to get Full control over your Privaye key and Data backup. 

Follow step and setup XinFin Full Node :- https://github.com/XinFinOrg/XinFin-Node


**Step 3**: Install Dependencies. 
Download [Nodejs and npm](https://docs.npmjs.com/getting-started/installing-node "Nodejs install") if you don't have them

Install dependencies:

`npm install xdc3@1.0.0-beta.41`


**Step 4**: Dowlonad Ready Script File, Learn API Command to Manage Loyalty Loken with your ERP/CRM System: 

e.g. `node Token_Transfer.js RPC_IP RPC_Port from_address to_address amount contract_address private_key decimals`

Execute XRC20 Transfer : 
`node Token_Transfer.js testnet.xinfin.network 443 xdcD000ea0B094EB93Bf4a545994048e630DFef922d  xdca5b6045297fc6aec660a2769e3bad08acb2098b3  1000  xdc880997e0a6de5671e8fc9e7b5424cd07b51c9ab8  c3d09a56285d70a531128cec7eb5ae905070f17705d2e1d112eaafd7d257f29b 18`

```
//to execute the script run the following command
// node file_name.js wallet_ip port from_address to_address amount contract_address private_key decimals


//ip and port for the blockchain node to be connected
var wallet_ip = process.argv[2];
var wallet_port = process.argv[3];
//address from which tokens need to be sent
var from_address = process.argv[4];
//address to which tokens need to be sent
var to_address = process.argv[5];
//amount of tokens to be sent
var sendamount = process.argv[6];
//contract address of the ERC20 token
var coinAddress = process.argv[7];
//private key of the from address
var private_key = process.argv[8];
//predefined no. of decimals in the contract
var tokendecimal = process.argv[9];

//web3 library needed
const Web3 = require("xdc3");

//connecting to the web3 provider
if (typeof web3 !== "undefined") {
  web3 = new Web3(web3.currentProvider);
} else {
  web3 = new Web3(
    new Web3.providers.HttpProvider("http://" + wallet_ip + ":" + wallet_port)
  );
}

//if the token decimal isn't specified then set it to default 18 and converting the amount to decimal form
if (tokendecimal == 18 || tokendecimal == null) {
  var send_amount = web3.utils.toWei(sendamount);
} else {
  var send_amount = sendamount * Math.pow(10, tokendecimal);
}

//data required for estimating the gas that will be needed for the transaction to complete
var est_main_gas = { from: from_address, to: to_address, value: send_amount };

//standard ERC20 contract ABI
const coinabi = [
  {
    constant: true,
    inputs: [],
    name: "name",
    outputs: [{ name: "", type: "string" }],
    payable: false,
    stateMutability: "view",
    type: "function"
  },
  {
    constant: false,
    inputs: [
      { name: "_spender", type: "address" },
      { name: "_value", type: "uint256" }
    ],
    name: "approve",
    outputs: [{ name: "success", type: "bool" }],
    payable: false,
    stateMutability: "nonpayable",
    type: "function"
  },
  {
    constant: true,
    inputs: [],
    name: "totalSupply",
    outputs: [{ name: "", type: "uint256" }],
    payable: false,
    stateMutability: "view",
    type: "function"
  },
  {
    constant: false,
    inputs: [
      { name: "_from", type: "address" },
      { name: "_to", type: "address" },
      { name: "_value", type: "uint256" }
    ],
    name: "transferFrom",
    outputs: [{ name: "success", type: "bool" }],
    payable: false,
    stateMutability: "nonpayable",
    type: "function"
  },
  {
    constant: true,
    inputs: [],
    name: "decimals",
    outputs: [{ name: "", type: "uint256" }],
    payable: false,
    stateMutability: "view",
    type: "function"
  },
  {
    constant: true,
    inputs: [{ name: "_owner", type: "address" }],
    name: "balanceOf",
    outputs: [{ name: "balance", type: "uint256" }],
    payable: false,
    stateMutability: "view",
    type: "function"
  },
  {
    constant: true,
    inputs: [],
    name: "owner",
    outputs: [{ name: "", type: "address" }],
    payable: false,
    stateMutability: "view",
    type: "function"
  },
  {
    constant: true,
    inputs: [],
    name: "symbol",
    outputs: [{ name: "", type: "string" }],
    payable: false,
    stateMutability: "view",
    type: "function"
  },
  {
    constant: false,
    inputs: [
      { name: "_to", type: "address" },
      { name: "_value", type: "uint256" }
    ],
    name: "transfer",
    outputs: [{ name: "success", type: "bool" }],
    payable: false,
    stateMutability: "nonpayable",
    type: "function"
  },
  {
    constant: true,
    inputs: [
      { name: "_owner", type: "address" },
      { name: "_spender", type: "address" }
    ],
    name: "allowance",
    outputs: [{ name: "remaining", type: "uint256" }],
    payable: false,
    stateMutability: "view",
    type: "function"
  },
  {
    constant: false,
    inputs: [{ name: "_newOwner", type: "address" }],
    name: "transferOwnership",
    outputs: [],
    payable: false,
    stateMutability: "nonpayable",
    type: "function"
  },
  {
    inputs: [],
    payable: false,
    stateMutability: "nonpayable",
    type: "constructor"
  },
  {
    anonymous: false,
    inputs: [
      { indexed: true, name: "from", type: "address" },
      { indexed: true, name: "to", type: "address" },
      { indexed: false, name: "value", type: "uint256" }
    ],
    name: "Transfer",
    type: "event"
  },
  {
    anonymous: false,
    inputs: [
      { indexed: true, name: "owner", type: "address" },
      { indexed: true, name: "spender", type: "address" },
      { indexed: false, name: "value", type: "uint256" }
    ],
    name: "Approval",
    type: "event"
  }
];

//creating an instance of the ERC20 contract
const coin = new web3.eth.Contract(coinabi, coinAddress);
//checking the balance of the from address to asure that it has sufficient balance to complete the transaction
coin.methods.balanceOf(from_address).call(function(err, bal) {
  bal = web3.utils.fromWei(bal, "wei").toString(10);

//generating the data for the transfer method of the ERC20 contract
  const txdata = coin.methods.transfer(to_address, send_amount).encodeABI(); //to adress

//estimating the gas required for the transaction to be completed
  web3.eth.estimateGas(est_main_gas, function(gaslimit_err, gaslimit) {
 //getting the current gas price on the network or else setting it to minimum 4 Gwei so that it won't take much time to execute 
    web3.eth.getGasPrice(function(gas_err, getGasPrice) {
      if (gas_err) {
        console.log(JSON.stringify({ error1: gas_err }));

        getGasPrice = 4000000000;
      } else {
        if (getGasPrice < 4000000000 || getGasPrice == null) {
          getGasPrice = 4000000000;
        }
      }

//finding the nonce for the from address
      web3.eth.getTransactionCount(from_address, function(
        tx_count_err,
        transactionCount
      ) {
        if (tx_count_err) {
          console.log(
            JSON.stringify({ "transaction count error ": tx_count_err })
          );
        }

//generating the transaction data
        const trans_det = {
          nonce: transactionCount, // Replace by nonce for your account on geth node
          gasPrice: getGasPrice,
          gas: "200000",
          to: coinAddress, //contract address
          from: from_address, //coin base
          data: txdata
        };

//signing the transaction generated to get a raw transaction
        web3.eth.accounts.signTransaction(trans_det, private_key, function(
          sign_error,
          signedTransaction
        ) {
          if (sign_error) {
            console.log(
              JSON.stringify({ "sign transaction error ": sign_error })
            );
          }

//raw transaction to be sent to the network.
          const rawTransaction = signedTransaction.rawTransaction;
          //sending the raw transaction after converting it in to hex format
          web3.eth.sendSignedTransaction(
            rawTransaction.toString("hex"),
            function(trans_err, txid) {
                     //printing the transaction hash or error
              if (trans_err)
                console.log(JSON.stringify({ "transaction error": trans_err }));

              if (txid && txid != "")
                console.log(JSON.stringify({ tx: txid, hash: txid }));
            }
          );
        });
      });
    });
  });
});
```

**Other Useful Command**

eth.estimateGas
eth.getGasPrice
eth.getTransactionCount
eth.accounts.signTransaction
eth.sendSignedTransaction

Ref Link: https://github.com/ethereum/wiki/wiki/JavaScript-API

Note: XinFin Network Replace Address start from OX to XDC 


**Troubleshooting**

Public discussions on the technical issues. Please Join Below mention Public Chat or Group. 

[Slack Public Chat](https://launchpass.com/xinfin-public), 

[Telegram Chat](http://bit.do/Telegram-XinFinDev), 

[Forum](https://xinfin.net)
