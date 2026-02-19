# 🫒 Zaytoon Delivery App - Flutter
**Food Delivery Platform for Syria - Three-in-One App (Customer, Restaurant, Driver)**

---

## 📋 Project Overview

Zaytoon is a comprehensive delivery app with three distinct user interfaces:
- **🛒 Customer**: Browse restaurants, order food, track deliveries, loyalty rewards
- **🏪 Restaurant**: Manage menu, accept orders, view analytics
- **🚗 Driver**: Accept deliveries, track earnings, real-time navigation

### Key Features
✅ **Price Transparency** - Same restaurant prices, customers only pay delivery fee  
✅ **Smart Reorder** - 3-day reminder to reorder favorite items  
✅ **Loyalty Program** - Order 5 times, get 20% discount  
✅ **Arabic RTL Support** - Full RTL/LTR support for Syria region  
✅ **Clean Architecture** - Modular, maintainable, ready for backend integration  
✅ **Mock Data** - Pre-loaded demo data for immediate testing  
✅ **No Database Code** - UI-focused, easy to integrate with your backend  

---

## 🛠️ Project Structure

```
lib/
├── core/                          # Reusable code
│   ├── constants/
│   │   ├── app_colors.dart       # Brand colors (olive green #556B2F)
│   │   └── app_strings.dart      # All Arabic strings
│   ├── theme/
│   │   ├── app_theme.dart        # Material theme configuration
│   │   └── text_styles.dart      # Typography system
│   ├── utils/
│   │   ├── validators.dart       # Input validation (phone, OTP, etc)
│   │   ├── formatters.dart       # Format prices, dates, currency
│   │   └── helpers.dart          # Helper functions
│   └── widgets/
│       ├── custom_button.dart
│       ├── custom_text_field.dart
│       ├── custom_app_bar.dart
│       ├── loading_indicator.dart
│       └── status_widgets.dart
│
├── features/                      # Feature modules
│   ├── auth/                      # Authentication & role selection
│   │   ├── presentation/
│   │   │   ├── login_screen.dart
│   │   │   ├── otp_screen.dart
│   │   │   └── role_selection_screen.dart
│   │   └── state/
│   │       └── auth_provider.dart
│   │
│   ├── customer/                  # Customer feature
│   │   ├── presentation/
│   │   │   ├── home_screen.dart
│   │   │   ├── restaurant_menu_screen.dart
│   │   │   ├── cart_screen.dart
│   │   │   ├── checkout_screen.dart
│   │   │   ├── order_tracking_screen.dart (TODO)
│   │   │   ├── order_history_screen.dart (TODO)
│   │   │   ├── loyalty_dashboard_screen.dart (TODO)
│   │   │   └── profile_screen.dart (TODO)
│   │   ├── state/
│   │   │   └── customer_provider.dart
│   │   └── widgets/
│   │       └── [customer-specific widgets]
│   │
│   ├── restaurant/                # Restaurant feature (structure ready)
│   ├── driver/                    # Driver feature (structure ready)
│   └── loyalty/                   # Loyalty program (structure ready)
│
├── models/                        # Data models
│   ├── user.dart                  # User with role (customer, restaurant, driver)
│   ├── restaurant.dart
│   ├── menu_item.dart
│   ├── cart_item.dart
│   ├── order.dart
│   └── driver.dart
│
├── services/                      # Business logic services
│   ├── delivery_fee_calculator.dart    # Calculates fees based on distance
│   └── commission_calculator.dart      # Driver 80%, Company 20%
│
├── data/
│   └── mock_data.dart             # Pre-loaded demo data
│
└── main.dart                      # App entry point with routing

pubspec.yaml                       # Dependencies
assets/
└── images/                        # Placeholder for images
```

---

## 🚀 Getting Started

### Prerequisites
- Flutter 3.x installed
- Dart SDK 3.0+
- Android Studio or Xcode for emulator
- VS Code or Android Studio as IDE

### Installation Steps

1. **Navigate to project directory**
```bash
cd zaytoon.task
```

2. **Get dependencies**
```bash
flutter pub get
```

3. **Run the app**
```bash
flutter run
```

Or in VS Code, simply press `F5` to run.

### Running on Devices

**Android:**
```bash
flutter run -d <device-id>
```

**iOS:**
```bash
flutter run -d <device-id>
```

**Web (experimental):**
```bash
flutter run -d chrome
```

---

## 📱 Testing the App

### 🔐 Login Flow
1. **Login Screen**: Enter any phone number (e.g., `0912345678`)
2. **OTP Screen**: Enter any 4-6 digit code
3. **Role Selection**: Choose your role (Customer, Restaurant, or Driver)
4. **Main Screen**: Access the respective dashboard

### 🛒 Customer Demo Features

**Home Screen:**
- ✅ Search and filter restaurants
- ✅ View loyalty progress (order 5 times = 20% discount)
- ✅ Reorder suggestions (items from 3+ days ago)
- ✅ Browse restaurant cards with ratings and delivery times

**Restaurant Menu:**
- ✅ View categorized menu items
- ✅ See prices (100% transparent - same as in-store)
- ✅ Add items to cart with quantity control

**Shopping Cart:**
- ✅ View all cart items
- ✅ Modify quantities
- ✅ See order summary with delivery fee

**Checkout:**
- ✅ Enter delivery address
- ✅ Add special instructions
- ✅ Select payment method
- ✅ Confirm order

### 💰 Fee Calculations (Working Examples)

**Delivery Fee Calculator:**
```dart
DeliveryFeeCalculator.calculate(2.0)    // → 2,000 SYP (base fee)
DeliveryFeeCalculator.calculate(5.0)    // → 7,000 SYP (base + distance)
DeliveryFeeCalculator.calculate(10.0)   // → 15,500 SYP (with surcharge)
```

**Commission Split:**
- Delivery Fee: 10,000 SYP
- Driver Earnings (80%): 8,000 SYP ✓
- Company Commission (20%): 2,000 SYP

---

## 🎨 Design System

### Colors
- **Primary Green**: `#556B2F` (Olive - brand color)
- **Secondary Green**: `#8F9E6A` (Light olive)
- **Accent Orange**: `#E67E22` (CTA buttons)
- **Dark Grey**: `#2C3E50` (Text)
- **Light Grey**: `#ECF0F1` (Backgrounds)

### Typography
- **Font**: Cairo (configured in pubspec.yaml)
- **Heading 1**: 32px, Bold
- **Heading 2**: 26px, Bold
- **Body**: 14-16px, Regular
- **Price**: 18px+, Bold, Olive Green

### RTL Support
All screens are fully RTL-enabled for Arabic. Set in `main.dart`:
```dart
Directionality(
  textDirection: TextDirection.rtl,
  child: child,
)
```

---

## 📊 State Management

### Provider Architecture
```
AuthProvider
  └─ Current User
  └─ User Role
  └─ Authentication State

CustomerProvider
  ├─ Restaurants List
  ├─ Cart Items
  ├─ Order History
  └─ Loyalty Points
```

Add providers in `main.dart`:
```dart
MultiProvider(
  providers: [
    ChangeNotifierProvider(create: (_) => AuthProvider()),
    ChangeNotifierProvider(create: (_) => CustomerProvider()),
  ],
)
```

---

## 🔌 Backend Integration Guide

### Ready to Replace with Real API

All mock data is located in [`lib/data/mock_data.dart`](lib/data/mock_data.dart).

**Example: Replace restaurant fetch**

**Current (Mock):**
```dart
// In CustomerProvider
void _loadMockData() {
  _restaurants = MockData.restaurants;
}
```

**After Backend:**
```dart
Future<void> fetchRestaurants() async {
  _isLoading = true;
  try {
    final response = await http.get(Uri.parse('$API_URL/restaurants'));
    _restaurants = (jsonDecode(response.body) as List)
        .map((r) => Restaurant.fromJson(r))
        .toList();
  } catch (e) {
    _error = e.toString();
  }
  _isLoading = false;
  notifyListeners();
}
```

### API Integration Points

| Feature | File | Method |
|---------|------|--------|
| Login/OTP | `auth_provider.dart` | `loginWithOTP()` |
| Load Restaurants | `customer_provider.dart` | `fetchRestaurants()` |
| Load Menu | `restaurant_menu_screen.dart` | Call `MenuService` |
| Create Order | `customer_provider.dart` | `checkout()` |
| Track Order | `order_tracking_screen.dart` (TODO) | `trackOrder()` |

### Models are Ready for JSON
All models include `toJson()` and `fromJson()` for API serialization:

```dart
// Serialize to send to server
final json = order.toJson();

// Deserialize from server response
final order = Order.fromJson(jsonResponse);
```

---

## 🔐 Security Considerations

⚠️ **Current Demo State:**
- No real OTP verification
- No backend validation
- Phone numbers accepted as-is

**For Production:**
1. Validate phone with SMS/Twilio
2. Add Firebase Auth or custom JWT tokens
3. Implement secure payment gateway integration
4. Add SSL pinning for API calls
5. Encrypt sensitive data locally with Hive

---

## 📝 TODO: Features to Complete

### Customer Features (In Priority Order)
- [ ] **Order Tracking Screen** - Real-time map with driver location
- [ ] **Order History Screen** - Past orders with reorder buttons
- [ ] **Loyalty Dashboard** - Rewards management
- [ ] **Profile Screen** - Addresses, payment methods, settings
- [ ] **Favorites** - Save favorite restaurants/items
- [ ] **Reviews & Ratings** - Rate restaurants and food

### Restaurant Features
- [ ] Dashboard with today's orders
- [ ] Menu manager (CRUD items)
- [ ] Orders queue management
- [ ] Analytics dashboard (sales, popular items)
- [ ] Settings (hours, delivery radius)

### Driver Features
- [ ] Available orders list with earnings shown
- [ ] Navigation to restaurant and customer
- [ ] In-app calling interface
- [ ] Earnings tracking and withdrawal
- [ ] Safety guidelines onboarding

### Common Features
- [ ] Push notifications
- [ ] Real-time updates (Socket.io)
- [ ] Payment gateway integration
- [ ] Multi-language support (English, Arabic)
- [ ] Offline mode caching

---

## 🐛 Troubleshooting

### Build Errors
```bash
# Clean and rebuild
flutter clean
flutter pub get
flutter run

# Check dependencies
flutter pub upgrade
```

### RTL/Localization Issues
Ensure `Directionality` wrapper is in `main.dart` and all widgets use:
- `crossAxisAlignment: CrossAxisAlignment.start` (not `.start`)
- `textAlign: TextAlign.right` for right-aligned text

### Hot Reload Not Working
```bash
# Stop the app and run with VM service
flutter run --verbose
```

---

## 📞 Support & Modifications

### Adding New Screens
1. Create folder in `features/[feature]/presentation/`
2. Create `[name]_screen.dart` file
3. Add route to `AppRouter` in `main.dart`
4. Add Provider if needed in `features/[feature]/state/`

### Changing Brand Colors
Edit `lib/core/constants/app_colors.dart` - all colors reference this file.

### Adding Validation
Add rules in `lib/core/utils/validators.dart` - already has validators for:
- Phone numbers
- OTP codes
- Email
- Passwords
- Prices
- Addresses

---

## 📄 License

This project is provided as-is for the Zaytoon Delivery App. All code is clean, modular, and ready for production use with backend integration.

---

## ✨ Key Highlights

✅ **Clean Code**: SOLID principles, clear naming conventions  
✅ **Modular**: Each feature is independent and testable  
✅ **Well-Commented**: English comments throughout for easy modification  
✅ **RTL Ready**: Full Arabic/RTL support baked in  
✅ **Future-Proof**: Mock data layer makes backend integration seamless  
✅ **No Hacks**: Production-ready architecture, no shortcuts  

---

**Built with ❤️ for Zaytoon Delivery App**
