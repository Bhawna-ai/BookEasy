# BookEasy 🎯

A comprehensive booking platform for restaurants, spas, gyms, and salons. Built with Node.js, Express, MongoDB, and vanilla JavaScript.

## Features ✨

- **Secure Booking System**: Users can book appointments at various businesses
- **Multiple Service Types**: Support for restaurants, spas, gyms, and salons
- **Real-time Validation**: Form validation with instant feedback
- **Booking Management**: Users can view their booking history by email
- **Responsive Design**: Works seamlessly on desktop, tablet, and mobile
- **MongoDB Integration**: Secure data storage with MongoDB Atlas
- **RESTful API**: Clean API architecture for easy integration

## Technologies Used 🛠️

- **Backend**: Node.js, Express.js (ES6 Modules)
- **Database**: MongoDB with Mongoose ODM
- **Frontend**: HTML5, CSS3, Vanilla JavaScript
- **Other**: dotenv, CORS

## Project Structure 📁

```
BookEasy/
├── client/
│   ├── booking.html       # Client booking page
│   ├── booking.css        # Booking page styles
│   └── booking.js         # Booking page logic
├── models/
│   └── Booking.js         # Mongoose booking model
├── admin/                 # Admin panel (future)
├── server.js              # Express server with API routes
├── package.json           # Dependencies
├── .env                   # Environment variables
├── .gitignore            # Git ignore rules
├── index.html            # Landing page
├── style.css             # Landing page styles
└── README.md             # This file
```

## Installation & Setup 🚀

### Prerequisites
- Node.js (v14 or higher)
- MongoDB Atlas account or local MongoDB installation
- npm or yarn

### Steps

1. **Clone the repository**
```bash
git clone <repository-url>
cd BookEasy
```

2. **Install dependencies**
```bash
npm install
```

3. **Configure environment variables**
   - The `.env` file is already configured with MongoDB connection string
   - Update `MONGO_URI` if needed:
```env
MONGO_URI=your_mongodb_connection_string
PORT=3000
```

4. **Start the server**
```bash
# Production
npm start

# Development (with nodemon)
npm run dev
```

5. **Access the application**
   - Main website: http://localhost:3000
   - Booking page: http://localhost:3000/client/booking.html
   - API health check: http://localhost:3000/api/health

## API Endpoints 📡

### Bookings

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/bookings` | Get all bookings |
| GET | `/api/bookings/:id` | Get booking by ID |
| GET | `/api/bookings/customer/:email` | Get bookings by customer email |
| POST | `/api/bookings` | Create new booking |
| PATCH | `/api/bookings/:id/status` | Update booking status |
| DELETE | `/api/bookings/:id` | Delete booking |
| GET | `/api/health` | Health check |

### Create Booking Example

```javascript
POST /api/bookings
Content-Type: application/json

{
  "customerName": "John Doe",
  "customerEmail": "john@example.com",
  "customerPhone": "(555) 123-4567",
  "serviceType": "restaurant",
  "businessName": "The Gourmet Kitchen",
  "businessLocation": "Downtown Plaza",
  "serviceDetails": "Dinner reservation",
  "bookingDate": "2025-11-15",
  "bookingTime": "19:00",
  "numberOfGuests": 4,
  "specialRequests": "Window seat preferred"
}
```

## Database Schema 💾

### Booking Model

```javascript
{
  customerName: String (required),
  customerEmail: String (required, validated),
  customerPhone: String (required),
  serviceType: String (enum: restaurant, spa, gym, salon),
  businessName: String (required),
  businessLocation: String,
  serviceDetails: String,
  bookingDate: Date (required),
  bookingTime: String (required),
  numberOfGuests: Number (default: 1),
  specialRequests: String,
  status: String (enum: pending, confirmed, cancelled, completed),
  bookingReference: String (auto-generated, unique),
  timestamps: true (createdAt, updatedAt)
}
```

## Features in Detail 🎨

### Client Booking Page
- Beautiful two-panel layout with information panel and booking form
- Real-time form validation
- Auto-populated business options based on service type
- Phone number formatting
- Date/time picker with validation
- Special requests textarea
- Terms and conditions checkbox
- Success modal with booking reference
- "Check My Bookings" feature to view booking history

### Security Features
- CORS enabled for secure cross-origin requests
- Input validation on both client and server
- Email format validation
- MongoDB injection prevention with Mongoose
- Environment variables for sensitive data

### Responsive Design
- Mobile-first approach
- Breakpoints for tablet and desktop
- Touch-friendly interface
- Optimized for all screen sizes

## Usage Guide 📖

### For Customers

1. **Browse Services**: Visit the homepage and explore different service categories
2. **Select Business**: Click "Book Now" on any featured business or "Explore" on service cards
3. **Fill Booking Form**: Complete the booking form with your details
4. **Submit**: Review and submit your booking
5. **Confirmation**: Receive booking reference and email confirmation
6. **Check Bookings**: Use "Check My Bookings" to view all your bookings

### For Businesses (Coming Soon)
- Business dashboard for managing bookings
- Real-time booking notifications
- Customer management
- Analytics and reporting

## Future Enhancements 🔮

- [ ] Business admin dashboard
- [ ] Payment integration
- [ ] Email notifications
- [ ] SMS reminders
- [ ] Calendar integration
- [ ] Reviews and ratings
- [ ] Advanced search and filters
- [ ] Multi-language support
- [ ] Mobile app

## Contributing 🤝

Contributions are welcome! Please feel free to submit a Pull Request.

## License 📄

ISC License

## Support 💬

For support, email support@bookeasy.com or open an issue in the repository.

---

Built with ❤️ by the BookEasy Team