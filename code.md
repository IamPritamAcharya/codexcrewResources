# Flutter Markdown with GitHub-Style Syntax Highlighting

This implementation provides GitHub-style syntax highlighting for Flutter markdown using the `flutter_highlighter` package.

## Installation

Add these dependencies to your `pubspec.yaml`:

```yaml
dependencies:
  flutter:
    sdk: flutter
  flutter_markdown: ^0.6.18
  flutter_highlighter: ^0.1.1
  markdown: ^7.1.1
```

## Features

✅ **GitHub-style syntax highlighting** for code blocks  
✅ **Pale color scheme** for headings and elements  
✅ **JetBrains Mono font** for code (with fallbacks)  
✅ **Dark and light themes** with proper contrast  
✅ **Language detection** from code fence language tags  
✅ **Horizontal scrolling** for long code lines  
✅ **Custom element builders** for advanced styling  

## Usage

### Basic Usage

```dart
import 'package:flutter/material.dart';
import 'markdown_styles.dart'; // Your markdown styles file

class MyMarkdownPage extends StatelessWidget {
  final String markdownContent = '''
# Hello World

Here's some `inline code` and a code block:

```dart
void main() {
  print('Hello, Flutter!');
}
```

```python
def greet(name):
    print(f"Hello, {name}!")
    
greet("World")
```
''';

  @override
  Widget build(BuildContext context) {
    final isDark = Theme.of(context).brightness == Brightness.dark;
    
    return Scaffold(
      appBar: AppBar(title: Text('Markdown Demo')),
      body: SingleChildScrollView(
        padding: EdgeInsets.all(16),
        child: StyledMarkdownWidget(
          data: markdownContent,
          isDark: isDark,
        ),
      ),
    );
  }
}
```

### Advanced Usage with Custom Theme

```dart
import 'package:flutter/material.dart';
import 'package:flutter_markdown/flutter_markdown.dart';
import 'markdown_styles.dart';

class CustomMarkdownViewer extends StatelessWidget {
  final String markdownData;
  final bool isDarkMode;

  const CustomMarkdownViewer({
    Key? key,
    required this.markdownData,
    this.isDarkMode = false,
  }) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return Container(
      padding: EdgeInsets.all(16),
      decoration: BoxDecoration(
        color: isDarkMode ? Color(0xFF0F172A) : Colors.white,
        borderRadius: BorderRadius.circular(12),
      ),
      child: Markdown(
        data: markdownData,
        shrinkWrap: true,
        physics: NeverScrollableScrollPhysics(),
        styleSheet: isDarkMode 
            ? MarkdownStyles.darkTheme 
            : MarkdownStyles.lightTheme,
        builders: isDarkMode
            ? MarkdownStyles.getDarkElementBuilders()
            : MarkdownStyles.getLightElementBuilders(),
        selectable: true,
        onTapLink: (text, href, title) {
          // Handle link taps
          print('Tapped link: $href');
        },
      ),
    );
  }
}
```

## Supported Languages

The syntax highlighter supports all languages that `flutter_highlighter` supports, including:

- **Dart** - `dart`
- **JavaScript** - `javascript`, `js`
- **TypeScript** - `typescript`, `ts`
- **Python** - `python`, `py`
- **Java** - `java`
- **C++** - `cpp`, `c++`
- **C#** - `csharp`, `cs`
- **Swift** - `swift`
- **Kotlin** - `kotlin`
- **Go** - `go`
- **Rust** - `rust`
- **HTML** - `html`
- **CSS** - `css`
- **SQL** - `sql`
- **JSON** - `json`
- **YAML** - `yaml`
- **XML** - `xml`
- **Bash** - `bash`, `sh`
- **PowerShell** - `powershell`
- **And many more...**

## Color Scheme

### Dark Theme
- **H1**: Pale Purple (`#C4B5FD`)
- **H2**: Pale Blue (`#93C5FD`)
- **H3**: Pale Teal (`#67E8F9`)
- **H4**: Pale Green (`#86EFAC`)
- **H5**: Pale Yellow (`#FDE047`)
- **H6**: Pale Pink (`#F9A8D4`)
- **Code Background**: GitHub Dark (`#0D1117`)

### Light Theme
- **H1**: Soft Purple (`#8B5CF6`)
- **H2**: Soft Blue (`#3B82F6`)
- **H3**: Soft Teal (`#06B6D4`)
- **H4**: Soft Green (`#10B981`)
- **H5**: Soft Yellow (`#F59E0B`)
- **H6**: Soft Pink (`#EC4899`)
- **Code Background**: GitHub Light (`#F6F8FA`)

## Customization

### Custom Fonts

To use JetBrains Mono font, add it to your `pubspec.yaml`:

```yaml
flutter:
  fonts:
    - family: JetBrains Mono
      fonts:
        - asset: assets/fonts/JetBrainsMono-Regular.ttf
        - asset: assets/fonts/JetBrainsMono-Bold.ttf
          weight: 700
```

### Custom Colors

You can modify the color constants in the `MarkdownStyles` class to match your app's theme:

```dart
// Custom pale colors
static const Color _customPurple = Color(0xFFB19CD9);
static const Color _customBlue = Color(0xFF87CEEB);
// ... add more custom colors
```

### Custom Element Builders

Add your own custom element builders:

```dart
static Map<String, MarkdownElementBuilder> getCustomElementBuilders() {
  return {
    'custom-element': (context, node, next) {
      return Container(
        // Your custom widget
      );
    },
    ...MarkdownStyles.getDarkElementBuilders(),
  };
}
```

## Performance Tips

1. **Use `shrinkWrap: true`** for markdown widgets inside scrollable containers
2. **Set `physics: NeverScrollableScrollPhysics()`** when the parent handles scrolling
3. **Use `selectable: true`** only when text selection is needed
4. **Consider using `SingleChildScrollView`** for long markdown content

## Example Output

The styled markdown will look like GitHub's markdown with:
- Proper syntax highlighting for code blocks
- Pale, readable colors for headings
- Professional typography
- Consistent spacing and alignment
- Responsive design for different screen sizes

This implementation provides a professional, GitHub-like markdown experience in your Flutter applications!
