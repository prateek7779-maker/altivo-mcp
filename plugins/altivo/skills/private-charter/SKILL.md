---
name: private-charter
description: Use when someone asks about private jet or helicopter charter, empty leg flights, private jet prices or flight times between cities, or wants a charter quote, in India, the US, the UK, Europe, the Middle East, Brazil, Canada or Mexico. Uses the Altivo Jets MCP tools.
---

# Private charter with Altivo Jets

1. **Empty legs first when the dates are flexible.** Call `search_empty_legs` with the route and passengers. Results are whole aircraft. Show the price, the estimated all-in figure and the departure window, and say the operator sets the departure time.
2. **Full charter for fixed plans.** Call `get_charter_estimate`. Show the recommended size first, the all-in range and the flight time. Say it is an estimate; the quote confirms the price.
3. **Hand off or request.** If the traveller wants a specific leg, give the `booking_handoff` link. If they want Altivo to contact them, confirm their name, email and optional phone, then call `request_quote` once.
4. **Never** present an estimate as a confirmed price or availability, never promise an operator by name for an empty leg, and never call `request_quote` without the traveller's consent.
