1. Navigate to `node_modules/native-base/src/core/NativeBaseProvider.tsx`.
2. Delete the `<SSRProvider></SSRProvider>` that wraps `{children}`. Take care not to delete `{children}`.
3. Remove the `SSRProvider` import. That is, delete this line: `import { SSRProvider } from '@react-native-aria/utils';`.
4. Run `npx patch-package native-base`. Select 'yes' in the prompt.