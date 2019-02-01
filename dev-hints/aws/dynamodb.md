# DynamoDB

#### Example command to query a table using key condition expressions and returning the consumed capacity units

    aws dynamodb query --table-name <table_name> \
      --key-condition-expression "field_name = :s AND field_name_two BETWEEN :s1 AND :s2" \
      --expression-attribute-values '{ ":s": { "S": "ALI" }, ":s1": { "S": "2018-01-03" }, ":s2": { "S": "2018-12-31" } }' \
      --return-consumed-capacity TOTAL