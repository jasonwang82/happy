# CodeBuddy Integration

This document describes the CodeBuddy Code integration that was added to the Happy coder mobile client.

## What Was Added

1. **CodeBuddy Connect Page** (`sources/app/(app)/settings/connect/codebuddy.tsx`)
   - Similar to Claude Code integration
   - Shows terminal command: `happy connect codebuddy`
   - Users run this command to connect their CodeBuddy account

2. **CodeBuddy Icon** (`sources/assets/images/icon-codebuddy.png`)
   - **IMPORTANT**: Currently using Claude icon as placeholder
   - **TODO**: Replace with actual CodeBuddy branding/icon
   - Should be 156x156 PNG with transparency

3. **Avatar Component Update** (`sources/components/Avatar.tsx`)
   - Added 'codebuddy' to the flavorIcons map
   - CodeBuddy avatars now display with proper icon overlay

4. **Settings View Integration** (`sources/components/SettingsView.tsx`)
   - Added CodeBuddy to "Connected Accounts" section
   - Includes connect/disconnect functionality
   - Shows active/inactive status

5. **Translations** (all language files)
   - Added `codeBuddyAuthSuccess` key to:
     - English (en): "Successfully connected to CodeBuddy"
     - Catalan (ca): "Connexió amb CodeBuddy realitzada amb èxit"
     - Spanish (es): "Conectado exitosamente con CodeBuddy"
     - Polish (pl): "Pomyślnie połączono z CodeBuddy"
     - Portuguese (pt): "Conectado ao CodeBuddy com sucesso"
     - Russian (ru): "Успешно подключено к CodeBuddy"
     - Chinese Simplified (zh-Hans): "成功连接到 CodeBuddy"

## How It Works

The integration follows the same pattern as Claude Code:

1. User navigates to Settings > Connected Accounts
2. Taps "CodeBuddy Code" 
3. App shows terminal command to run
4. User runs `happy connect codebuddy` on their computer
5. The happy CLI handles the OAuth/connection flow
6. Status updates in the app via the sync service

## Backend Requirements

The backend server (happy-server) must support:
- `/v1/connect/codebuddy/register` endpoint
- Storing 'codebuddy' in profile.connectedServices array
- Disconnecting via DELETE `/v1/connect/codebuddy`

## CLI Requirements

The happy CLI must support:
- `happy connect codebuddy` command
- CodeBuddy authentication flow
- Similar to existing `happy connect claude` implementation
- Support for `codebuddy --acp` protocol integration

## Testing

To test the integration:
1. Build and run the app
2. Navigate to Settings > Connected Accounts
3. Verify CodeBuddy Code appears in the list
4. Try tapping it to see the connect page
5. Verify the terminal command is displayed correctly

## Future Improvements

1. Replace placeholder icon with actual CodeBuddy branding
2. Add ACP protocol specific features if needed
3. Add CodeBuddy-specific settings/configuration options
4. Consider adding CodeBuddy to agent type selections in chat views
