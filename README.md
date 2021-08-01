# Elastic stack (ELK) on Docker

# Get all ips from AWS public CIDR blocks for elasticsearch services
`
curl https://ip-ranges.amazonaws.com/ip-ranges.json | jq -r '[.prefixes[] | select(.service=="AMAZON").ip_prefix] - [.prefixes[] | select(.service=="ES").ip_prefix] | .[]' > aws_elasticsearch_service_cidr.txt
`

# Activate the stack
`
docker-compose up -d
`

# Then, Visit the kibana (5601) and visualive the open ports in the dashboard.
