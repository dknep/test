# Navigate to the project directory
cd /home/ubuntu/1792024-git-excluding-specific-files-and-directories

# Add the .env file and cache/ directory to .gitignore
echo ".env" >> .gitignore
echo "cache/" >> .gitignore

# Remove them from Git tracking (but keep them in the filesystem)
git rm --cached .env
git rm -r --cached cache/

# Commit the changes
git add .gitignore
git commit -m "Exclude .env and cache/ from tracking"

# Push the changes (if required)
git push origin main  # Change 'main' to the correct branch if needed
