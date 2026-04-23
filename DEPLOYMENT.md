# Deployment Guide - Table Lorem

## GitHub Pages Status ✅

- **Repository:** https://github.com/haizlcloud/tablelorem_com
- **GitHub Pages URL:** https://haizlcloud.github.io/tablelorem_com/
- **Auto-deployment:** Enabled (pushes to `main` auto-deploy)

## Cloudflare Setup 🎯

Your domain `tablelorem.com` is registered with Cloudflare. Follow these steps to connect it to GitHub Pages:

### Step 1: Get GitHub Pages IP Address
GitHub Pages serves from: **185.199.108.153, 185.199.109.153, 185.199.110.153, 185.199.111.153**

### Step 2: Add A Records in Cloudflare

1. Log into Cloudflare Dashboard
2. Select your domain `tablelorem.com`
3. Go to **DNS** → **Records**
4. Create **4 A records** pointing to GitHub IPs:
   - `A` record: `@` → `185.199.108.153`
   - `A` record: `@` → `185.199.109.153`
   - `A` record: `@` → `185.199.110.153`
   - `A` record: `@` → `185.199.111.153`

### Step 3: Add CNAME for www (Optional)
1. Create `CNAME` record: `www` → `haizlcloud.github.io`
2. Or use redirect to point www → non-www

### Step 4: Enable HTTPS

1. Go to **SSL/TLS** → **Overview**
2. Set **SSL/TLS encryption mode** to **Full** (or **Flexible** if issues)
3. Go to **SSL/TLS** → **Edge Certificates**
4. Enable **Always Use HTTPS**

### Step 5: Configure GitHub Repository

1. Go to https://github.com/haizlcloud/tablelorem_com/settings/pages
2. Under "Custom domain", enter: `tablelorem.com`
3. Check "Enforce HTTPS"
4. GitHub will auto-create a `CNAME` file

### Step 6: DNS Propagation

After Cloudflare changes propagate (usually 5-30 minutes):
- Visit https://tablelorem.com
- Should resolve to the GitHub Pages Coming Soon page
- HTTPS should work automatically via Cloudflare

## Verification

```bash
# Check DNS resolution
dig tablelorem.com
nslookup tablelorem.com

# Check SSL certificate
curl -vI https://tablelorem.com
```

## Future Updates

Anytime you push to `main` on the GitHub repo, the site auto-updates within seconds:

```bash
git add .
git commit -m "Update: [Your changes]"
git push origin main
```

Done! 🚀
