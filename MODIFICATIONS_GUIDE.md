# 🔧 COMMON MODIFICATIONS GUIDE

Quick code snippets for common changes you might want to make.

---

## 🎨 Brand Customization

### Change Primary Color Everywhere

**File:** `lib/core/constants/app_colors.dart`

```dart
// OLD:
static const Color primaryGreen = Color(0xFF556B2F); // Olive Green

// NEW (Example: Red brand):
static const Color primaryGreen = Color(0xFFE74C3C); // Red
```

This single change updates buttons, headers, and all UI elements!

### Change App Name

**File:** `lib/core/constants/app_strings.dart`

```dart
// OLD:
static const String appName = 'زيتون';
static const String appTagline = 'توصيل الطعام الذي تثق به';

// NEW (Example):
static const String appName = 'طلباتي';
static const String appTagline = 'الطعام بسرعة وأمان';
```

### Change App Logo

**File:** `lib/features/auth/presentation/login_screen.dart`

```dart
// OLD:
child: const Text(
  '🫒',
  style: TextStyle(fontSize: 48),
),

// NEW (Use any emoji or image):
child: Image.asset(
  'assets/images/your_logo.png',
  width: 80,
  height: 80,
)
```

---

## 👥 Add More Restaurants

**File:** `lib/data/mock_data.dart`

```dart
static final List<Restaurant> restaurants = [
  // ... existing restaurants ...
  
  // ADD NEW:
  Restaurant(
    id: 'rest_5',
    name: 'مطعم الذوق',
    cuisine: 'لبناني',
    rating: 4.8,
    reviewCount: 156,
    deliveryTime: '30-40 دقيقة',
    imageUrl: 'https://via.placeholder.com/300x200?text=مطعم+الذوق',
    isOpen: true,
    deliveryFee: 5500,
    minOrderAmount: 22000,
    ownerPhone: '0116666777',
    address: 'دمشق، الرقة',
    latitude: 33.5200,
    longitude: 36.2800,
    createdAt: DateTime.now().subtract(const Duration(days: 20)),
  ),
];
```

---

## 🍽️ Add Menu Items

**File:** `lib/data/mock_data.dart`

```dart
static final List<MenuItem> menuItems = [
  // ... existing items ...
  
  // ADD NEW:
  MenuItem(
    id: 'item_15',
    restaurantId: 'rest_1', // Link to restaurant
    name: 'مشكل كبسة',
    description: 'خليط من اللحوم مع أرز فاخر',
    price: 18000,
    category: 'أطباق رئيسية',
    imageUrl: 'https://via.placeholder.com/200x150?text=مشكل+كبسة',
    isAvailable: true,
    calories: 950,
    tags: ['حار', 'لحوم'],
    createdAt: DateTime.now(),
  ),
];
```

---

## 💰 Change Fee Calculation

**File:** `lib/services/delivery_fee_calculator.dart`

```dart
// CURRENT (SYP):
static const double baseFee = 2000;      // 2,000 SYP
static const double perKmRate = 1000;    // 1,000 SYP per km
static const double fuelSurcharge = 500; // 500 SYP

// CHANGE TO (Example: USD):
static const double baseFee = 2.50;      // $2.50
static const double perKmRate = 0.80;    // $0.80 per km
static const double fuelSurcharge = 0.50; // $0.50
```

---

## 💵 Change Commission Split

**File:** `lib/services/commission_calculator.dart`

```dart
// CURRENT (Driver 80%, Company 20%):
static const double companyShare = 0.20; // 20%
static const double driverShare = 0.80;  // 80%

// CHANGE TO (Example: Driver 70%, Company 30%):
static const double companyShare = 0.30; // 30%
static const double driverShare = 0.70;  // 70%
```

---

## ✅ Add Custom Validation

**File:** `lib/core/utils/validators.dart`

```dart
// ADD NEW VALIDATOR:
static String? validateRestaurantName(String? name) {
  if (name == null || name.isEmpty) {
    return 'اسم المطعم مطلوب';
  }
  
  if (name.length < 3) {
    return 'اسم المطعم يجب أن يكون أطول من حرفين';
  }
  
  if (name.length > 100) {
    return 'اسم المطعم طويل جداً';
  }
  
  return null;
}
```

Then use in TextField:
```dart
CustomTextField(
  label: 'اسم المطعم',
  hint: 'أدخل اسم المطعم',
  validator: Validators.validateRestaurantName,
)
```

---

## 📝 Add New String Constant

**File:** `lib/core/constants/app_strings.dart`

```dart
class AppStrings {
  // ... existing strings ...
  
  // ADD NEW:
  static const String myNewString = 'قيمة النص الجديد';
  static const String anotherString = 'نص آخر';
}
```

Use anywhere:
```dart
Text(AppStrings.myNewString)
```

---

## 🎯 Change Loyalty Target

**File:** `lib/features/customer/state/customer_provider.dart`

```dart
// CURRENT: 5 orders = reward
int get ordersUntilReward => (_orderCount >= 5 ? 0 : 5 - _orderCount);

// CHANGE TO: 10 orders = reward
int get ordersUntilReward => (_orderCount >= 10 ? 0 : 10 - _orderCount);
```

Also update the checkout:
```dart
bool get isEligibleForReward => _orderCount >= 10; // Change from 5
```

---

## 🎨 Change Button Color

**File:** Any screen using CustomButton

```dart
// CURRENT (Primary Green):
CustomButton(
  label: 'اضغط هنا',
  onPressed: () {},
)

// CHANGE TO ORANGE:
CustomButton(
  label: 'اضغط هنا',
  onPressed: () {},
  backgroundColor: AppColors.accentOrange,
)

// CHANGE TO CUSTOM COLOR:
CustomButton(
  label: 'اضغط هنا',
  onPressed: () {},
  backgroundColor: Color(0xFF123456), // Your hex color
)
```

---

## 📍 Change Mock Distance for Fee Calculation

**File:** `lib/features/customer/presentation/cart_screen.dart`

```dart
// CURRENT:
const mockDistance = 5.0; // 5 km

// CHANGE TO:
const mockDistance = 3.0; // 3 km (will calculate lower fee)
const mockDistance = 10.0; // 10 km (will include surcharge)
```

---

## 🔄 Add New Provider

**File:** `lib/features/your_feature/state/your_provider.dart`

```dart
import 'package:flutter/material.dart';

class YourProvider extends ChangeNotifier {
  // State variables
  String _data = '';
  bool _isLoading = false;
  
  // Getters
  String get data => _data;
  bool get isLoading => _isLoading;
  
  // Methods
  Future<void> loadData() async {
    _isLoading = true;
    notifyListeners();
    
    try {
      // Load data here
      _data = 'Sample data';
    } catch (e) {
      print('Error: $e');
    }
    
    _isLoading = false;
    notifyListeners();
  }
}
```

Register in `main.dart`:
```dart
MultiProvider(
  providers: [
    ChangeNotifierProvider(create: (_) => AuthProvider()),
    ChangeNotifierProvider(create: (_) => CustomerProvider()),
    ChangeNotifierProvider(create: (_) => YourProvider()), // ADD THIS
  ],
)
```

---

## 🎬 Add New Screen

**Steps:**

1. **Create file:** `lib/features/customer/presentation/my_screen.dart`

```dart
import 'package:flutter/material.dart';

class MyScreen extends StatefulWidget {
  const MyScreen({Key? key}) : super(key: key);

  @override
  State<MyScreen> createState() => _MyScreenState();
}

class _MyScreenState extends State<MyScreen> {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: const Text('My Screen')),
      body: const Center(child: Text('Your content here')),
    );
  }
}
```

2. **Add navigation:**

```dart
// From another screen:
Navigator.of(context).push(
  MaterialPageRoute(builder: (_) => const MyScreen()),
);
```

---

## 🌐 Change Delivery Zone Max Distance

**File:** `lib/services/delivery_fee_calculator.dart`

```dart
// CURRENT: 50 km max:
static bool isDeliveryAvailable(double distanceInKm) {
  const maxDeliveryDistance = 50; // 50 km
  return distanceInKm > 0 && distanceInKm <= maxDeliveryDistance;
}

// CHANGE TO 30 km:
static bool isDeliveryAvailable(double distanceInKm) {
  const maxDeliveryDistance = 30; // 30 km
  return distanceInKm > 0 && distanceInKm <= maxDeliveryDistance;
}
```

---

## 📱 Add Landscape Support

**File:** `lib/main.dart`

```dart
MaterialApp(
  title: AppStrings.appName,
  theme: AppTheme.lightTheme,
  // ADD:
  supportedLocales: const [
    Locale('ar', 'SY'), // Arabic - Syria
    Locale('en', 'US'), // English - US
  ],
)
```

---

## 🔐 Add User Authentication Check

**File:** Any screen

```dart
// Before showing sensitive data:
Consumer<AuthProvider>(
  builder: (context, authProvider, _) {
    if (!authProvider.isAuthenticated) {
      return const LoginScreen();
    }
    
    return YourActualScreen();
  },
)
```

---

## 💾 Add Local Storage (with SharedPreferences)

**File:** Create `lib/services/local_storage_service.dart`

```dart
import 'package:shared_preferences/shared_preferences.dart';

class LocalStorageService {
  static late SharedPreferences _prefs;
  
  static Future<void> init() async {
    _prefs = await SharedPreferences.getInstance();
  }
  
  // Save string
  static Future<bool> saveString(String key, String value) async {
    return await _prefs.setString(key, value);
  }
  
  // Get string
  static String? getString(String key) {
    return _prefs.getString(key);
  }
  
  // Save int
  static Future<bool> saveInt(String key, int value) async {
    return await _prefs.setInt(key, value);
  }
  
  // Get int
  static int? getInt(String key) {
    return _prefs.getInt(key);
  }
}
```

Initialize in `main.dart`:
```dart
void main() async {
  WidgetsFlutterBinding.ensureInitialized();
  await LocalStorageService.init();
  runApp(const ZaytoonApp());
}
```

---

## 🔗 Integrate Real API

**File:** `lib/services/api_service.dart` (NEW)

```dart
import 'package:http/http.dart' as http;
import 'dart:convert';

class ApiService {
  static const String baseUrl = 'https://your-api.com/api';
  
  static Future<Map<String, dynamic>> fetchRestaurants() async {
    try {
      final response = await http.get(
        Uri.parse('$baseUrl/restaurants'),
        headers: {'Content-Type': 'application/json'},
      );
      
      if (response.statusCode == 200) {
        return jsonDecode(response.body);
      } else {
        throw Exception('Failed to load restaurants');
      }
    } catch (e) {
      print('Error: $e');
      rethrow;
    }
  }
}
```

Use in Provider:
```dart
Future<void> fetchRestaurants() async {
  _isLoading = true;
  try {
    final data = await ApiService.fetchRestaurants();
    _restaurants = (data['restaurants'] as List)
        .map((r) => Restaurant.fromJson(r))
        .toList();
  } catch (e) {
    _error = e.toString();
  }
  _isLoading = false;
  notifyListeners();
}
```

---

## ❓ Need Help?

All the patterns shown here are already used in the codebase. Look at:
- `lib/features/auth/presentation/login_screen.dart` - Form validation example
- `lib/features/customer/state/customer_provider.dart` - Provider pattern
- `lib/data/mock_data.dart` - Data structure examples
- `lib/core/widgets/` - Custom widget patterns

**You've got this! 🚀**
