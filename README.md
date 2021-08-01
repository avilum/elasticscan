# AWS ELK (ES - ElasticSearch Service) Port Scanner 

## 1. Get all ips from AWS public CIDR blocks for elasticsearch services
`
curl https://ip-ranges.amazonaws.com/ip-ranges.json | jq -r '[.prefixes[] | select(.service=="AMAZON").ip_prefix] - [.prefixes[] | select(.service=="ES").ip_prefix] | .[]' > aws_elasticsearch_service_cidr.txt
`

## 2. Activate the stack
`
docker-compose up -d
`

## 3. Visualizing Open Servers
Then, Visit the kibana (5601) and visualive the open ports in the dashboard.

## 4. Re-run port scan:
1. `docker-compose stop masscan`
2. `nano aws_elasticsearch_service_cidr.txt # Edit the CIDR blocks to scan with masscan` 
3. `docker-compose start masscan`
