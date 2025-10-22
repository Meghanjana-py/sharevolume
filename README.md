# SEC Entity Shares Viewer Application

This is a single-page web application designed to fetch and display the maximum and minimum outstanding common stock shares for a given SEC Central Index Key (CIK).

## Features

-   **Dynamic Data Fetching**: Retrieves `EntityCommonStockSharesOutstanding` data from the SEC EDGAR API.
-   **CIK Support**: Defaults to Bank of America (BAC, CIK 0000070858) but can accept any 10-digit CIK via URL parameter.
-   **Data Filtering**: Filters share data to include only entries after the fiscal year 2020 with valid numeric values.
-   **Max/Min Identification**: Clearly displays the highest and lowest outstanding share values and their corresponding fiscal years.
-   **Responsive Design**: Utilizes Tailwind CSS for a fully responsive and modern user interface, adapting to various screen sizes.
-   **No Page Reload**: Updates content dynamically without a full page reload when a CIK is changed via the URL.
-   **Error Handling**: Provides a user-friendly message if data fetching or processing fails.

## Technologies Used

-   **HTML5**: Structure of the web page.
-   **Tailwind CSS**: Utility-first CSS framework for styling and responsiveness.
-   **JavaScript (ES6+)**: For fetching data, processing, and dynamically updating the DOM.
-   **SEC EDGAR API**: Data source for company financial information.
-   **AllOrigins Proxy**: Used to bypass potential Cross-Origin Resource Sharing (CORS) restrictions when fetching data from the SEC API from a client-side application.

## How to Run

To run this application, simply open the `index.html` file in your web browser.

```bash
# No server needed for basic functionality
open index.html
```

### Using a Custom CIK

You can specify a different CIK by adding a `?CIK=` query parameter to the URL.

**Example: Viewing data for Apple Inc. (CIK 0000320193)**

```
file:///path/to/your/index.html?CIK=0000320193
```

If you deploy this application to a web server, the URL would look like:

```
https://your-domain.com/index.html?CIK=0000320193
```

### User-Agent

As per SEC guidance, a descriptive `User-Agent` header is included in the fetch requests. Please note that modern browsers may restrict client-side JavaScript from setting arbitrary `User-Agent` headers directly. The `allorigins.win` proxy used in this application might handle or pass on the `User-Agent` to the SEC API.

## Project Structure

-   `index.html`: The main and only HTML file containing all the application's code (HTML, CSS via Tailwind CDN, JavaScript).
-   `README.md`: This file.
-   `LICENSE`: The MIT License for the project.
-   `uid.txt`: An additional context file provided in the project root, not directly used by the web application logic.

## Development Notes

-   The application uses a public proxy (`https://api.allorigins.win/raw?url=`) for fetching SEC data. While convenient for client-side development, for production environments, it is generally recommended to implement a custom server-side proxy to have full control over requests, including `User-Agent` and error handling.
-   The `data.json` structure mentioned in the requirements is conceptually generated and used internally by the JavaScript logic to determine the `max` and `min` share values for display, rather than being saved as an actual file.

