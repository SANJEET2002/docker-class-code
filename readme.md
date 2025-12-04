# 1. Activate your virtual environment (you already have one in env/)
source env/bin/activate

# 2. Install dependencies (if not already installed)
pip install -r requirements.txt

# 3. Set Flask environment variables
export FLASK_APP=app.py
export FLASK_ENV=development  # Optional: enables debug mode

# 4. Run the Flask app
flask run