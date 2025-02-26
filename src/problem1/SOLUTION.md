Provide your CLI command here:
# Extract and Fetch Order Details for TSLA Transactions

This script extracts `order_id` values for transactions where the symbol is `TSLA` from `transaction-log.txt` and fetches the corresponding order details from the API endpoint. The results are appended to `output.txt`.

## Command

- **jq**: use this command to parse JSON data
  ```bash
  jq -r 'select(.symbol == "TSLA") | .order_id' ./transaction-log.txt | while read order_id; do
  {
    echo "# curl -i -s https://example.com/api/${order_id}"
    curl -i -s "https://example.com/api/${order_id}"
    echo ""  # Add an empty line for readability
  } >> ./output.txt
  done
  ```
