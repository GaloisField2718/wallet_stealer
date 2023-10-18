# Bitcoin Wallet Stealer 💳


This method wants to use seedphrase brute-force with optimised check for balances. 

We use [hnzr/bip39_checksum](https://github.com/hnzr/bip39_checksum/tree/master).

## Run ⚙️  

`python3 main.py`

Doesn't work for now


## Algorithm 📟

This is the general idea 💡

### Functions required ⨐

- `read_dict(file) -> list` : Read dictionnary file ;
- `seed_from_dict(dic) -> list` : Pick 11 random words into `dic` and calculate the last one by checksum ;
- `convert_seed_into_addresses(seed) -> list` : Return public addresses derived from seed. It has to stop when we find 2 same addresses. Important : manage possible errors (e.g. inifinite runtime) ;
- `check_balance(address) -> int` : Make a bitcoin call to request balance of address ;
- `map(address, seed) -> string` : Return the private key ;
- `write(text_to_write, file) -> void` : Write non empty address balance into file. The structure of `text_to_write` should be like `(public_address, pv_key, balance)`. 


### Main 📙

```py

dic = read_dict('dictionnary.txt')
rand_seed = seed_from_dict(dic)
addresses = convert_seed_into_addresses(rand_seed)
for add in addresses:
    balance = check_balance(add)
    if bal != 0:
        pv_key = map(add, rand_seed)
        write((add,pv_key,bal), hack.xt)
```



