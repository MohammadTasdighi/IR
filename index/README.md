normalize_date(date_str)

Converts a Persian (Jalali) date string into a Gregorian date format (yyyy-MM-dd).
If the date is invalid or empty, it returns None.
This ensures Elasticsearch receives properly formatted date values.

___

gen_actions(df_chunk)

Generates indexing actions (documents) for Elasticsearch from a Pandas DataFrame chunk.
Each row in the CSV is transformed into a JSON document containing fields like title, body, advantages, disadvantages, and created_at.
Returns a generator to optimize memory usage when indexing large datasets.

___

main()

The main execution function.
It reads the CSV file in chunks, processes each chunk using gen_actions(), and sends the documents to Elasticsearch using the bulk API.
Handles errors, logs progress, and prints the total number of indexed documents upon completion.
