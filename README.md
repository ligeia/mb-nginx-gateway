mkdir mb_gatway

cp docker-compose.yml mb_gateway/

cd mb_gateway/

docker compose -f docker-compose.yml pull

cp nginx.conf mb_gateway/

## Make sure the upstream mb_mirror (in # ---- Upstreams ---- ) points to your MusicBrainz mirror's address and port

docker compose -f docker-compose.yml up -d
