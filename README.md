# familiars-token-drops 🧝🏾
This directory includes details around the token airdrop and how the results were produced.

Metaboss snapshot [ArTyyFU6iiKfJSpsKz4LTuak6rTrrxg6E73bB4ThLMYs_holders.json](./ArTyyFU6iiKfJSpsKz4LTuak6rTrrxg6E73bB4ThLMYs_holders.json)

Assuming you download the metadata for the darkelvs using metaboss decode in `../arweave-metadata` with the silver searcher installed:

```
ag -l 'Mask' ../arweave-metadata/ | cut -d'/' -f3 | cut -d'.' -f1 | sort > mask-mints-addresses.csv
```

Produce a line by line list of snapshots for use with grep:
```
jq -c '.[]' ArTyyFU6iiKfJSpsKz4LTuak6rTrrxg6E73bB4ThLMYs_holders.json > snapshot-lines.json
```

cat crystal-freak-mints-addresses.csv | xargs -n1 -I '{}' jq -r -c 'select(.mint_account == "{}") | .owner_wallet' snapshot-lines.json | sort > crystal-freak-winners.csv
cat half-abstract-mints-addresses.csv | xargs -n1 -I '{}' jq -r -c 'select(.mint_account == "{}") | .owner_wallet' snapshot-lines.json | sort > half-abstract-winners.csv
cat liquid-demon-mints-addresses.csv | xargs -n1 -I '{}' jq -r -c 'select(.mint_account == "{}") | .owner_wallet' snapshot-lines.json | sort > liquid-demon-winners.csv
cat spiky-freak-mints-addresses.csv | xargs -n1 -I '{}' jq -r -c 'select(.mint_account == "{}") | .owner_wallet' snapshot-lines.json | sort > spiky-freak-winners.csv
cat tech-vulture-mints-addresses.csv | xargs -n1 -I '{}' jq -r -c 'select(.mint_account == "{}") | .owner_wallet' snapshot-lines.json | sort > tech-vulture-winners.csv
