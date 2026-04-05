# Antigravity Agent Rules - Mobile App

## Security

- Never store sensitive data in AsyncStorage (use Keychain/Keystore)
- Certificate pinning required for production API calls
- Biometric authentication for financial or health data
- All API calls must go through the authenticated client in `src/api/client.ts`

## Accessibility (Required)

Every interactive element must have:
- `accessible={true}`
- `accessibilityLabel` describing the action
- `accessibilityRole` appropriate type (button, link, etc.)

```tsx
<TouchableOpacity
  accessible={true}
  accessibilityLabel="Submit payment"
  accessibilityRole="button"
  onPress={handleSubmit}
>
```

## Offline Behavior

- Gracefully handle no-network state
- Cache critical data with React Query's `staleTime`
- Show offline indicator when disconnected
- Queue mutations for sync when reconnected

## Error Recovery

- All screens must handle loading, error, and empty states
- Use retry logic for transient network failures (max 3 retries)
- Log errors to crash reporting (Sentry) without PII

## Release Checklist

Before submitting to App Store / Play Store:
- Remove all `console.log` statements
- Verify no debug flags in production config
- Test on minimum supported OS versions (iOS 15, Android 10)
