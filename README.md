# Math Match!

A multiplayer math game where players compete to solve math problems!

Adding a row to see if the branch will trigger a build.

## Setup Instructions

1. Clone this repository
2. Create a Supabase project at https://supabase.com
3. Get your Supabase URL and anon key from your project settings
4. Copy `config.template.js` to `config.js`
5. Fill in your Supabase credentials in `config.js`:
   ```javascript
   const config = {
       supabaseUrl: 'YOUR_SUPABASE_URL',
       supabaseKey: 'YOUR_SUPABASE_ANON_KEY'
   };
   ```
6. Set up your Supabase database with the following table:
   ```sql
   create table math_games (
       game_id text primary key,
       host_id text not null,
       status text not null,
       players jsonb not null,
       current_question jsonb,
       question_start_time timestamp with time zone,
       last_winner text,
       message text,
       round integer,
       max_rounds integer,
       created_at timestamp with time zone,
       question_answered_by jsonb
   );
   ```
7. Enable Row Level Security (RLS) and create appropriate policies for your table
8. Serve the files using a web server (e.g., using Python's `http.server` or Node's `http-server`)

## Deployment to GitHub Pages

1. Create a new GitHub repository
2. Push your code to the repository:
   ```bash
   git init
   git add .
   git commit -m "Initial commit"
   git branch -M main
   git remote add origin https://github.com/YOUR_USERNAME/YOUR_REPO_NAME.git
   git push -u origin main
   ```
3. Set up GitHub Pages:
   - Go to repository Settings
   - Navigate to "Pages" section
   - Under "Source", select "GitHub Actions"
4. Add repository secrets:
   - Go to repository Settings
   - Navigate to "Secrets and variables" → "Actions"
   - Add two secrets:
     - `SUPABASE_URL`: Your Supabase project URL
     - `SUPABASE_KEY`: Your Supabase anon key
5. The site will be automatically deployed to GitHub Pages
6. Your site will be available at: `https://YOUR_USERNAME.github.io/YOUR_REPO_NAME`

## Security Notes

- Never commit your `config.js` file to version control
- The `config.js` file is already added to `.gitignore`
- Use environment variables in production environments
- Consider implementing additional security measures like rate limiting

## Development

To run locally:
```bash
# Using Python
python -m http.server 8000

# Or using Node.js
npx http-server
```

Then open `http://localhost:8000` in your browser.

## License

MIT License 
