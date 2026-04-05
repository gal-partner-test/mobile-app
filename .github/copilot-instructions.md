# GitHub Copilot Instructions - Mobile App

## Stack
React Native (Expo SDK 50), TypeScript 5, React Navigation 6, React Query, Jest + RNTL.

## Component Template
```tsx
import React from 'react';
import { View, Text, StyleSheet } from 'react-native';

interface ScreenProps {
  title: string;
}

export const ExampleScreen: React.FC<ScreenProps> = ({ title }) => {
  return (
    <View style={styles.container}>
      <Text style={styles.title}>{title}</Text>
    </View>
  );
};

const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: '#fff',
  },
  title: {
    fontSize: 24,
    fontWeight: '600',
  },
});
```

## API Hook Template
```typescript
export const useUserProfile = (userId: string) => {
  return useQuery({
    queryKey: ['profile', userId],
    queryFn: () => api.users.getProfile(userId),
    staleTime: 5 * 60 * 1000,  // 5 min
  });
};
```

## Platform-Specific Code
```typescript
// Use Platform.select for platform-specific styles/values
const shadowStyle = Platform.select({
  ios: { shadowColor: '#000', shadowOpacity: 0.1, shadowRadius: 4 },
  android: { elevation: 4 },
});
```
