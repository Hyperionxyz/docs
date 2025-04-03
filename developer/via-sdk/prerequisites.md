# Prerequisites

## 1. NPM install

{% code fullWidth="true" %}
```sh
npm i @hyperionxyz/sdk
```
{% endcode %}

## 2. Setting Up Configuration

Hyperion Typescript SDK now includes a default initialization method that allows for quick generation of the Hyperion SDK configuration. You can utilize the `src/config/initCetusSDK` method to swiftly initialize the configuration. You have the option to select either 'mainnet' or 'testnet' for the network.

```typescript
import { Network } from "@aptos-labs/ts-sdk";
import { initHyperionSDK } from '@hyperionxyz/sdk'

const sdk = initHyperionSDK({network: Network.MAINNET})
```

Now, you can start using Hyperion SDK!
