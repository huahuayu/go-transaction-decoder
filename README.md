# Go transaction decoder

This is a go ethereum transaction decoder, it is used to decode `input` field like below example.

```json
{
  "txHash": "0x76066e2722dfb3a61988b7c9d2be2cb20cb4c0ab5e4ce874641f753ab5287024",
  "txContents": {
    "from": "0x98e55d2288385bc1b0ebbe0e56eac6aeb099c496",
    "gas": "0x21a68",
    "gasPrice": "0x24c988ac00",
    "hash": "0x76066e2722dfb3a61988b7c9d2be2cb20cb4c0ab5e4ce874641f753ab5287024",
    "input": "0x38ed173900000000000000000000000000000000000000000000001043561a88293000000000000000000000000000000000000000000000000000000000000025026bd100000000000000000000000000000000000000000000000000000000000000a000000000000000000000000098e55d2288385bc1b0ebbe0e56eac6aeb099c496000000000000000000000000000000000000000000000000000000005ff2944e0000000000000000000000000000000000000000000000000000000000000002000000000000000000000000a283aa7cfbb27ef0cfbcb2493dd9f4330e0fd304000000000000000000000000a0b86991c6218b36c1d19d4a2e9eb0ce3606eb48",
    "nonce": "0x304",
    "value": "0x0",
    "v": "0x26",
    "r": "0x62c507995886100ae49cd60c7c0c5e97b52a4427cbcc3874626d303758d7a46d",
    "s": "0x425c5e2b00867224d42d0a54a36010a69ebd5c007473f7e8213737fb90cf8823",
    "to": "0x7a250d5630b4cf539739df2c5dacb4c659f2488d"
  }
}
```

## Get started

```bash
git clone https://github.com/huahuayu/go-transaction-decoder.git
cd go-transaction-decoder
go run main.go
```

output:

```
{AmountOutMin:+73018504691422977465158 Path:[0xC02aaA39b223FE8D0A0e5C4F27eAD9083C756Cc2 0x6B175474E89094C44Da98b954EedeAC495271d0F] To:0xcc5B73E4dae936F3BD830F048303c076EaE3edF9 Deadline:+1609744624}
```

## Notes

0). The `input` data is in hex format.

1). In order to decode, the smart contract's abi is needed, you can copy it from etherscan or generate it by `solc`.

2). From the 3rd char to 9th char(include) of the `input` field is the function name hash. Without abi, in theory, you can't get the function name, but with abi, by looping the function name, do hash and compare, you can tell the function.

3). From 10th char to the end is the actual payload, in order to decode, you need define the input struct to map the data.

## Other decoder

[nodejs decoder](https://github.com/miguelmota/ethereum-input-data-decoder)

## Reference

[How to decode input data with ABI using golang?](https://ethereum.stackexchange.com/questions/29809/how-to-decode-input-data-with-abi-using-golang)
