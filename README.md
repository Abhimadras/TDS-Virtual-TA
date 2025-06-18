# TDS-Virtual-TA




# TDS Virtual Teaching Assistant

![FastAPI](https://img.shields.io/badge/FastAPI-005571?style=for-the-badge&logo=fastapi)
![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54)
![Render](https://img.shields.io/badge/Render-%46E3B7.svg?style=for-the-badge&logo=render&logoColor=white)

An AI-powered virtual teaching assistant for IIT Madras's Online Degree in Data Science program that automatically answers student questions based on course content and forum discussions.

## Features

-  **FastAPI backend** with RESTful API endpoints
-  **LLM-powered responses** using Groq's LLaMA3 model
-  **Smart forum search** to find relevant discussion threads
-  **Course-aware responses** based on Tools in Data Science content
-  **Quick response times** (<30 seconds)
-  **CORS-enabled** for web integration

## API Endpoints

### Main Endpoint
- `POST /api/` - Submit a student question and get an AI-generated response

```json
{
  "question": "Which AI model should I use for GA5?",
  "image": null
}
```

Example response:
```json
{
  "answer": "For assignment GA5, you must use gpt-3.5-turbo-0125 as specified in the course requirements...",
  "links": [
    {
      "url": "https://discourse.onlinedegree.iitm.ac.in/t/ga5-model-requirements/12345",
      "text": "GA5 Model Requirements (see post #4)"
    }
  ]
}

### Other Endpoints
- `GET /` - API status and documentation
- `GET /debug_match` - Debug endpoint for testing question matching

## Setup and Deployment

### Prerequisites
- Python 3.9+
- Groq API key (set as `GROQ_API_KEY` environment variable)

### Installation
1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/tds-virtual-ta.git
   cd tds-virtual-ta
   ```

2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

3. Set up environment variables:
   ```bash
   echo "GROQ_API_KEY=your_api_key_here" > .env
   ```

### Running Locally
```bash
uvicorn main:app --reload
```

The API will be available at `http://localhost:8000`

### Deployment
The application can be deployed to any cloud platform supporting Python (Render, Heroku, etc.). 

Example Render.com configuration:
- Runtime: Python 3
- Build Command: `pip install -r requirements.txt`
- Start Command: `uvicorn main:app --host 0.0.0.0 --port $PORT`

## Data Sources
The system uses two main data sources:
1. **Course Content**: Scraped from IITM's TDS course materials
2. **Forum Discussions**: From the IITM Discourse platform (Jan-Apr 2025)

To update the data:
```bash
python scraper.py
```

## Evaluation
Test the API using the provided promptfoo configuration:
```bash
npx -y promptfoo eval --config project-tds-virtual-ta-promptfoo.yaml
```

## Project Structure
```
tds-virtual-ta/
├── main.py            # FastAPI application
├── scraper.py         # Data scraping script
├── data.json          # Course and forum data
├── requirements.txt   # Python dependencies
├── promptfoo.yaml     # Evaluation configuration
└── README.md          # This file
```

## License
MIT License - See [LICENSE](LICENSE) for details.

## Acknowledgments
- IIT Madras Online Degree Program
- Groq for the LLM API
- FastAPI for the web framework
```

This README includes:
1. Project overview with badges
2. Key features
3. API documentation
4. Setup and deployment instructions
5. Data source information
6. Evaluation instructions
7. Project structure
8. License information
9. Acknowledgments

You can customize it further by:
- Adding screenshots of example responses
- Including more detailed deployment instructions for your specific hosting platform
- Adding contribution guidelines if you want others to contribute
- Including known limitations or future improvements
