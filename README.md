# Vela — Screen-aware assistant prototype

Vela is a small, dependency-free browser prototype exploring how an assistant could help explain what is on your screen.

- [Try the live prototype](https://abishithgg.github.io/vela-screen-assistant-prototype/)
- [View the GitHub repository](https://github.com/abishithgg/vela-screen-assistant-prototype)

> **Status:** This is a product concept, not a production screen-reading assistant. Its answers are sample text; no AI or vision model is connected.

## What works today

- Three interactive views: onboarding, a sample chat, and history/privacy settings.
- User-started browser screen sharing through `navigator.mediaDevices.getDisplayMedia()`.
- A local video preview of the tab, window, or screen selected in the browser’s sharing picker.
- Clear stop behavior when you click **Stop sharing**, the browser ends sharing, you leave the chat view, or the page is closed.
- Sample Q&A is disabled while screen sharing is active, because Vela does not analyze the live preview.

The sample page, answers, conversation history, and settings are demo content. They are not backed by an account, database, or AI service.

## Privacy notes

- Screen sharing starts only after you click **Share screen** and choose a source in the browser’s native picker.
- The captured stream is shown in the page’s video preview. This prototype does not extract, upload, or save screen frames.
- The browser controls the sharing permission and shows its own sharing indicator. You can stop sharing from Vela or from the browser’s sharing controls.
- Choose a different tab or window for a clean preview; sharing the tab running Vela can make the preview repeat inside itself.
- Use a non-sensitive screen when testing. Do not share private messages, passwords, or confidential information.

## Run it locally

You need Git and a browser that supports the Screen Capture API. There is no package install or build step.

```sh
git clone https://github.com/abishithgg/vela-screen-assistant-prototype.git
cd vela-screen-assistant-prototype
python3 -m http.server 8000
```

Open <http://localhost:8000> in your browser. Screen capture requires a secure context, so use `localhost` or the HTTPS GitHub Pages site rather than relying on a `file://` URL. Browser and operating-system support for the native picker can vary.

## Project structure

```text
index.html   Complete app: markup, styles, and prototype interactions
README.md    Project overview and contributor guide
```

## Contributing

Small, focused improvements are easiest to review. To propose a change:

1. Create a branch from `main`.
2. Edit the standalone page or this README; keep the project dependency-free unless a new dependency is discussed first.
3. Run the page locally and check both desktop and mobile layouts.
4. For screen-sharing changes, test allowing and cancelling the browser picker, stopping from Vela, stopping from the browser, and leaving the chat view. Use a safe, non-sensitive source.
5. Open a pull request with a short summary and the checks you ran.

### Before submitting a screen-sharing change

- Keep capture behind an explicit user click and let the browser’s native picker choose the source.
- Stop every media track when sharing ends or the page no longer needs the stream.
- Do not add frame extraction, uploads, recording, or storage without a separately reviewed privacy design.
- Keep the UI clear that the current Q&A is sample-only and cannot analyze a live screen.
- Preserve keyboard access, visible focus states, and reduced-motion support.

## License

No license is included yet. Please check with the repository owner before reusing this project outside the repository.
