<p align="center">
  <img src="https://github.com/itssudhanshu/BrewCrew-App/blob/master/assets/drink.png" width="150">
</p>
<p align="center">(Android/iOS)</p>
<h1 align="center">BrewCrew</h1>

<p align="center"> 
  <a href="https://github.com/itssudhanshu/CareIndia/blob/master/CareIndia_v1.0.0_Light.apk?raw=true">
    <img src="https://img.shields.io/badge/Download App-CareIndia-blue.svg?style=for-the-badge">
  </a> 
</p>

---

## Application Development

* **Programming Language** - Dart, Java, Kotlin
* **Development Tool** - Flutter

---

## Development Tools

### Code Snippets (Firebase Authentication)

```Dart
class AuthService {
  final FirebaseAuth _auth = FirebaseAuth.instance;

  //create user object on FireBaseUser
  User _userFromFirebaseUser(FirebaseUser user) {
    return user != null ? User(uid: user.uid) : null;
  }

  // auth change user stream
  Stream<User> get user {
    return _auth.onAuthStateChanged
        // .map((FirebaseUser user) => _userFromFirebaseUser(user));
        .map(_userFromFirebaseUser);
  }

  //sign in annonymus
  Future signInAnon() async {
    try {
      AuthResult result = await _auth.signInAnonymously();
      FirebaseUser user = result.user;
      return _userFromFirebaseUser(user);
    } catch (e) {
      print(e.toString());
      return null;
    }
  }

  //sign in with email & password
  Future signInWithEmailAndPassword(String email, String password) async {
    try {
      AuthResult result = await _auth.signInWithEmailAndPassword(
          email: email, password: password);
      FirebaseUser user = result.user;
      return _userFromFirebaseUser(user);
    } catch (e) {
      print(e.toString());
      return null;
    }
  }

  //register with email & password
  Future registerWithEmailAndPassword(String email, String password) async {
    try {
      AuthResult result = await _auth.createUserWithEmailAndPassword(
          email: email, password: password);
      FirebaseUser user = result.user;

      //create a new document for the user with the uid
      await DatabaseService(uid: user.uid).updateUserData('0', 'Sudhanshu', 100);
      return _userFromFirebaseUser(user);
    } catch (e) {
      print(e.toString());
      return null;
    }
  }

  //sign out
  Future signOut() async {
    try {
      return await _auth.signOut();
    } catch (e) {
      print(e.toString());
      return null;
    }
  }
 }
```


### Tools Used

* [Flutter](https://flutter.dev/) 
  - Flutter is a framework for **Cross-Platform Development** on which we can make applications for both iOS and Android.
  - Flutter is Google’s UI toolkit for building beautiful, natively compiled applications for mobile, web, and desktop from a single codebase.
* [Firebase](https://firebase.google.com/) - A comprehensive app development platform support system in [Google Cloud Platform](https://cloud.google.com/).
  - [Firebase - Authentication](https://firebase.google.com/products/auth) - Authenticate users simply and securely.
  - [Firebase - Performance Monitoring](https://firebase.google.com/products/performance) - Gain insight into your app's performance.
  

### Documentation

* [Flutter - Docs](https://flutter.dev/docs) 
* [Firebase - Docs](https://firebase.google.com/docs)

### Testing 

* [Flutter Testing](https://flutter.dev/docs/testing) - Automated tests help ensure that your app performs correctly before you publish it, while retaining your feature and bug fix velocity.
* [Firebase - TestLab](https://firebase.google.com/products/test-lab) - Test your app on devices hosted in a Google data center.

---

## Design

* [Flutter - Cookbook](https://flutter.dev/docs/cookbook) 
* [Google Fonts](https://fonts.google.com/) - Google Fonts is a library of 991 free licensed font families.
* [Iconfinder](https://www.iconfinder.com/) - 2,775,000+ free and premium vector icons. SVG, PNG, AI, CSH and PNG format.

---

## Deployment

Apk Link:   

 <a href="https://github.com/itssudhanshu/CareIndia/blob/master/CareIndia_v1.0.0_Light.apk?raw=true">
    <img src="https://img.shields.io/badge/Download App-CareIndia-blue.svg?style=for-the-badge">
  </a>  

<h3>Building</h3>

Android Release: `flutter build apk` 

Android (arm64-v8a)/(armeabi-v7a): `flutter build apk --split-per-abi`  

If you have a connected device or emulator you can run and deploy the app with `flutter run` 

---
