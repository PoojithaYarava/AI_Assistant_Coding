# Privacy in API Usage - Weather Data Fetcher

This project demonstrates secure API key management by fetching weather data without exposing sensitive credentials in the code.

## Security Best Practices Implemented

1. **Environment Variables**: API keys are stored in `.env` file, not hardcoded
2. **File Gitignore**: `.env` file should never be committed to version control
3. **Error Handling**: Secure error messages that don't expose sensitive data
4. **Type Hints**: Clear function signatures for maintainability
5. **Documentation**: Comments explaining security considerations

## Setup Instructions

### 1. Install Dependencies
```bash
pip install -r requirements.txt
```

### 2. Create .env File
Copy `.env.example` to `.env`:
```bash
cp .env.example .env
```

### 3. Add Your API Key
- Get a free API key from [OpenWeatherMap](https://openweathermap.org/api)
- Open `.env` and replace `your_openweathermap_api_key_here` with your actual key

### 4. Run the Script
```bash
python 10_2.py
```

## File Structure
```
├── 10_2.py              # Main script with SecureWeatherFetcher class
├── requirements.txt     # Python dependencies
├── .env.example        # Template for environment variables
├── .env                # Your actual credentials (DO NOT COMMIT)
└── .gitignore          # Should include .env
```

## Key Security Features

### Secure API Key Management
```python
# ✅ GOOD - Use environment variables
api_key = os.getenv('WEATHER_API_KEY')

# ❌ BAD - Never hardcode API keys
api_key = "your-api-key-123"  # INSECURE!
```

### Error Handling Without Exposing Secrets
```python
# ✅ GOOD - Generic error message
raise ValueError("WEATHER_API_KEY not found in environment variables")

# ❌ BAD - Exposes the key in error message
raise ValueError(f"Invalid API key: {api_key}")
```

## What NOT to Do

❌ Never commit `.env` files to version control
❌ Never log or print API keys
❌ Never share credentials in code comments
❌ Never hard-code sensitive data

## What TO Do

✅ Use environment variables
✅ Use `.env` with `python-dotenv`
✅ Add `.env` to `.gitignore`
✅ Use `.env.example` as a template
✅ Document required environment variables
✅ Use secure configuration management in production

## Additional Resources

- [python-dotenv Documentation](https://python-dotenv.readthedocs.io/)
- [OpenWeatherMap API](https://openweathermap.org/api)
- [OWASP: Sensitive Data Exposure](https://owasp.org/www-project-top-ten/)
- [12-Factor App: Config Management](https://12factor.net/config)
