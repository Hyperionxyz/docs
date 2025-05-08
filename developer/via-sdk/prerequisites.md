# Prerequisites

## 1. NPM install

```sh
$ pnpm i @hyperionxyz/sdk
```

## 2. Setting Up Configuration

> You need create an Aptos Build account, and generate a API key for using Aptos public services. Click [https://build.aptoslabs.com/docs/introduction](https://build.aptoslabs.com/docs/introduction) to learn more.

Hyperion Typescript SDK now includes a default initialization method that allows for quick generation of the Hyperion SDK configuration. You can utilize the `src/config/initCetusSDK` method to swiftly initialize the configuration. You have the option to select either 'mainnet' or 'testnet' for the network.

```typescript
import { Network } from "@aptos-labs/ts-sdk";
import { initHyperionSDK } from '@hyperionxyz/sdk'

const sdk = initHyperionSDK({
    network: Network.MAINNET, 
    APTOS_API_KEY: "Your APTOS API key"
})
```

Now, you can start using Hyperion SDK!
