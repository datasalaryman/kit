Kit is developed in public and we encourage and appreciate contributions.

## Getting Started

1. Install dependencies: `pnpm install`
2. The first time you build Kit, you will need to install the Agave test validator, which is used for some tests. `pnpm test:setup`
3. Start a test validator before running tests. `./scripts/start-shared-test-validator.sh`
4. Build + test all packages: `pnpm build`

## Development Environment

Kit is developed as a monorepo using [pnpm](https://pnpm.io/) and [turborepo](https://turborepo.com/).

Often your changes will only apply to a single package. You can run tests for a single package and watch for changes:

```shell
cd packages/accounts
pnpm turbo compile:js compile:typedefs
pnpm dev
```

## Package dependencies (Mermaid)

Dependency diagram for `@solana/kit` and its direct dependencies. **Kit** is at the center with all direct dependency packages around it; an arrow A → B means A depends on B. Packages that are depended on by more than one other appear in the **Shared dependencies** box (no arrows); footnote symbols on a package indicate which of those shared dependencies it uses.

```mermaid
graph TD
    subgraph center[" "]
        kit["kit †‡⑬③⑦◦㉚⑭⑮⑯⑥㉛¶㉜②①"]
    end

    subgraph direct["Direct dependencies"]
        accounts["accounts ㉙"]
        addresses["addresses ‡"]
        codecs["codecs ⑬"]
        errors["errors †"]
        functional["functional ③"]
        instruction_plans["instruction-plans †‡⑬③⑦⑪②①"]
        instructions["instructions ⑦"]
        keys["keys ◦"]
        offchain_messages["offchain-messages ㉚"]
        plugin_core[plugin-core]
        programs["programs †‡③②"]
        rpc["rpc ⑭"]
        rpc_api["rpc-api ⑮"]
        rpc_parsed_types["rpc-parsed-types ⑯"]
        rpc_spec_types["rpc-spec-types ⑥"]
        rpc_subscriptions["rpc-subscriptions ㉛"]
        rpc_types["rpc-types ¶"]
        signers["signers ㉜"]
        sysvars["sysvars ㉙⑬⑮⑯⑨⑱"]
        transaction_confirmation["transaction-confirmation †◦⑭⑪¶⑧⑦㉛②①"]
        transaction_messages["transaction-messages ②"]
        transactions["transactions ①"]
    end

    subgraph shared["Shared dependencies (footnotes)"]
        s1["† errors"]
        s2["‡ addresses"]
        s3["§ codecs-core"]
        s4["¶ rpc-types"]
        s5["• codecs-strings"]
        s6["◦ keys"]
        s7["① transactions"]
        s8["② transaction-messages"]
        s9["③ functional"]
        s10["④ nominal-types"]
        s11["⑤ codecs-numbers"]
        s12["⑥ rpc-spec-types"]
        s13["⑦ instructions"]
        s14["⑧ event-target-impl"]
        s15["⑨ rpc-spec"]
        s16["⑩ codecs-data-structures"]
        s17["⑪ promises"]
        s18["⑫ rpc-transformers"]
        s19["⑬ codecs"]
        s20["⑭ rpc"]
        s21["⑮ rpc-api"]
        s22["⑯ rpc-parsed-types"]
        s23["⑰ fast-stable-stringify"]
        s24["⑱ rpc-transport-http"]
        s25["⑲ rpc-subscriptions-spec"]
        s26["⑳ subscribable"]
        s27["㉗ assertions"]
        s28["㉘ text-encoding-impl"]
        s29["㉙ accounts"]
        s30["㉚ offchain-messages"]
        s31["㉛ rpc-subscriptions"]
        s32["㉜ signers"]
        s33["㉓ rpc-subscriptions-channel-websocket"]
    end

    kit --> accounts
    kit --> addresses
    kit --> codecs
    kit --> errors
    kit --> functional
    kit --> instruction_plans
    kit --> instructions
    kit --> keys
    kit --> offchain_messages
    kit --> plugin_core
    kit --> programs
    kit --> rpc
    kit --> rpc_api
    kit --> rpc_parsed_types
    kit --> rpc_spec_types
    kit --> rpc_subscriptions
    kit --> rpc_types
    kit --> signers
    kit --> sysvars
    kit --> transaction_confirmation
    kit --> transaction_messages
    kit --> transactions

    accounts --> addresses
    accounts --> codecs
    accounts --> errors
    accounts --> rpc_types
    addresses --> errors
    codecs --> errors
    instruction_plans --> addresses
    instruction_plans --> codecs
    instruction_plans --> errors
    instruction_plans --> functional
    instruction_plans --> instructions
    instruction_plans --> keys
    instruction_plans --> transaction_messages
    instruction_plans --> transactions
    programs --> addresses
    programs --> errors
    programs --> functional
    programs --> transaction_messages
    rpc --> errors
    rpc --> functional
    rpc --> rpc_api
    rpc --> rpc_spec_types
    rpc --> rpc_types
    rpc_api --> addresses
    rpc_api --> codecs
    rpc_api --> errors
    rpc_api --> keys
    rpc_api --> rpc_parsed_types
    rpc_api --> rpc_spec_types
    rpc_api --> rpc_types
    rpc_api --> transaction_messages
    rpc_api --> transactions
    rpc_parsed_types --> addresses
    rpc_parsed_types --> rpc_types
    rpc_subscriptions --> errors
    rpc_subscriptions --> functional
    rpc_subscriptions --> rpc_spec_types
    rpc_subscriptions --> rpc_types
    signers --> addresses
    signers --> errors
    signers --> instructions
    signers --> keys
    signers --> offchain_messages
    signers --> rpc_types
    signers --> transaction_messages
    signers --> transactions
    sysvars --> accounts
    sysvars --> addresses
    sysvars --> codecs
    sysvars --> errors
    sysvars --> rpc_api
    sysvars --> rpc_parsed_types
    sysvars --> rpc_types
    transaction_confirmation --> addresses
    transaction_confirmation --> errors
    transaction_confirmation --> keys
    transaction_confirmation --> rpc
    transaction_confirmation --> rpc_subscriptions
    transaction_confirmation --> rpc_types
    transaction_confirmation --> transaction_messages
    transaction_confirmation --> transactions
    transaction_messages --> addresses
    transaction_messages --> errors
    transaction_messages --> functional
    transaction_messages --> instructions
    transaction_messages --> rpc_types
    transactions --> addresses
    transactions --> errors
    transactions --> functional
    transactions --> instructions
    transactions --> keys
    transactions --> rpc_types
    transactions --> transaction_messages
```
