# Exercise 4: Defining familiar Concepts

*Deliverables: three concept specifications, with any subtleties explained in brief additional notes.*

1. URL Shortener

<div style="border: 1px solid #ccc; padding: 10px; background-color: #f9f9f9;">

**concept:** URLShortener  
**purpose:** create short, memorable URLs that redirect to longer destination URLs  
**principle:** a user provides a long URL and optionally a custom suffix; the system returns a short URL that maps to the original, and accessing the short URL redirects to the original

**states:**  
a set of Mappings with  
&nbsp;a shortCode String  
&nbsp;a longURL String  
&nbsp;a creator User  
&nbsp;a customFlag Boolean  

a counter AutoCodeCounter for generating unique random short codes  

**actions:**  

shorten(longURL: String, customCode: String?, user: User): (shortCode: String)  

&nbsp;**requires**  
&nbsp;&nbsp;&nbsp;&nbsp;customCode is either not provided or is not already in use  

&nbsp;**effects**  
&nbsp;&nbsp;&nbsp;&nbsp;if customCode is provided, create a mapping using it  
&nbsp;&nbsp;&nbsp;&nbsp;otherwise, generate a random code using AutoCodeCounter and create a new mapping  
&nbsp;&nbsp;&nbsp;&nbsp;return the new shortCode  

redirect(shortCode: String): (longURL: String)  

&nbsp;**requires**  
&nbsp;&nbsp;&nbsp;&nbsp;a mapping exists for the given shortCode  

&nbsp;**effects**  
&nbsp;&nbsp;&nbsp;&nbsp;returns the longURL associated with the shortCode  

delete(shortCode: String, user: User)  

&nbsp;**requires**  
&nbsp;&nbsp;&nbsp;&nbsp;a mapping exists for shortCode, and user is the creator  

&nbsp;**effects**  
&nbsp;&nbsp;&nbsp;&nbsp;removes the mapping  

**notes:**  
Short codes must be globally unique. The system may reject duplicate longURLs with the same customCode, but allows multiple short codes for the same longURL with different suffixes.

</div>



2. Conference Room Booking

<div style="border: 1px solid #ccc; padding: 10px; background-color: #f9f9f9;">

**concept:** RoomBookingSystem  
**purpose:** allow users to book and manage reservations for shared conference rooms without overlap or conflicts  
**principle:** each room maintains a schedule of non-overlapping reservations; a new booking can only be added if it does not conflict with any existing bookings

**states:**  
a set of Rooms with  
&nbsp;a roomID String  
&nbsp;a schedule List of Bookings  

a Booking with  
&nbsp;a roomID String  
&nbsp;a startTime DateTime  
&nbsp;a endTime DateTime  
&nbsp;a user User  

**actions:**  
book(roomID: String, start: DateTime, end: DateTime, user: User): (booking: Booking)  

&nbsp;**requires**  
&nbsp;&nbsp;&nbsp;&nbsp;room exists, no conflicting booking in the interval  

&nbsp;**effects**  
&nbsp;&nbsp;&nbsp;&nbsp;adds booking to room’s schedule  

cancel(booking: Booking, user: User)  

&nbsp;**requires**  
&nbsp;&nbsp;&nbsp;&nbsp;booking exists and belongs to user  

&nbsp;**effects**  
&nbsp;&nbsp;&nbsp;&nbsp;removes booking from schedule  

getAvailability(start: DateTime, end: DateTime): (availableRooms: Set<Room>)  

&nbsp;**requires**  
&nbsp;&nbsp;&nbsp;&nbsp;start < end  

&nbsp;**effects**  
&nbsp;&nbsp;&nbsp;&nbsp;returns rooms that are free in the interval  

**notes:**  
Overlap detection must be atomic to prevent race conditions in concurrent booking scenarios. Bookings are assumed to be in the future (i.e., cannot book dates/times in the past).

</div>



3.  Electronic Boarding Pass

<div style="border: 1px solid #ccc; padding: 10px; background-color: #f9f9f9;">

**concept:** ElectronicBoardingPass  
**purpose:** provide passengers with an up-to-date, scannable digital credential for boarding a flight, reflecting real-time flight information  
**principle:** a boarding pass is tied to a passenger and flight, includes necessary metadata like seat and gate, and reflects live updates from backend flight data

**states:**  
a set of BoardingPasses with  
&nbsp;a passengerID String  
&nbsp;a flightID String  
&nbsp;a seat String  
&nbsp;a issuedAt DateTime  

a set of Flights with  
&nbsp;a flightID String  
&nbsp;a gate String  
&nbsp;a departureTime DateTime  
&nbsp;a status Enum {scheduled, delayed, boarding, departed, canceled}  

**actions:**  

issueBoardingPass(passengerID: String, flightID: String, seat: String): (pass: BoardingPass)  

&nbsp;**requires**  
&nbsp;&nbsp;&nbsp;&nbsp;flight exists, status is scheduled or delayed  

&nbsp;**effects**  
&nbsp;&nbsp;&nbsp;&nbsp;creates a new boarding pass with given passenger and seat, tied to the specified flight with flightID

updateFlight(flightID: String, gate?: String, departureTime?: DateTime, status?: Status)  

&nbsp;**requires**  
&nbsp;&nbsp;&nbsp;&nbsp;flight exists and proposed updates represent a valid status transition (e.g. not from departed to delayed), and departureTime is in the future if updated  

&nbsp;**effects**  
&nbsp;&nbsp;&nbsp;&nbsp;updates the flight’s gate, time, and/or status; all linked boarding passes (passes with the same flightID) reflect these updates automatically  

scanPass(passengerID: String, flightID: String): (valid: Boolean)  

&nbsp;**requires**  
&nbsp;&nbsp;&nbsp;&nbsp;a boarding pass exists for the passenger and flight; flight status is boarding  

&nbsp;**effects**  
&nbsp;&nbsp;&nbsp;&nbsp;returns True if the boarding pass is valid for entry (i.e. flight is boarding, not canceled or departed)  

**notes:**  
Live updates to flight info must be propagated to all issued boarding passes in real time. Status transitions must follow valid state progressions, such as scheduled → delayed → boarding → departed. The system should prevent nonsensical backward transitions like departed → scheduled.

</div>

---

<div align="center">
  <a href="./exercise3.md">⬅️ Go to Exercise 3</a>&emsp;&emsp;&emsp;
</div>

<div align="center" style="margin-top: 1em;">
  <a href="../pset1.md">🏠 Go to Pset 1 Table of Contents</a>
</div>
