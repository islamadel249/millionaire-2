<!-- LOVABLE:BEGIN -->
> [!IMPORTANT]
> This project is connected to [Lovable](https://lovable.dev). Avoid rewriting
> published git history — force pushing, or rebasing/amending/squashing commits
> that are already pushed — as it rewrites history on Lovable's side and the
> user will likely lose their project history.
>
> Commits you push to the connected branch sync back to Lovable and show up in
> the editor, so keep the branch in a working state.
<!-- LOVABLE:END -->

## Architecture rules
- Game rules live in a pure reducer (`src/lib/quiz/engine.ts`); UI only dispatches actions — keeps transitions testable and prevents double scoring.
- Timer uses absolute deadlines (`timer.ts`), never per-second decrements — accurate after tab throttling/refresh.
- All data is browser localStorage (`storage.ts`), no backend — app must work offline at a school.
- Presenter window owns state; display windows mirror it via BroadcastChannel + storage events — supports a second screen without a server.
- Sounds are generated with Web Audio (`sound.ts`) — no licensed asset files needed.
