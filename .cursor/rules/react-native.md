# Cursor Rules - React Native App

## Platform Conventions
- Use `Platform.OS` checks sparingly; prefer platform-agnostic abstractions
- Expo SDK for device APIs (camera, location, notifications)
- Navigation: React Navigation v6

## Performance Rules
- Use `FlatList` for lists, never `ScrollView` with map
- Memoize list item components with `React.memo`
- Use `useCallback` for handlers passed to list items
- Avoid `setState` in render functions
- Profile with Flipper before optimizing

## Styling
- StyleSheet.create() for all styles (enables optimization)
- No inline style objects in render (creates new objects each render)
- Design tokens from `src/theme/tokens.ts`

## Navigation
```typescript
// Typed navigation params
type RootStackParams = {
  Home: undefined;
  Profile: { userId: string };
  Settings: undefined;
};

const navigation = useNavigation<StackNavigationProp<RootStackParams>>();
```

## State
- Local: useState / useReducer
- Server: React Query with offline support
- Persistent: AsyncStorage or MMKV for large data

## Testing
- Jest + React Native Testing Library
- Mock native modules in `__mocks__/`
- Detox for E2E on device
