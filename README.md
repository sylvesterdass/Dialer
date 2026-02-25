# Dialer (Twilio-ready Android app scaffold)

This repository now contains a Jetpack Compose Android dialer scaffold designed to mirror key Google Dialer patterns and integrate with Twilio Voice.

## Included features

- **Dial pad with T9 contact search** (type numbers and filter contacts by mapped letters).
- **Theme switcher** between light and dark mode.
- **Haptic feedback** on dial-pad taps and incoming-call actions.
- **Incoming call screen** with **Accept** and **Reject** actions.
- **Active call duration timer** displayed on the dial screen.
- **Audio route selector** for **Earpiece / Speaker / Bluetooth**.
- **Call logs** showing:
	- missed-call ringing time (`Rang for`),
	- completed-call duration (`Call duration`).
- **Caller ID picker** on the dial screen bottom area, inspired by apps like Spoke Phone, to choose the outbound number.
- **Contacts screen** sorted alphabetically with an alphabetical letter rail for quick scanning.

## Project layout

- `app/src/main/java/com/example/dialer/ui` – Compose screens, state, theme.
- `app/src/main/java/com/example/dialer/model` – Domain models.
- `app/src/main/java/com/example/dialer/data` – Fake repository/sample data.
- `app/src/main/java/com/example/dialer/twilio` – Twilio integration seam (`TwilioVoiceManager`) with TODO hooks.

## Twilio integration notes

`TwilioVoiceManager` is intentionally a clean seam with TODO markers for:

1. `Voice.connect(...)` for outgoing calls,
2. registering for incoming calls,
3. accepting/rejecting incoming invites,
4. disconnecting active calls.

To productionize this app:

- Provision Twilio access tokens from your backend,
- Add push registration + incoming call notification handling,
- Run Twilio call lifecycle callbacks into `DialerViewModel`,
- Persist contacts/logs into a local database.

## Build note

A local Gradle wrapper is not generated in this environment due Java/Gradle compatibility constraints on the host image. Add a standard Android Gradle wrapper (`gradlew`) in your development machine/CI and run `./gradlew assembleDebug`.
