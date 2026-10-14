This nginx-based gateway is designed to help users who want to use a MusicBrainz mirror but maintain a fallback to MusicBrainz production. It's main intent is to handle new releases which aren't yet replicated on the mirror: when the mirror produces a 404, it routes to the production server. It also does so when the mirror is not responding.

It was also designed for mirrors without Solr enabled. When you submit a query that depends on Solr, it will again route to production instead.

This was built by Claude Opus 4.5. I am not actively maintaining it but may be able to provide basic support if you open an Issue.

Setup

mkdir mb_gateway

cp docker-compose.yml mb_gateway/

cd mb_gateway/

docker compose -f docker-compose.yml pull

cp nginx.conf mb_gateway/

## Make sure the upstream mb_mirror (in nginx.conf # ---- Upstreams ---- ) points to your MusicBrainz mirror's address and port

docker compose -f docker-compose.yml up -d

Now point any scripts you use to the mb_gateway instead of directly to the mirror. In this case, rather than pointing to localhost:5000, you would point to localhost:5110. If you don't want to use 5110 for the gateway, change that in the docker-compose.yml file before your docker compose pull.
