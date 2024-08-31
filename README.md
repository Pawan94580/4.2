# Custom Hyperchain Configuration on Avalanche with HyperSDK

This code snippet describes a custom hyperchain on the Avalanche network using the HyperSDK. This includes setting up a human-readable part (HRP), chain name and token symbol, and starting a chain ID record for services and authorizations

## Description

The provided Go code is part of a project aimed at developing a customized hyperchain on the Avalanche blockchain using the HyperSDK. It starts with regular expressions like the human readable portion (HRP) which means "PawanPandey", the series name as "Pawan" and the token symbol as "PP" The code also starts with a unique identifier for the series by the Avalanche ids package so, make sure the name is correctly converted to a valid ID.

In addition, the code configures global registries for actions and authorizations (ActionRegistry and AuthRegistry). These registries are important for handling the various actions and authorization schemes in the hyperchain, making it easier to manage and modularly extend the use of the chain These structures are important for using the hyperchain and with avalanche network the extensive has communicated.

## Getting Started

In this assessment, I have used remix IDE [https://remix.ethereum.org/]

### Executing program
```
// Copyright (C) 2023, Ava Labs, Inc. All rights reserved.
// See the file LICENSE for licensing terms.

package consts

import (
	"github.com/ava-labs/avalanchego/ids"
	"github.com/ava-labs/avalanchego/vms/platformvm/warp"
	"github.com/ava-labs/hypersdk/chain"
	"github.com/ava-labs/hypersdk/codec"
	"github.com/ava-labs/hypersdk/consts"
)

const (
	// TODO: choose a human-readable part for your hyperchain
	HRP = "PawanPandey"
	// TODO: choose a name for your hyperchain
	Name = "Pawan"
	// TODO: choose a token symbol
	Symbol = "PP"
)

var ID ids.ID

func init() {
	b := make([]byte, consts.IDLen)
	copy(b, []byte(Name))
	vmID, err := ids.ToID(b)
	if err != nil {
		panic(err)
	}
	ID = vmID
}

// Instantiate registry here so it can be imported by any package. We set these
// values in [controller/registry].
var (
	ActionRegistry *codec.TypeParser[chain.Action, *warp.Message, bool]
	AuthRegistry   *codec.TypeParser[chain.Auth, *warp.Message, bool]
)
```
To compile the code, click on the "Solidity Compiler" tab in the left-hand sidebar. Make sure the "Compiler" option is set to "0.8.7" (or another compatible version), and then click on the button.

Once the code is compiled, you can deploy the contract by clicking on the "Deploy & Run Transactions" tab in the left-hand sidebar. Select the contract from the dropdown menu, and then click on the "Deploy" button.

## Authors

Pawan Kumar - (https://www.linkedin.com/in/pawan-pandey-540a94266/)


## License

This project is licensed under the MIT License
