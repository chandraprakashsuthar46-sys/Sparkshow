<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ShowSpark - Book Movie Tickets</title>
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Poppins', sans-serif;
            background-color: #f5f7fa;
            color: #333;
            line-height: 1.6;
        }

        .container {
            width: 100%;
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 15px;
        }

        /* Header Styles */
        header {
            background-color: #032541;
            padding: 15px 0;
            position: sticky;
            top: 0;
            z-index: 100;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
        }

        .header-content {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .logo {
            display: flex;
            align-items: center;
        }

        .logo span {
            font-size: 28px;
            font-weight: 700;
            color: #fff;
            margin-left: 10px;
        }

        .logo-icon {
            background: linear-gradient(135deg, #8e2de2, #4a00e0);
            width: 40px;
            height: 40px;
            border-radius: 8px;
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-size: 24px;
        }

        nav ul {
            display: flex;
            list-style: none;
        }

        nav ul li {
            margin-left: 25px;
        }

        nav ul li a {
            color: #fff;
            text-decoration: none;
            font-weight: 500;
            transition: color 0.3s;
        }

        nav ul li a:hover {
            color: #01b4e4;
        }

        .auth-buttons button {
            background-color: #01b4e4;
            color: white;
            border: none;
            padding: 8px 16px;
            border-radius: 20px;
            font-weight: 500;
            cursor: pointer;
            transition: background-color 0.3s;
        }

        .auth-buttons button:hover {
            background-color: #0099c3;
        }

        /* Hero Section */
        .hero {
            background: linear-gradient(rgba(0, 0, 0, 0.7), rgba(0, 0, 0, 0.7)), url('https://storage.googleapis.com/workspace-0f70711f-8b4e-4d94-86f1-2a93ccde5887/image/6e9e5f21-cea8-4e05-b564-9081e94e03a5.png') no-repeat center center/cover;
            color: white;
            padding: 80px 0;
            text-align: center;
            margin-bottom: 30px;
        }

        .hero h1 {
            font-size: 48px;
            margin-bottom: 20px;
        }

        .hero p {
            font-size: 18px;
            max-width: 700px;
            margin: 0 auto 30px;
        }

        .search-box {
            display: flex;
            max-width: 600px;
            margin: 0 auto;
        }

        .search-box input {
            flex: 1;
            padding: 12px 20px;
            border: none;
            border-radius: 30px 0 0 30px;
            font-size: 16px;
        }

        .search-box button {
            background: #01b4e4;
            color: white;
            border: none;
            padding: 12px 24px;
            border-radius: 0 30px 30px 0;
            cursor: pointer;
            font-weight: 500;
        }

        /* Filters */
        .filters {
            display: flex;
            justify-content: center;
            gap: 15px;
            margin-bottom: 30px;
            flex-wrap: wrap;
        }

        .filter-btn {
            background: white;
            border: 1px solid #ddd;
            padding: 8px 20px;
            border-radius: 20px;
            cursor: pointer;
            transition: all 0.3s;
        }

        .filter-btn:hover, .filter-btn.active {
            background: #01b4e4;
            color: white;
            border-color: #01b4e4;
        }

        /* Movies Grid */
        .movies-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(220px, 1fr));
            gap: 25px;
            margin-bottom: 40px;
        }

        .movie-card {
            background: white;
            border-radius: 10px;
            overflow: hidden;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
            transition: transform 0.3s;
        }

        .movie-card:hover {
            transform: translateY(-5px);
        }

        .movie-poster {
            height: 330px;
            width: 100%;
            object-fit: cover;
        }

        .movie-info {
            padding: 15px;
        }

        .movie-title {
            font-size: 18px;
            font-weight: 600;
            margin-bottom: 8px;
            white-space: nowrap;
            overflow: hidden;
            text-overflow: ellipsis;
        }

        .movie-details {
            display: flex;
            justify-content: space-between;
            color: #666;
            font-size: 14px;
            margin-bottom: 12px;
        }

        .movie-rating {
            color: #f5c518;
            font-weight: 500;
        }

        .book-btn {
            width: 100%;
            background: #032541;
            color: white;
            border: none;
            padding: 10px;
            border-radius: 5px;
            cursor: pointer;
            font-weight: 500;
            transition: background 0.3s;
        }

        .book-btn:hover {
            background: #01b4e4;
        }

        /* Booking Section */
        .booking-section {
            background: white;
            border-radius: 10px;
            padding: 25px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
            margin-bottom: 30px;
            display: none;
        }

        .booking-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 20px;
        }

        .booking-title {
            font-size: 24px;
            font-weight: 600;
        }

        .close-booking {
            background: #ff4d4d;
            color: white;
            width: 30px;
            height: 30px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            cursor: pointer;
        }

        .booking-details {
            display: grid;
            grid-template-columns: 1fr 2fr;
            gap: 20px;
        }

        .booking-poster {
            width: 100%;
            border-radius: 10px;
        }

        .booking-form {
            display: grid;
            gap: 15px;
        }

        .form-group {
            display: flex;
            flex-direction: column;
        }

        .form-group label {
            font-weight: 500;
            margin-bottom: 5px;
        }

        .form-group select, .form-group input {
            padding: 10px;
            border: 1px solid #ddd;
            border-radius: 5px;
        }

        .seats-grid {
            display: grid;
            grid-template-columns: repeat(10, 1fr);
            gap: 8px;
            margin: 15px 0;
        }

        .seat {
            width: 30px;
            height: 30px;
            background: #e4e4e4;
            border-radius: 5px;
            display: flex;
            align-items: center;
            justify-content: center;
            cursor: pointer;
            font-size: 12px;
        }

        .seat.selected {
            background: #5cb85c;
            color: white;
        }

        .seat.occupied {
            background: #d9534f;
            color: white;
            cursor: not-allowed;
        }

        .confirm-btn {
            background: #032541;
            color: white;
            border: none;
            padding: 12px;
            border-radius: 5px;
            cursor: pointer;
            font-weight: 500;
            margin-top: 15px;
            transition: background 0.3s;
        }

        .confirm-btn:hover {
            background: #01b4e4;
        }

        /* Tickets Section */
        .tickets-section {
            background: white;
            border-radius: 10px;
            padding: 25px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
            margin-bottom: 30px;
            display: none;
        }

        .ticket {
            background: linear-gradient(to right, #8e2de2, #4a00e0);
            color: white;
            border-radius: 10px;
            padding: 20px;
            margin-bottom: 15px;
            position: relative;
            overflow: hidden;
        }

        .ticket::before {
            content: '';
            position: absolute;
            height: 100%;
            width: 20px;
            background: #f5f7fa;
            top: 0;
            left: 70px;
            border-radius: 0 10px 10px 0;
        }

        .ticket-info {
            display: grid;
            grid-template-columns: 70px 1fr;
            gap: 20px;
        }

        .ticket-poster {
            width: 70px;
            height: 100px;
            object-fit: cover;
            border-radius: 5px;
        }

        .ticket-details h3 {
            font-size: 18px;
            margin-bottom: 10px;
        }

        .ticket-details p {
            margin-bottom: 5px;
            font-size: 14px;
        }

        /* Footer */
        footer {
            background: #032541;
            color: white;
            padding: 40px 0;
        }

        .footer-content {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 30px;
        }

        .footer-section h3 {
            font-size: 18px;
            margin-bottom: 20px;
            position: relative;
        }

        .footer-section h3::after {
            content: '';
            position: absolute;
            bottom: -8px;
            left: 0;
            width: 40px;
            height: 3px;
            background: #01b4e4;
        }

        .footer-section ul {
            list-style: none;
        }

        .footer-section ul li {
            margin-bottom: 10px;
        }

        .footer-section ul li a {
            color: #ccc;
            text-decoration: none;
            transition: color 0.3s;
        }

        .footer-section ul li a:hover {
            color: #01b4e4;
        }

        .social-links {
            display: flex;
            gap: 15px;
            margin-top: 15px;
        }

        .social-links a {
            color: white;
            font-size: 20px;
            transition: color 0.3s;
        }

        .social-links a:hover {
            color: #01b4e4;
        }

        .copyright {
            text-align: center;
            margin-top: 40px;
            padding-top: 20px;
            border-top: 1px solid #1a3c5d;
            color: #ccc;
        }

        /* Responsive Design */
        @media (max-width: 992px) {
            .footer-content {
                grid-template-columns: repeat(2, 1fr);
            }
            
            .booking-details {
                grid-template-columns: 1fr;
            }
        }

        @media (max-width: 768px) {
            .header-content {
                flex-direction: column;
                gap: 15px;
            }
            
            nav ul {
                gap: 15px;
                flex-wrap: wrap;
                justify-content: center;
            }
            
            .hero h1 {
                font-size: 36px;
            }
            
            .movies-grid {
                grid-template-columns: repeat(auto-fill, minmax(170px, 1fr));
            }
        }

        @media (max-width: 576px) {
            .footer-content {
                grid-template-columns: 1fr;
            }
            
            .movie-poster {
                height: 280px;
            }
            
            .seats-grid {
                grid-template-columns: repeat(5, 1fr);
            }
        }
    </style>
</head>
<body>
    <!-- Header -->
    <header>
        <div class="container header-content">
            <div class="logo">
                <div class="logo-icon"><i class="fas fa-ticket-alt"></i></div>
                <span>ShowSpark</span>
            </div>
            <nav>
                <ul>
                    <li><a href="#">Movies</a></li>
                    <li><a href="#">Events</a></li>
                    <li><a href="#">Plays</a></li>
                    <li><a href="#">Sports</a></li>
                    <li><a href="#">Activities</a></li>
                </ul>
            </nav>
            <div class="auth-buttons">
                <button>Sign In</button>
            </div>
        </div>
    </header>

    <!-- Hero Section -->
    <section class="hero">
        <div class="container">
            <h1>Book Your Movie Tickets</h1>
            <p>Discover the latest movies and book your tickets in just a few clicks. Experience the magic of cinema with ShowSpark.</p>
            <div class="search-box">
                <input type="text" id="searchInput" placeholder="Search for movies...">
                <button id="searchBtn"><i class="fas fa-search"></i></button>
            </div>
        </div>
    </section>

    <!-- Main Content -->
    <main class="container">
        <!-- Filters -->
        <div class="filters">
            <button class="filter-btn active" data-filter="all">All</button>
            <button class="filter-btn" data-filter="action">Action</button>
            <button class="filter-btn" data-filter="comedy">Comedy</button>
            <button class="filter-btn" data-filter="drama">Drama</button>
            <button class="filter-btn" data-filter="sci-fi">Sci-Fi</button>
            <button class="filter-btn" data-filter="horror">Horror</button>
            <button class="filter-btn" data-filter="animated">Animated</button>
        </div>

        <!-- Movies Grid -->
        <div class="movies-grid" id="moviesGrid">
            <!-- Movies will be populated by JavaScript -->
        </div>

        <!-- Booking Section -->
        <section class="booking-section" id="bookingSection">
            <div class="booking-header">
                <h2 class="booking-title">Book Tickets</h2>
                <div class="close-booking" id="closeBooking">
                    <i class="fas fa-times"></i>
                </div>
            </div>
            <div class="booking-details">
                <img src="" alt="Movie Poster" class="booking-poster" id="bookingPoster">
                <div class="booking-form">
                    <h3 id="bookingMovieTitle">Movie Title</h3>
                    <div class="form-group">
                        <label for="theaterSelect">Select Theater:</label>
                        <select id="theaterSelect">
                            <option value="">Select a theater</option>
                            <option value="theater1">PVR Cinemas - Downtown</option>
                            <option value="theater2">INOX Multiplex - City Center</option>
                            <option value="theater3">Cinepolis - Entertainment Plaza</option>
                            <option value="theater4">AMC Theaters - West Mall</option>
                        </select>
                    </div>
                    <div class="form-group">
                        <label for="showtimeSelect">Select Showtime:</label>
                        <select id="showtimeSelect">
                            <option value="">Select a showtime</option>
                            <option value="10:00 AM">10:00 AM</option>
                            <option value="1:30 PM">1:30 PM</option>
                            <option value="4:00 PM">4:00 PM</option>
                            <option value="6:30 PM">6:30 PM</option>
                            <option value="9:00 PM">9:00 PM</option>
                        </select>
                    </div>
                    <div class="form-group">
                        <label>Select Seats:</label>
                        <div class="seats-grid" id="seatsGrid">
                            <!-- Seats will be populated by JavaScript -->
                        </div>
                    </div>
                    <div class="form-group">
                        <label for="ticketCount">Number of Tickets:</label>
                        <input type="number" id="ticketCount" min="1" max="10" value="1" readonly>
                    </div>
                    <div>
                        <p>Total Amount: <span id="totalAmount">₹0</span></p>
                    </div>
                    <button class="confirm-btn" id="confirmBooking">Confirm Booking</button>
                </div>
            </div>
        </section>

        <!-- Tickets Section -->
        <section class="tickets-section" id="ticketsSection">
            <h2>Your Tickets</h2>
            <div id="ticketsList">
                <!-- Tickets will be populated by JavaScript -->
            </div>
        </section>
    </main>

    <!-- Footer -->
    <footer>
        <div class="container">
            <div class="footer-content">
                <div class="footer-section">
                    <h3>About ShowSpark</h3>
                    <p>ShowSpark is your one-stop destination for booking movie tickets, event passes, and more. Experience the best of entertainment with us.</p>
                    <div class="social-links">
                        <a href="#"><i class="fab fa-facebook"></i></a>
                        <a href="#"><i class="fab fa-twitter"></i></a>
                        <a href="#"><i class="fab fa-instagram"></i></a>
                        <a href="#"><i class="fab fa-youtube"></i></a>
                    </div>
                </div>
                <div class="footer-section">
                    <h3>Quick Links</h3>
                    <ul>
                        <li><a href="#">About Us</a></li>
                        <li><a href="#">Contact Us</a></li>
                        <li><a href="#">Privacy Policy</a></li>
                        <li><a href="#">Terms & Conditions</a></li>
                        <li><a href="#">FAQ</a></li>
                    </ul>
                </div>
                <div class="footer-section">
                    <h3>Top Cities</h3>
                    <ul>
                        <li><a href="#">Mumbai</a></li>
                        <li><a href="#">Delhi</a></li>
                        <li><a href="#">Bangalore</a></li>
                        <li><a href="#">Hyderabad</a></li>
                        <li><a href="#">Chennai</a></li>
                    </ul>
                </div>
                <div class="footer-section">
                    <h3>Download Our App</h3>
                    <p>Book tickets on the go with our mobile app.</p>
                    <div class="app-download">
                        <button style="background: black; color: white; border: none; padding: 10px; border-radius: 5px; margin-right: 10px;">
                            <i class="fab fa-apple"></i> App Store
                        </button>
                        <button style="background: black; color: white; border: none; padding: 10px; border-radius: 5px;">
                            <i class="fab fa-google-play"></i> Play Store
                        </button>
                    </div>
                </div>
            </div>
            <div class="copyright">
                <p>© 2023 ShowSpark. All rights reserved.</p>
            </div>
        </div>
    </footer>

    <script>
        // Movie data with 100+ movies
        const movies = [
            { id: 1, title: "Avatar: The Way of Water", genre: "sci-fi", duration: "3h 12m", rating: 4.5 },
            { id: 2, title: "John Wick: Chapter 4", genre: "action", duration: "2h 49m", rating: 4.7 },
            { id: 3, title: "The Batman", genre: "action", duration: "2h 56m", rating: 4.3 },
            { id: 4, title: "Black Panther: Wakanda Forever", genre: "action", duration: "2h 41m", rating: 4.2 },
            { id: 5, title: "Top Gun: Maverick", genre: "action", duration: "2h 10m", rating: 4.8 },
            { id: 6, title: "Jurassic World: Dominion", genre: "sci-fi", duration: "2h 27m", rating: 3.9 },
            { id: 7, title: "Minions: The Rise of Gru", genre: "animated", duration: "1h 30m", rating: 4.1 },
            { id: 8, title: "Doctor Strange: Multiverse", genre: "action", duration: "2h 6m", rating: 4.4 },
            { id: 9, title: "The Super Mario Bros. Movie", genre: "animated", duration: "1h 32m", rating: 4.6 },
            { id: 10, title: "Spider-Man: No Way Home", genre: "action", duration: "2h 28m", rating: 4.7 },
            { id: 11, title: "Avengers: Endgame", genre: "action", duration: "3h 1m", rating: 4.9 },
            { id: 12, title: "The Dark Knight", genre: "action", duration: "2h 32m", rating: 4.9 },
            { id: 13, title: "Inception", genre: "sci-fi", duration: "2h 28m", rating: 4.8 },
            { id: 14, title: "Interstellar", genre: "sci-fi", duration: "2h 49m", rating: 4.8 },
            { id: 15, title: "The Shawshank Redemption", genre: "drama", duration: "2h 22m", rating: 4.9 },
            { id: 16, title: "Pulp Fiction", genre: "drama", duration: "2h 34m", rating: 4.8 },
            { id: 17, title: "Forrest Gump", genre: "drama", duration: "2h 22m", rating: 4.7 },
            { id: 18, title: "The Matrix", genre: "sci-fi", duration: "2h 16m", rating: 4.7 },
            { id: 19, title: "Goodfellas", genre: "drama", duration: "2h 26m", rating: 4.8 },
            { id: 20, title: "The Godfather", genre: "drama", duration: "2h 55m", rating: 4.9 },
            { id: 21, title: "The Silence of the Lambs", genre: "horror", duration: "1h 58m", rating: 4.8 },
            { id: 22, title: "Se7en", genre: "horror", duration: "2h 7m", rating: 4.7 },
            { id: 23, title: "The Shining", genre: "horror", duration: "2h 26m", rating: 4.7 },
            { id: 24, title: "Alien", genre: "horror", duration: "1h 57m", rating: 4.6 },
            { id: 25, title: "Psycho", genre: "horror", duration: "1h 49m", rating: 4.5 },
            { id: 26, title: "The Exorcist", genre: "horror", duration: "2h 2m", rating: 4.4 },
            { id: 27, title: "Jaws", genre: "horror", duration: "2h 4m", rating: 4.3 },
            { id: 28, title: "The Conjuring", genre: "horror", duration: "1h 52m", rating: 4.2 },
            { id: 29, title: "Get Out", genre: "horror", duration: "1h 44m", rating: 4.5 },
            { id: 30, title: "Hereditary", genre: "horror", duration: "2h 7m", rating: 4.1 },
            { id: 31, title: "Toy Story", genre: "animated", duration: "1h 21m", rating: 4.8 },
            { id: 32, title: "Finding Nemo", genre: "animated", duration: "1h 40m", rating: 4.7 },
            { id: 33, title: "The Lion King", genre: "animated", duration: "1h 28m", rating: 4.8 },
            { id: 34, title: "Frozen", genre: "animated", duration: "1h 42m", rating: 4.3 },
            { id: 35, title: "Shrek", genre: "animated", duration: "1h 30m", rating: 4.5 },
            { id: 36, title: "Zootopia", genre: "animated", duration: "1h 48m", rating: 4.6 },
            { id: 37, title: "The Incredibles", genre: "animated", duration: "1h 55m", rating: 4.6 },
            { id: 38, title: "Spirited Away", genre: "animated", duration: "2h 5m", rating: 4.8 },
            { id: 39, title: "Up", genre: "animated", duration: "1h 36m", rating: 4.7 },
            { id: 40, title: "Inside Out", genre: "animated", duration: "1h 35m", rating: 4.6 },
            { id: 41, title: "The Hangover", genre: "comedy", duration: "1h 40m", rating: 4.2 },
            { id: 42, title: "Superbad", genre: "comedy", duration: "1h 53m", rating: 4.3 },
            { id: 43, title: "Bridesmaids", genre: "comedy", duration: "2h 5m", rating: 4.0 },
            { id: 44, title: "Anchorman", genre: "comedy", duration: "1h 34m", rating: 4.1 },
            { id: 45, title: "Step Brothers", genre: "comedy", duration: "1h 38m", rating: 4.2 },
            { id: 46, title: "Dumb and Dumber", genre: "comedy", duration: "1h 47m", rating: 4.3 },
            { id: 47, title: "Airplane!", genre: "comedy", duration: "1h 28m", rating: 4.5 },
            { id: 48, title: "Ghostbusters", genre: "comedy", duration: "1h 45m", rating: 4.4 },
            { id: 49, title: "Groundhog Day", genre: "comedy", duration: "1h 41m", rating: 4.6 },
            { id: 50, title: "The Big Lebowski", genre: "comedy", duration: "1h 57m", rating: 4.5 },
            { id: 51, title: "Star Wars: A New Hope", genre: "sci-fi", duration: "2h 1m", rating: 4.8 },
            { id: 52, title: "The Empire Strikes Back", genre: "sci-fi", duration: "2h 4m", rating: 4.9 },
            { id: 53, title: "Return of the Jedi", genre: "sci-fi", duration: "2h 11m", rating: 4.7 },
            { id: 54, title: "Blade Runner", genre: "sci-fi", duration: "1h 57m", rating: 4.6 },
            { id: 55, title: "2001: A Space Odyssey", genre: "sci-fi", duration: "2h 29m", rating: 4.7 },
            { id: 56, title: "The Terminator", genre: "sci-fi", duration: "1h 47m", rating: 4.5 },
            { id: 57, title: "Terminator 2: Judgment Day", genre: "sci-fi", duration: "2h 17m", rating: 4.8 },
            { id: 58, title: "Back to the Future", genre: "sci-fi", duration: "1h 56m", rating: 4.8 },
            { id: 59, title: "E.T. the Extra-Terrestrial", genre: "sci-fi", duration: "1h 55m", rating: 4.7 },
            { id: 60, title: "The Martian", genre: "sci-fi", duration: "2h 24m", rating: 4.6 },
            { id: 61, title: "La La Land", genre: "drama", duration: "2h 8m", rating: 4.4 },
            { id: 62, title: "The Social Network", genre: "drama", duration: "2h", rating: 4.5 },
            { id: 63, title: "Fight Club", genre: "drama", duration: "2h 19m", rating: 4.7 },
            { id: 64, title: "Good Will Hunting", genre: "drama", duration: "2h 6m", rating: 4.6 },
            { id: 65, title: "The Departed", genre: "drama", duration: "2h 31m", rating: 4.7 },
            { id: 66, title: "Schindler's List", genre: "drama", duration: "3h 15m", rating: 4.9 },
            { id: 67, title: "Saving Private Ryan", genre: "drama", duration: "2h 49m", rating: 4.8 },
            { id: 68, title: "Gladiator", genre: "drama", duration: "2h 35m", rating: 4.8 },
            { id: 69, title: "Braveheart", genre: "drama", duration: "2h 58m", rating: 4.7 },
            { id: 70, title: "The Green Mile", genre: "drama", duration: "3h 9m", rating: 4.7 },
            { id: 71, title: "The Lord of the Rings: Fellowship", genre: "action", duration: "2h 58m", rating: 4.9 },
            { id: 72, title: "The Lord of the Rings: Two Towers", genre: "action", duration: "2h 59m", rating: 4.8 },
            { id: 73, title: "The Lord of the Rings: Return", genre: "action", duration: "3h 21m", rating: 4.9 },
            { id: 74, title: "The Avengers", genre: "action", duration: "2h 23m", rating: 4.7 },
            { id: 75, title: "Guardians of the Galaxy", genre: "action", duration: "2h 1m", rating: 4.6 },
            { id: 76, title: "Mad Max: Fury Road", genre: "action", duration: "2h", rating: 4.7 },
            { id: 77, title: "Die Hard", genre: "action", duration: "2h 12m", rating: 4.6 },
            { id: 78, title: "Indiana Jones: Raiders", genre: "action", duration: "1h 55m", rating: 4.8 },
            { id: 79, title: "Mission: Impossible", genre: "action", duration: "1h 50m", rating: 4.4 },
            { id: 80, title: "The Bourne Identity", genre: "action", duration: "1h 59m", rating: 4.5 },
            { id: 81, title: "Gone Girl", genre: "drama", duration: "2h 29m", rating: 4.4 },
            { id: 82, title: "The Girl with the Dragon Tattoo", genre: "drama", duration: "2h 38m", rating: 4.3 },
            { id: 83, title: "No Country for Old Men", genre: "drama", duration: "2h 2m", rating: 4.7 },
            { id: 84, title: "There Will Be Blood", genre: "drama", duration: "2h 38m", rating: 4.6 },
            { id: 85, title: "The Revenant", genre: "drama", duration: "2h 36m", rating: 4.5 },
            { id: 86, title: "American Beauty", genre: "drama", duration: "2h 2m", rating: 4.5 },
            { id: 87, title: "The Sixth Sense", genre: "horror", duration: "1h 47m", rating: 4.5 },
            { id: 88, title: "The Ring", genre: "horror", duration: "1h 55m", rating: 4.2 },
            { id: 89, title: "A Quiet Place", genre: "horror", duration: "1h 30m", rating: 4.4 },
            { id: 90, title: "It", genre: "horror", duration: "2h 15m", rating: 4.3 },
            { id: 91, title: "The Descent", genre: "horror", duration: "1h 39m", rating: 4.1 },
            { id: 92, title: "Shaun of the Dead", genre: "comedy", duration: "1h 39m", rating: 4.5 },
            { id: 93, title: "Hot Fuzz", genre: "comedy", duration: "2h 1m", rating: 4.6 },
            { id: 94, title: "The World's End", genre: "comedy", duration: "1h 49m", rating: 4.3 },
            { id: 95, title: "Scott Pilgrim vs. the World", genre: "comedy", duration: "1h 52m", rating: 4.4 },
            { id: 96, title: "Napoleon Dynamite", genre: "comedy", duration: "1h 36m", rating: 4.2 },
            { id: 97, title: "Mean Girls", genre: "comedy", duration: "1h 37m", rating: 4.4 },
            { id: 98, title: "Legally Blonde", genre: "comedy", duration: "1h 36m", rating: 4.3 },
            { id: 99, title: "Clueless", genre: "comedy", duration: "1h 37m", rating: 4.4 },
            { id: 100, title: "Ferris Bueller's Day Off", genre: "comedy", duration: "1h 43m", rating: 4.5 },
            { id: 101, title: "Back to the Future Part II", genre: "sci-fi", duration: "1h 48m", rating: 4.5 },
            { id: 102, title: "The Truman Show", genre: "drama", duration: "1h 43m", rating: 4.6 },
            { id: 103, title: "Eternal Sunshine", genre: "drama", duration: "1h 48m", rating: 4.5 },
            { id: 104, title: "The Prestige", genre: "drama", duration: "2h 10m", rating: 4.7 },
            { id: 105, title: "Whiplash", genre: "drama", duration: "1h 46m", rating: 4.8 }
        ];

        // Global variables to manage state
        let selectedMovie = null;
        let selectedSeats = [];
        let bookedTickets = [];

        // Initialize the app
        function init() {
            displayMovies(movies);
            setupEventListeners();
            generateSeats();
        }

        // Display movies in the grid
        function displayMovies(moviesToShow) {
            const moviesGrid = document.getElementById('moviesGrid');
            moviesGrid.innerHTML = '';
            
            moviesToShow.forEach(movie => {
                const movieCard = document.createElement('div');
                movieCard.className = 'movie-card';
                movieCard.innerHTML = `
                    <img src="https://placehold.co/300x450/032541/FFFFFF?text=${encodeURIComponent(movie.title)}" alt="${movie.title} movie poster" class="movie-poster">
                    <div class="movie-info">
                        <h3 class="movie-title">${movie.title}</h3>
                        <div class="movie-details">
                            <span>${movie.duration}</span>
                            <span class="movie-rating">★ ${movie.rating}</span>
                        </div>
                        <button class="book-btn" data-id="${movie.id}">Book Tickets</button>
                    </div>
                `;
                moviesGrid.appendChild(movieCard);
            });
            
            // Add event listeners to book buttons
            document.querySelectorAll('.book-btn').forEach(button => {
                button.addEventListener('click', (e) => {
                    const movieId = parseInt(e.target.getAttribute('data-id'));
                    openBooking(movieId);
                });
            });
        }

        // Set up event listeners
        function setupEventListeners() {
            // Filter buttons
            document.querySelectorAll('.filter-btn').forEach(button => {
                button.addEventListener('click', (e) => {
                    document.querySelectorAll('.filter-btn').forEach(btn => btn.classList.remove('active'));
                    e.target.classList.add('active');
                    
                    const filter = e.target.getAttribute('data-filter');
                    if (filter === 'all') {
                        displayMovies(movies);
                    } else {
                        const filteredMovies = movies.filter(movie => movie.genre === filter);
                        displayMovies(filteredMovies);
                    }
                });
            });
            
            // Search functionality
            document.getElementById('searchBtn').addEventListener('click', searchMovies);
            document.getElementById('searchInput').addEventListener('keyup', (e) => {
                if (e.key === 'Enter') {
                    searchMovies();
                }
            });
            
            // Close booking section
            document.getElementById('closeBooking').addEventListener('click', () => {
                document.getElementById('bookingSection').style.display = 'none';
            });
            
            // Confirm booking
            document.getElementById('confirmBooking').addEventListener('click', confirmBooking);
            
            // Update ticket count and amount when seats are selected
            document.getElementById('seatsGrid').addEventListener('click', updateTicketCount);
        }

        // Search movies
        function searchMovies() {
            const query = document.getElementById('searchInput').value.toLowerCase();
            if (query.trim() === '') {
                displayMovies(movies);
                return;
            }
            
            const filteredMovies = movies.filter(movie => 
                movie.title.toLowerCase().includes(query)
            );
            
            displayMovies(filteredMovies);
        }

        // Open booking section for a movie
        function openBooking(movieId) {
            selectedMovie = movies.find(movie => movie.id === movieId);
            document.getElementById('bookingMovieTitle').textContent = selectedMovie.title;
            document.getElementById('bookingPoster').src = `https://placehold.co/600x900/032541/FFFFFF?text=${encodeURIComponent(selectedMovie.title)}`;
            
            // Reset form
            document.getElementById('theaterSelect').selectedIndex = 0;
            document.getElementById('showtimeSelect').selectedIndex = 0;
            document.getElementById('ticketCount').value = 1;
            document.getElementById('totalAmount').textContent = '₹0';
            
            // Clear seat selection
            selectedSeats = [];
            document.querySelectorAll('.seat').forEach(seat => {
                if (!seat.classList.contains('occupied')) {
                    seat.classList.remove('selected');
                }
            });
            
            // Show booking section
            document.getElementById('bookingSection').style.display = 'block';
            
            // Scroll to booking section
            document.getElementById('bookingSection').scrollIntoView({ behavior: 'smooth' });
        }

        // Generate seats grid
        function generateSeats() {
            const seatsGrid = document.getElementById('seatsGrid');
            seatsGrid.innerHTML = '';
            
            const rows = ['A', 'B', 'C', 'D', 'E', 'F', 'G', 'H'];
            const seatsPerRow = 10;
            
            rows.forEach(row => {
                for (let i = 1; i <= seatsPerRow; i++) {
                    const seat = document.createElement('div');
                    seat.className = 'seat';
                    seat.textContent = row + i;
                    
                    // Randomly mark some seats as occupied
                    if (Math.random() < 0.2) {
                        seat.classList.add('occupied');
                    }
                    
                    seatsGrid.appendChild(seat);
                }
            });
        }

        // Update ticket count and total amount
        function updateTicketCount() {
            selectedSeats = [];
            document.querySelectorAll('.seat.selected').forEach(seat => {
                selectedSeats.push(seat.textContent);
            });
            
            const ticketCount = selectedSeats.length;
            document.getElementById('ticketCount').value = ticketCount;
            document.getElementById('totalAmount').textContent = `₹${ticketCount * 250}`;
        }

        // Confirm booking
        function confirmBooking() {
            const theater = document.getElementById('theaterSelect').value;
            const showtime = document.getElementById('showtimeSelect').value;
            
            if (!theater || !showtime || selectedSeats.length === 0) {
                alert('Please select theater, showtime, and at least one seat');
                return;
            }
            
            // Create ticket object
            const ticket = {
                id: Date.now(),
                movie: selectedMovie.title,
                theater: document.getElementById('theaterSelect').options[document.getElementById('theaterSelect').selectedIndex].text,
                showtime: showtime,
                seats: selectedSeats,
                amount: selectedSeats.length * 250
            };
            
            // Add to booked tickets
            bookedTickets.push(ticket);
            
            // Show confirmation
            alert(`Booking confirmed for ${selectedMovie.title} at ${showtime}. Seats: ${selectedSeats.join(', ')}. Total: ₹${ticket.amount}`);
            
            // Update tickets section
            displayTickets();
            
            // Hide booking section
            document.getElementById('bookingSection').style.display = 'none';
        }

        // Display booked tickets
        function displayTickets() {
            const ticketsList = document.getElementById('ticketsList');
            ticketsList.innerHTML = '';
            
            if (bookedTickets.length === 0) {
                ticketsList.innerHTML = '<p>No tickets booked yet.</p>';
                document.getElementById('ticketsSection').style.display = 'block';
                return;
            }
            
            bookedTickets.forEach(ticket => {
                const ticketElement = document.createElement('div');
                ticketElement.className = 'ticket';
                ticketElement.innerHTML = `
                    <div class="ticket-info">
                        <img src="https://placehold.co/100x150/032541/FFFFFF?text=${encodeURIComponent(ticket.movie)}" alt="${ticket.movie} ticket" class="ticket-poster">
                        <div class="ticket-details">
                            <h3>${ticket.movie}</h3>
                            <p><strong>Theater:</strong> ${ticket.theater}</p>
                            <p><strong>Showtime:</strong> ${ticket.showtime}</p>
                            <p><strong>Seats:</strong> ${ticket.seats.join(', ')}</p>
                            <p><strong>Amount:</strong> ₹${ticket.amount}</p>
                        </div>
                    </div>
                `;
                ticketsList.appendChild(ticketElement);
            });
            
            document.getElementById('ticketsSection').style.display = 'block';
        }

        // Initialize the app when the DOM is loaded
        document.addEventListener('DOMContentLoaded', init);
    </script>
</body>
</html>
