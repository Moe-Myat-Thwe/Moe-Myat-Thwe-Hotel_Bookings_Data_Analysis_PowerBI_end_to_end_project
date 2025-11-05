# 🏨 Hotel Booking Dashboard (Power BI)
##  📊 Analysis of 2015–2017 Bookings for City & Resort Hotels

 This Power BI dashboard provides an interactive analysis of hotel booking data from 2015 to 2017, covering City Hotel and Resort Hotel performance. It highlights booking trends, customer behavior, and key performance metrics to support data-driven decisions.

## 🔍 Key Insights

- Total Bookings: 330 across both hotels
- Cancellation Rate: 35.45% (a major concern area)
- Repeated Guests: 3.03% — relatively low, indicating weak customer retention
- Average Daily Rate (ADR): $86.56
- Average Length of Stay: 3.72 nights
- Total Revenue: $109.31K

## 📅 Monthly & Segment Trends

- Peak Month: Resort Hotels shows the highest bookings in July and ADR in August.
- Top Country: Portugal (PRT) dominates bookings, followed by the UK (GBR).
- Top Market Segment: Offline TA/TO (Travel Agents/Tour Operators) leads with 177 bookings.
- Cancellation by Segment: Aviation and Groups segments have the highest cancellation rates.
- Special Requests: Customers with 1–2 requests have higher cancellation rates.

## 📈 Dashboard Features

- Interactive Year Slicer: Filter data by 2015, 2016, or 2017
- Hotel Filter: Toggle between City and Resort Hotel
- Market Segment Filter: View performance by booking segment
- Dynamic KPIs: Automatically update key metrics with filters
- Visual Variety: Line charts, bar charts, column charts and donut chart for comprehensive analysis

## 🧰 Tools & Techniques

- Tool: Power BI Desktop
- Data Source: Hotel Booking Dataset (2015–2017) from Kaggle: 
  https://www.kaggle.com/datasets/mojtaba142/hotel-booking

- Data Cleaning & Transformation: Power Query Editor
- DAX Measures:
  - Cancellation Rate = DIVIDE(
    CALCULATE(COUNTROWS('hotel_booking'), 'hotel_booking'[is_canceled] = 1),
    COUNTROWS('hotel_booking'))
  - Total Revenue = SUMX(
    'hotel_booking',
    'hotel_booking'[adr] * 
    ('hotel_booking'[stays_in_week_nights] + 'hotel_booking'[stays_in_weekend_nights]))
  - Repeated Guest % = DIVIDE(SUM(hotel_booking[is_repeated_guest]), COUNTROWS('hotel_booking'))
  - arrival_date = DATE(
    'hotel_booking'[arrival_date_year],
    SWITCH(
        'hotel_booking'[arrival_date_month],
        "January", 1,
        "February", 2,
        "March", 3,
        "April", 4,
        "May", 5,
        "June", 6,
        "July", 7,
        "August", 8,
        "September", 9,
        "October", 10,
        "November", 11,
        "December", 12
    ),
    'hotel_booking'[arrival_date_day_of_month])

## 🗂️ Files in Repository
- hotel_booking_dashboard.pbix	(Power BI dashboard file)
- hotel_booking_data.csv	(Raw dataset used for analysis)
- Dashboard_Screenshot.png	(Preview of the dashboard)
- README.md	Documentation of project details

## 💡 Future Improvements
- Add forecasting for booking trends
- Include customer demographics and satisfaction analysis
- Build predictive model for cancellation likelihood



