# COPOM Minutes Scraper

This project is a Python web scraping application to extract and process the minutes of the COPOM (Monetary Policy Committee of the Central Bank of Brazil) meetings.

## Features

- Extracts data from both old and new COPOM meeting minutes.
- Processes both HTML and PDF content.
- Saves the extracted texts in an output file.

## Project Structure

- **`fetch_json(url: str) -> dict`**: Sends a GET request to the provided URL and returns the JSON.
- **`extract_data(json_data: dict, link_key: str) -> pd.DataFrame`**: Normalizes the JSON content and extracts specific columns.
- **`get_copom_data() -> pd.DataFrame`**: Combines data from both old and new minutes APIs into a single DataFrame.
- **`fetch_html_content(link: str, base_url: str = "https://www.bcb.gov.br") -> str`**: Extracts and processes the HTML content of old minutes.
- **`fetch_pdf_content(link: str, base_url: str = "https://www.bcb.gov.br") -> str`**: Sends a GET request to the "PDF" URL and processes the content.
- **`fetch_content(row)`**: Determines the content type (PDF or HTML) and calls the appropriate function to extract the text.
- **`process_atas() -> pd.DataFrame`**: Processes the minutes and extracts the complete content for each one.
- **`parcial(text: str) -> str`**: Extracts portions of the text for preview.
- **`main()`**: Executes the complete process and saves the result in an output file.

## Requirements

- Python 3.8+
- Install the required Python libraries listed in `requirements.txt`

## How to Use

1. Clone the repository:

   ```bash
   git clone https://github.com/your-username/copom-minutes-scraper.git
   cd copom-minutes-scraper
   ```

2. Create and activate a virtual environment:

   ```bash
   python -m venv venv
   source venv/bin/activate  # Linux/Mac
   venv\Scripts\activate  # Windows
   ```

3. Install the dependencies:

   ```bash
   pip install -r requirements.txt
   ```

4. Run the script:
   ```bash
   python main.py
   ```

## Output

The script generates a file `df_atas.fst` in the `assets` folder, containing the processed COPOM meeting minutes.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
