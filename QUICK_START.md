# 🚀 Zaytoon App - Quick Start Guide

## ⚡ Get Running in 30 Seconds

### Step 1: Navigate to Project
```bash
cd zaytoon.task
```

### Step 2: Get Dependencies
```bash
flutter pub get
```

### Step 3: Run the App
```bash
flutter run
```

That's it! The app will open on your emulator/device.

---

## 📱 What to Try

### 1. **Login Screen**
- Phone: `0912345678` (any 10-digit number works)
- Click "إرسال رمز التحقق"

### 2. **OTP Screen**
- OTP: `123456` (any 4-6 digit code works)
- Click "تحقق"

### 3. **Role Selection**
- Choose **"عميل"** (Customer) to see the app in action
- Restaurant & Driver screens are structure-ready

### 4. **Customer Home Screen**
- 🔍 **Search**: Try searching "شام" or "برجر"
- 💚 **Loyalty Bar**: Shows "اطلب 3 مرات أخرى واحصل على خصم 20%!"
- 🔄 **Reorder**: Suggestions for items ordered 3+ days ago
- 🏪 **Restaurants**: Tap any restaurant to see menu

### 5. **Restaurant Menu**
- 🍽️ Tap a restaurant card
- Select category from chips
- Add items to cart with quantity control
- See olive green pricing (transparent, no markups)

### 6. **Shopping Cart**
- 🛒 Click "عرض السلة" at bottom
- Modify quantities
- See delivery fee calculation

### 7. **Checkout**
- 📍 Enter delivery address
- 💬 Add special instructions (optional)
- 💳 Select payment method
- ✅ Confirm order

---

## 🎨 Customization Examples

### Change Brand Color
Edit `lib/core/constants/app_colors.dart`:
```dart
static const Color primaryGreen = Color(0xFF556B2F); // Change this
```

### Change App Name
Edit `lib/core/constants/app_strings.dart`:
```dart
static const String appName = 'زيتون'; // Change to your app name
```

### Add More Restaurants
Edit `lib/data/mock_data.dart` - Add to `restaurants` list:
```dart
Restaurant(
  id: 'rest_5',
  name: 'اسم المطعم',
  cuisine: 'نوع الطعام',
  // ... other fields
)
```

---

## 📂 Project Files Overview

| File | Purpose |
|------|---------|
| `lib/main.dart` | App entry point & routing |
| `lib/core/theme/app_theme.dart` | Material design theme |
| `lib/models/*.dart` | Data classes |
| `lib/features/auth/` | Login/OTP/Role selection |
| `lib/features/customer/` | Customer screens (home, menu, cart, checkout) |
| `lib/services/*.dart` | Fee & commission calculators |
| `pubspec.yaml` | Dependencies |

---

## 🔌 Ready for Backend

All API calls can be added to:
- `lib/features/auth/state/auth_provider.dart` - Login
- `lib/features/customer/state/customer_provider.dart` - Restaurants, orders
- Mock data is in `lib/data/mock_data.dart`

Just replace the mock calls with real API calls!

---

## ❓ Common Questions

### Q: How do I test with different data?
Edit `lib/data/mock_data.dart` and add your test data.

### Q: How do I change the language?
The app is currently hardcoded to Arabic. To add English:
1. Use Flutter's `intl` package (already in pubspec.yaml)
2. Create separate localization files
3. Use `Localizations` delegate

### Q: Can I use this for production?
Yes! Just add your backend API instead of mock data. The code is production-ready.

### Q: Why no Firebase?
As requested, we kept it pure Flutter with mock data. Firebase/Backend integration is your responsibility and we've made it easy to add.

---

## 🎓 Learning Tips

1. **State Management**: See how `Provider` is used in `auth_provider.dart`
2. **Custom Widgets**: Check `lib/core/widgets/` for reusable components
3. **Routing**: See `AppRouter` class in `main.dart` for role-based navigation
4. **Models**: Check `lib/models/` for JSON serialization patterns
5. **Validation**: See `lib/core/utils/validators.dart` for input validation

---

## ✨ Key Features Already Implemented

✅ Full authentication flow with role selection  
✅ Restaurant browsing and menu viewing  
✅ Shopping cart with quantity control  
✅ Delivery fee calculation based on distance  
✅ Loyalty progress tracking (order count)  
✅ Reorder suggestions  
✅ Complete checkout flow  
✅ Arabic RTL support  
✅ Responsive design  
✅ Clean, modular code  

---

## 📋 Still TODO (Optional)

- Order tracking with real-time map
- Order history screen
- Loyalty rewards dashboard
- User profile management
- Restaurant dashboard
- Driver app features
- Push notifications
- Payment gateway integration

---

## 💡 Tips

1. **Hot Reload**: Press 'r' in terminal to hot reload (changes in code)
2. **Full Restart**: Press 'R' in terminal to restart app completely
3. **Flutter Outline**: Shows widget tree in VS Code (helps with debugging)
4. **DevTools**: `flutter pub global activate devtools && devtools` for debugging

---

**Happy coding! 🫒**
