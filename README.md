# Node.js-Notes

## CORS (Cross-Origin Resource Sharing)
- CORS errors occur when a web application running on one domain (origin) tries to fetch resources (API, fonts, scripts) from another domain without proper permissions.
### Solutions to Prevent CORS Issues
1. Enable CORS on the Server (Best Approach)
2. Modify Headers in the Backend
3. Use a Proxy (Frontend Side Fix)
4. Enable CORS in Browser (Temporary Fix for Testing)

### Best Practice
- ✅ Modify the backend to send proper CORS headers (recommended).
- ✅ Use a proxy if backend changes are not possible.
- ✅ Do not disable CORS security in production.

# What is NodeJs?
- Javascript runtime environment
- Run javascript not only browser even run anywhere.
- NodeJs use V8 and V8 is JS engine build by google that run javascript in browser.
- Engine mean: Engine take js code and node use and its compile js code in machine code.
- V8 written in C++ language.
<img width="780" alt="node js 2025-03-21 at 4 13 19 PM" src="https://github.com/user-attachments/assets/1eb1f606-7e41-4680-85bf-1604b939a18c" />

