# Password Manager 🔐

A secure web-based password manager with encryption, import/export functionality, and Vercel deployment support.

## Features

✅ **Master Password Authentication** - Single password to unlock all your passwords  
✅ **AES-256 Encryption** - All passwords encrypted with strong encryption  
✅ **Add/Edit/Delete Passwords** - Full CRUD operations  
✅ **Copy to Clipboard** - One-click copy for usernames and passwords  
✅ **Show/Hide Passwords** - Toggle password visibility  
✅ **Import/Export Data** - Backup and restore passwords as JSON  
✅ **Responsive Design** - Works on desktop, tablet, and mobile  
✅ **Vercel Ready** - Deploy directly to Vercel  

## Prerequisites

- Node.js 18+ 
- npm or yarn

## Installation

1. **Clone the repository**
```bash
git clone https://github.com/baimdevs/CGS.git
cd CGS
```

2. **Install dependencies**
```bash
npm install
```

3. **Setup environment variables**
```bash
cp .env.example .env.local
```

4. **Generate Master Password Hash**

Generate your master password hash:
```bash
node -e "const crypto = require('crypto'); console.log(crypto.createHash('sha256').update('your-password-here').digest('hex'))"
```

Then update `.env.local`:
```env
NEXT_PUBLIC_MASTER_PASSWORD_HASH=your_generated_hash_here
ENCRYPTION_SECRET_KEY=your_super_secret_key_min_32_characters_long
```

## Development

```bash
npm run dev
```

Open [http://localhost:3000](http://localhost:3000) in your browser.

## Build for Production

```bash
npm run build
npm start
```

## Deployment to Vercel

### Option 1: Using Vercel CLI

```bash
npm install -g vercel
vercel
```

### Option 2: Using GitHub Integration

1. Push your code to GitHub
2. Go to [vercel.com](https://vercel.com)
3. Import your repository
4. Add environment variables:
   - `NEXT_PUBLIC_MASTER_PASSWORD_HASH`
   - `ENCRYPTION_SECRET_KEY`
5. Click Deploy

## Usage

### First Time Setup

1. Enter your master password on the login page
2. You're authenticated for 24 hours

### Adding Passwords

1. Click "➕ Add Password"
2. Fill in the details (Name, Username, Password, Email, URL, Notes)
3. Click "Add Password"

### Managing Passwords

- **Copy**: Click 📋 to copy username or password
- **View**: Click 👁️ to show/hide passwords
- **Delete**: Click 🗑️ to remove a password
- **Export**: Go to 📊 Data Manager → Export as JSON
- **Import**: Go to 📊 Data Manager → Import from JSON

## Security Notes

⚠️ **Important Security Considerations:**

1. **Master Password**: Never share your master password
2. **Backups**: Export and store backups securely
3. **Browser**: Use trusted devices only
4. **HTTPS**: Always use HTTPS in production
5. **Environment Variables**: Keep your encryption keys secret

## File Structure

```
src/
├── app/
│   ├── api/
│   │   ├── auth/login/route.ts
│   │   └── passwords/
│   │       ├── add/route.ts
│   │       ├── list/route.ts
│   │       ├── delete/[id]/route.ts
│   │       ├── export/route.ts
│   │       └── import/route.ts
│   ├── layout.tsx
│   ├── page.tsx (Login)
│   └── dashboard/page.tsx
├── components/
│   ├── AddPasswordModal.tsx
│   ├── PasswordList.tsx
│   └── DataManager.tsx
├── lib/
│   └── store.ts (Zustand state management)
├── utils/
│   └── encryption.ts
├── types/
│   └── index.ts
└── styles/
    └── globals.css
```

## Technologies Used

- **Next.js 14** - React framework
- **TypeScript** - Type safety
- **Tailwind CSS** - Styling
- **Zustand** - State management
- **Node.js Crypto** - Encryption

## API Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/api/auth/login` | Authenticate with master password |
| POST | `/api/passwords/add` | Add new password |
| GET | `/api/passwords/list` | Get all passwords |
| DELETE | `/api/passwords/delete/[id]` | Delete password by ID |
| GET | `/api/passwords/export` | Export all passwords |
| POST | `/api/passwords/import` | Import passwords from JSON |

## Environment Variables

```env
# Master password hash (SHA-256)
NEXT_PUBLIC_MASTER_PASSWORD_HASH=

# Encryption secret key (min 32 chars)
ENCRYPTION_SECRET_KEY=

# Node environment
NODE_ENV=development
```

## Troubleshooting

### "Invalid password" error
- Make sure `NEXT_PUBLIC_MASTER_PASSWORD_HASH` is correct
- Generate hash again using the provided command

### Passwords not persisting
- Currently using in-memory storage
- For production, integrate with a database (PostgreSQL, MongoDB, etc.)

### Import fails
- Ensure JSON file is properly formatted
- File should be exported from this application

## Future Enhancements

- [ ] Database integration (PostgreSQL/MongoDB)
- [ ] User accounts with authentication
- [ ] Two-factor authentication
- [ ] Password strength indicator
- [ ] Password generator
- [ ] Categories/Tags for passwords
- [ ] Search functionality
- [ ] Mobile app (React Native)
- [ ] Browser extensions
- [ ] Encrypted cloud sync

## License

MIT

## Support

For issues and questions, please open an issue on GitHub.

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.
