# API Integration in Flutter

![API Integration](https://miro.medium.com/v2/resize:fit:1400/1*7M9bxaWVFUVvnMqXZLhj2g.png)

## Working with REST APIs

Learn how to integrate REST APIs into your Flutter applications effectively.

### HTTP Package Setup

Add the HTTP package to your `pubspec.yaml`:

```yaml
dependencies:
  http: ^1.1.0
```

### Making GET Requests

```dart
import 'package:http/http.dart' as http;
import 'dart:convert';

Future<List<User>> fetchUsers() async {
  final response = await http.get(
    Uri.parse('https://jsonplaceholder.typicode.com/users'),
    headers: {'Content-Type': 'application/json'},
  );
  
  if (response.statusCode == 200) {
    List<dynamic> data = json.decode(response.body);
    return data.map((json) => User.fromJson(json)).toList();
  } else {
    throw Exception('Failed to load users');
  }
}
```

### Making POST Requests

```dart
Future<User> createUser(User user) async {
  final response = await http.post(
    Uri.parse('https://jsonplaceholder.typicode.com/users'),
    headers: {'Content-Type': 'application/json'},
    body: json.encode(user.toJson()),
  );
  
  if (response.statusCode == 201) {
    return User.fromJson(json.decode(response.body));
  } else {
    throw Exception('Failed to create user');
  }
}
```

### Error Handling

Always handle potential errors:

```dart
Future<List<User>> fetchUsersWithErrorHandling() async {
  try {
    final response = await http.get(
      Uri.parse('https://jsonplaceholder.typicode.com/users'),
    ).timeout(const Duration(seconds: 10));
    
    if (response.statusCode == 200) {
      List<dynamic> data = json.decode(response.body);
      return data.map((json) => User.fromJson(json)).toList();
    } else {
      throw HttpException('HTTP ${response.statusCode}: ${response.reasonPhrase}');
    }
  } on SocketException {
    throw NetworkException('No internet connection');
  } on TimeoutException {
    throw NetworkException('Request timeout');
  } catch (e) {
    throw Exception('Unexpected error: $e');
  }
}
```

### Using FutureBuilder

Display API data in your UI:

```dart
FutureBuilder<List<User>>(
  future: fetchUsers(),
  builder: (context, snapshot) {
    if (snapshot.hasData) {
      return ListView.builder(
        itemCount: snapshot.data!.length,
        itemBuilder: (context, index) {
          final user = snapshot.data![index];
          return ListTile(
            title: Text(user.name),
            subtitle: Text(user.email),
          );
        },
      );
    } else if (snapshot.hasError) {
      return Center(child: Text('Error: ${snapshot.error}'));
    }
    return const Center(child: CircularProgressIndicator());
  },
)
```

### Best Practices

1. **Use proper error handling** for network requests
2. **Show loading states** while fetching data
3. **Cache data locally** when appropriate
4. **Use timeouts** to prevent hanging requests
5. **Validate data** before using it

> API integration is essential for modern mobile applications. Always prioritize user experience with proper loading states and error handling.