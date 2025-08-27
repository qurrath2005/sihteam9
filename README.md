# SIH25027 Starter Pack — v2 (Beginner friendly)

**What's new in v2**
- `/api/create-batch` to group CollectionEvents into a batch and return a QR image
- `/api/batch/:id/provenance` to read a simple provenance bundle
- Auto-creates DB tables for collection events, batches, and batch_items
- Postman collection included

## Quick start
```bash
cp .env.example .env
docker compose -f infra/docker-compose.yml up -d
cd middleware
npm install
npm run dev
```

## Test
1) Create a few `CollectionEvent`s (see v1 README or Postman).
2) Create a batch:
```bash
curl -X POST http://localhost:3000/api/create-batch   -H "Content-Type: application/json"   -d '{"eventIds":[1,2]}'
```
You get `{ batchId, qrPngBase64 }` (open the Base64 as an image).
3) View provenance:
`GET http://localhost:3000/api/batch/1/provenance`
