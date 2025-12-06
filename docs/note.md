# Spotify Web API + Postman Integration

This is a basic setup for testing Spotify APIs using Postman.

---

## Steps

1. **Create a Spotify App**
   - Go to [Spotify Developer Dashboard](https://developer.spotify.com/dashboard).
   - Register a new app.
   - Get your `client_id` and `client_secret`.
   - Add a redirect URI (e.g., http://localhost:3000/callback).

2. **Set Up Postman**
   - Create a new collection (e.g., "Spotify API").
   - Add variables:
     - `base_url = https://api.spotify.com/v1`
     - `auth_url = https://accounts.spotify.com/authorize`
     - `token_url = https://accounts.spotify.com/api/token`
     - `client_id`, `client_secret`, `redirect_uri`, `access_token`

3. **Authorization Flow**
   - Request User Authorization → `GET {{auth_url}}` with query params (`client_id`, `redirect_uri`, `scope`, `response_type=code`).
   - Exchange Code for Token → `POST {{token_url}}` with `client_id`, `client_secret`, `redirect_uri`, and `code`.
   - Save the `access_token` in your environment.

4. **Make API Calls**
   - Use `{{base_url}}` + endpoints (e.g., `/me/playlists`).
   - Add header: `Authorization: Bearer {{access_token}}`.
   - Run requests and check responses.

---

## Notes

- Public URLs (base, auth, token) can stay in the collection.
- Secrets (client_id, client_secret, tokens) should be in the environment.
- Always select the right environment before running requests.
