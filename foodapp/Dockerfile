# Use Flutter 3.27 (which includes Dart 3.6.1)
FROM ghcr.io/cirruslabs/flutter:3.27.3

# Optional: create non-root user to avoid warnings
RUN useradd -m app
USER app
WORKDIR /app

# Bring in pubspec files first (for Docker caching)
COPY pubspec.* ./
RUN flutter pub get

# Copy full source after dependencies
COPY . .

# Build release APK
RUN flutter build apk --release

# Optional: do nothing on run
CMD ["echo", "Build complete"]