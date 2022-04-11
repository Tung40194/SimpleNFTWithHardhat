1) Command
npx hardhat compile
npx hardhat run scripts/deploy.js --network mumbai
npx hardhat verify 0xDd6e09B39111acC4025E2f9B11c06e8bcD0b0eeF --network mumbai



2) 2 options to write config files

# hardhat config 1:

require("@nomiclabs/hardhat-waffle");
require('dotenv').config();
require("@nomiclabs/hardhat-ethers");
require("@nomiclabs/hardhat-etherscan");

/**
 * @type import('hardhat/config').HardhatUserConfig
 */
module.exports = {
  defaultNetwork: "matic",
  networks: {
    hardhat: {
    },
    matic: {
      url: "https://rpc-mumbai.maticvigil.com",
      accounts: [process.env.PRIVATE_KEY]
    },
    mumbai: {
      url: "https://rpc-mumbai.maticvigil.com",
      accounts: [process.env.PRIVATE_KEY]
    }
  },
  etherscan: {
    apiKey: process.env.POLYGONSCAN_API_KEY
  },
  solidity: {
    version: "0.8.1",
  },
}



# hardhat config 2:

require("@nomiclabs/hardhat-waffle");

// Go to https://www.alchemyapi.io, sign up, create
// a new App in its dashboard, and replace "KEY" with its key
const ALCHEMY_API_KEY = "su2A9rO2bDs_ezGXRJefzN3ZOsEz8lQw";

// Replace this private key with your Ropsten account private key
// To export your private key from Metamask, open Metamask and
// go to Account Details > Export Private Key
// Be aware of NEVER putting real Ether into testing accounts
const MUMBAI_PRIVATE_KEY = "f1ecb6306d77b1711cf725473d3c18e23b00ea17005eb6eeebbe042201b8033c";

module.exports = {
  solidity: "0.8.1",
  networks: {
    mumbai: {
      url: `https://polygon-mumbai.g.alchemy.com/v2/su2A9rO2bDs_ezGXRJefzN3ZOsEz8lQw`,
      accounts: [`${MUMBAI_PRIVATE_KEY}`]
    }
  }
};