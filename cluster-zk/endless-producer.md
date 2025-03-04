```
#!/bin/bash

BROKER="localhost:19092"
TOPIC="random-messages"

while true; do
ID=$((RANDOM % 10000 + 1))
VALUE=$(awk -v seed=$RANDOM 'BEGIN { srand(seed); print rand() }')
STATUS=$(shuf -e success failure pending -n 1)
TIMESTAMP=$(date +%s)
MESSAGE="{\"id\": $ID, \"value\": $VALUE, \"status\": \"$STATUS\", \"timestamp\": $TIMESTAMP}"

    echo "$MESSAGE" | /bin/kafka-console-producer --broker-list $BROKER --topic $TOPIC
    echo "Produced: $MESSAGE"
    sleep 1
done
```