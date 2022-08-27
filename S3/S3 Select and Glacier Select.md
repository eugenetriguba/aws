* Allow you to use SQL-Like statements to retrieve partial objects from S3 and Glacier.
* Often want to retrieve the entire object. However, retrieving a whole huge object takes time and uses the full object space ($$). Filtering at the client side doesn't reduce this.
* Pre-filtered partial select is retrieved by S3 (faster and cheaper).
* CSV, JSON, Parquet, BZIP2 Compression for CSV and JSON.

Application data stored on S3 and can be filtered to app. W/o S3 Select filtering occurs in the application itself and the full amount is retrieved and billed for by S3.
