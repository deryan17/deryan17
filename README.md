npm i thirdweb
import {
  createThirdwebClient,
  getContract,
} from "thirdweb";
import { defineChain } from "thirdweb/chains";

// create the client with your clientId, or secretKey if in a server environment
const client = createThirdwebClient({
  clientId: "YOUR_CLIENT_ID",
});

// connect to your contract
const contract = getContract({
  client,
  chain: defineChain(93384),
  address: "0xd4B8F7ea1BeCd05e9b2A6C7A5c810dc8b39bFee6",
});

import {
  prepareContractCall,
  sendTransaction,
} from "thirdweb";

const transaction = await prepareContractCall({
  contract,
  method:
    "function approve(address spender, uint256 amount) returns (bool)",
  params: [spender, amount],
});
const { transactionHash } = await sendTransaction({
  transaction,
  account,
});

