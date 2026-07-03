# AI-TRAVEL-BOOKING-AGENT

# AI Travel Booking Agent

A multi-step travel booking agent built with **LangGraph** and **Gemini 2.5 Flash**.
It reads a plain-text customer email, extracts the trip request, searches for
flights and hotels, picks the best option under the customer's budget and
preferences, and generates a booking confirmation.

## How it works

The agent is a LangGraph state machine with six nodes:

1. **parse_request** — LLM extracts source, destination, dates, passengers,
   budget, and preferred airline from the raw email.
2. **flight_search** — searches for available flights (currently mocked;
   swap in a real flight API here).
3. **best_flight** — picks the best flight within budget, preferring the
   customer's preferred airline when possible.
4. **hotel_search** — searches for available hotels (currently mocked).
5. **best_hotel** — picks the best hotel by rating-per-price value.
6. **booking_manager** — LLM generates a friendly booking confirmation,
   including any warnings (e.g. budget or airline preference not met).

## Setup

```bash
pip install -r requirements.txt
cp .env.example .env   # add your Google API key
```

## Usage

Open `notebooks/travel_booking_agent.ipynb` and run all cells. The email
text and trip details can be edited directly in the notebook.

## Example

**Input:** an email requesting a Pune → Delhi round trip for 2 passengers,
₹7,000/passenger budget, IndiGo preferred.

**Output:** a booking confirmation with the selected flight, hotel, and
total estimated cost.

## Notes / limitations

- Flight and hotel search are mocked with static sample data — no real
  booking API is connected yet.
- Requires a `GOOGLE_API_KEY` (Gemini) to run the LLM steps.
- This is a demo/learning project, not a production booking system.

