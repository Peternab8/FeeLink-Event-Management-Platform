# Product decisions and workflows

## The two jobs of the platform

**Public side:** explain who the organization is, show what it has done, and help visitors discover and book upcoming activities.  
**Operations side:** help the team set up, sell, operate, review, and report on events.

This matters because the organization's identity is a first-class experience—not a ticket checkout disguised as a homepage.

## Booking models

1. **Reserved seating:** a visitor selects numbered seats from a hall layout; seats have distinct inventory and booking states.
2. **General admission:** a visitor books from an overall event capacity rather than picking a specific seat.

These modes affect data modeling, customer UX, validation, and operational reporting. Some implementation and testing remains open.

## Booking and payment states

The private architecture documentation distinguishes states including `available`, `held`, `pending`, `payment_review`, `booked`, and `cancelled`. These are **server/data concepts**, not an assurance that every UI screen or transition is currently production-perfect.

Key intent:
- Selecting a seat on screen does not itself guarantee a hold; reservation must be authorized by the backend.
- Payment is currently made outside the app and reviewed by staff.
- A pending booking should not be represented as a paid, confirmed ticket.
- Staff actions such as approval and check-in must be permission-checked and auditable.

## Operational views

The product has separate screen families for the event owner, sales/booking operators, scanner/check-in staff, and other staff. It aims to expose only the actions allowed by the relevant authority. The permissions model is nontrivial and still has known verification/cutover work in the private roadmap.

## Product decisions I considered

- **Organization first:** a public presence that can present past work and activities, not just a ticket form.
- **Two booking experiences:** avoid forcing numbered seating onto every type of event.
- **Truthful states:** show payment-review status explicitly and avoid fake confirmations.
- **Explicit operations:** separate day-of-event work, reports, activity history, and permission review.
- **Commercial boundaries:** keep the full internal codebase private while sharing a truthful public case study.

## Development method

I use Codex and Claude Code for implementation and iteration, with the product requirements, workflows, feedback, and priorities directed by me. The case study focuses on those contributions while making the AI-assisted nature of the development explicit.
