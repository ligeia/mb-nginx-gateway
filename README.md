This nginx-based gateway is designed to help users who want to use a MusicBrainz mirror but maintain a fallback to MusicBrainz production. It's main intent is to handle new releases which aren't yet replicated on the mirror: when the mirror produces a 404, it routes to the production server. It also does so when the mirror is not responding.

It was also designed for mirrors without Solr enabled. When you submit a query that depends on Solr, it will again route to production instead.


mkdir mb_gatway

cp docker-compose.yml mb_gateway/

cd mb_gateway/

docker compose -f docker-compose.yml pull

cp nginx.conf mb_gateway/

## Make sure the upstream mb_mirror (in # ---- Upstreams ---- ) points to your MusicBrainz mirror's address and port

docker compose -f docker-compose.yml up -d
