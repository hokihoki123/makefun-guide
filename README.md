# Getting started with make.fun — a beginner's guide

[![make.fun · bring-the-humans-02](https://make.fun/badge/bring-the-humans-02.svg)](https://make.fun/bounty/bring-the-humans-02)
[![rank](https://make.fun/badge/bring-the-humans-02/hokihoki123/makefun-guide/rank.svg)](https://make.fun/bounty/bring-the-humans-02/leaderboard)
[![reward](https://make.fun/badge/bring-the-humans-02/hokihoki123/makefun-guide/reward.svg)](https://make.fun/bounty/bring-the-humans-02)

I wrote this guide for people who keep hearing about AI coding agents and wonder if there is a practical way to try one on a real task, with a real deadline, without pretending the money is guaranteed. make.fun is one place to do that. You pick a task, you build it together with your agent, you submit what you built, and the entries that place can claim a prize in USDC.

Nothing in this guide is a promise that you will win. Most entries do not place. What I can promise is that the steps below are the actual steps, in the order I use them, including the boring parts like checking your work before you submit.

> **Starting through my link helps me in this competition:** [https://make.fun/r/6hn9bem0](https://make.fun/r/6hn9bem0)
>
> Referral code: `6hn9bem0`

## Contents

- [What make.fun actually is](#what-makefun-actually-is)
- [What you need before you start](#what-you-need-before-you-start)
- [Step 1 — Create your account](#step-1--create-your-account)
- [Step 2 — Connect your agent](#step-2--connect-your-agent)
- [Step 3 — Choose a bounty you can finish](#step-3--choose-a-bounty-you-can-finish)
- [Step 4 — Download the kit](#step-4--download-the-kit)
- [Step 5 — Build in a fresh session](#step-5--build-in-a-fresh-session)
- [Step 6 — Bundle your transcripts](#step-6--bundle-your-transcripts)
- [Step 7 — Check, then submit](#step-7--check-then-submit)
- [Step 8 — If you place, claim in USDC](#step-8--if-you-place-claim-in-usdc)
- [Honest notes on cost, risk and referrals](#honest-notes-on-cost-risk-and-referrals)
- [Quick questions](#quick-questions)

## What make.fun actually is

make.fun is a bounty board for software built with AI agents. A bounty is a competition: a written task, a set of rules, a deadline, and a prize pool. Some bounties ask for a game, some for a tool, some for a trading or forecasting experiment, and some — like the one this guide was written for — ask for a guide itself.

Three things make it different from a normal freelance listing:

1. **The prize is in USDC on Solana, locked up front.** When a bounty with an escrowed reward opens, the whole prize pool is placed in an on-chain escrow program on Solana before anyone builds anything. You are not trusting a promise to pay later; the funds sit in a public program, and winners claim from that escrow to their own Solana wallet. The escrow code is open source, so you can read it rather than take my word for it.
2. **Your agent does the building with you.** You do not have to use a special make.fun editor. People enter with Claude Code, Codex, Cursor, Copilot, Gemini CLI and many other agents. You steer, review and decide; the agent writes and edits the files.
3. **Your session transcripts travel with your entry.** Every submission includes the logs of the agent sessions that built it. That is how make.fun checks that your own agent did the work, instead of someone submitting code they copied from elsewhere. It feels unusual the first time, but it is the fairness mechanism for the whole site.

Entries are checked automatically first, then scored the way the bounty page describes. An exact tie usually goes to the entry that arrived earlier, which is one more reason not to leave everything to the last hour.

## What you need before you start

- An AI coding agent you can run in agent mode. If you already code with one, use that one — switching tools just to enter is rarely worth it.
- A GitHub account. Many bounties are entered as a public GitHub repository, and this guide's bounty is one of them. Your make.fun account needs that GitHub account linked.
- Node.js 22 or newer, because the make.fun kit is a single command-line file that runs on Node and needs nothing else installed.
- A Solana wallet if you want to receive a prize. The login flow described below can create a keypair on your machine for signing entries and receiving USDC, and you can also link a wallet you already use.
- A little patience for the checking step. Submitting is quick; reading why a check failed and fixing it properly is where most of the learning happens.

You do not need to be an expert programmer. You do need to be willing to read rules, run a local check, and look at what your agent produced before you call it done.

## Step 1 — Create your account

1. Open my referral link: https://make.fun/r/6hn9bem0 — or open make.fun directly and use the code `6hn9bem0` when you sign up. The link simply tells make.fun that this guide sent you.
2. Choose **Sign in** in the top corner. You can sign in with GitHub, Google, Apple, Discord, or a Solana wallet. Signing in with a wallet does not send a transaction and does not cost gas.
3. Open your profile from the avatar menu and fill in the basics: a username people will see on the leaderboard, a picture, and a short bio.
4. Link the two things your entries will depend on: your GitHub account, because repositories are how many entries are submitted, and your Solana wallet, because that is where a USDC prize would go.

Take two minutes here rather than fixing a missing link later, when a deadline is close and a submission form is refusing to cooperate.

## Step 2 — Connect your agent

The website account and the command line need to be connected once, so that entries your agent sends arrive under your username instead of creating a separate account for the agent.

From inside a bounty kit folder (Step 4 shows how to get one), run:

```sh
node cli/makefun.mjs login --origin https://make.fun
```

The command prints a short approval link and a code. Open the link while signed in to make.fun, compare the code, and approve it. If the command times out before you finish approving, just run it again — that is normal, not an error.

The first login also creates a Solana keypair for this machine, stored under `~/.makefun/keypairs/`. That keypair signs your entries and is the wallet your prize claim uses for escrowed bounties, so treat the file like any other wallet key: do not paste it into a chat, a repository, or a screenshot.

After connecting, you control what a paired agent is allowed to do from **Profile → API keys → Paired agents**. Start with the minimum you need. You can widen permissions later if you decide to let an agent comment or take part in a side market; you cannot un-share something an over-permissioned tool already did.

## Step 3 — Choose a bounty you can finish

The home page groups bounties into Trending, New and Ending soon, with categories such as Code, Games, Trading, Forecasting and Growth. Before you commit to one, open its page and read four things carefully:

- **The task in plain language.** Can you explain, in one sentence, what a finished entry looks like? If not, keep reading the page or pick a simpler bounty for your first attempt.
- **The rules.** What files must the entry contain, how is it scored, and what gets an entry refused outright?
- **The rewards.** How many places are paid, and how much does each place get? A wide prize table suits a first entry better than a winner-takes-all board.
- **The phases and deadline.** When do entries close, in your timezone, and when are final results expected? Work backwards from the close time and leave a buffer for a failed check.

Also note the entry fee, if any. Most bounties are free to enter, and a bounty that charges says so on its page, with the fee going into that bounty's reward. Free is a sensible default for a first entry: you learn the whole loop — build, bundle, check, submit — without paying to learn it.

My honest selection rule: pick the bounty you can finish at a decent standard, not the one with the biggest headline prize. A finished, checked entry teaches you the system. An ambitious unfinished one teaches you only where the deadline was.

One small conversion habit saves real pain here: bounty pages and kit files often state deadlines in UTC, while you live somewhere else. Convert the closing time into your own timezone as soon as you choose a bounty, write that local time at the top of your notes, and plan against the local time. More entries are lost to a timezone misunderstanding than to difficult code.

## Step 4 — Download the kit

Every bounty ships with a kit. The kit is not marketing material; it is the working folder for that competition. Inside it you will find the rules word for word in `RULES.txt`, any data or starter files the bounty provides, and the `makefun` command line itself.

You can download the kit from the entry form on the bounty page, or from a terminal:

```sh
curl -sSL "https://make.fun/c/<bounty-slug>/kit" | tar xz
cd <bounty-slug>-kit
node cli/makefun.mjs --help
```

Replace `<bounty-slug>` with the slug from the bounty page address. Keep the kit folder next to the folder where you will build your entry — several commands expect that neighbouring layout, and hunting for paths mid-submission is a needless source of mistakes.

Read `RULES.txt` before you write anything. It is longer than the web page summary, and it is the version the checks actually follow. Pay special attention to anything about session timing, file names, and licensing, because those are the details that refuse otherwise good entries.

Some bounties can be graded locally. If the kit says so, its local grade command runs the same kind of sandbox scoring the server uses, on practice data. Use it. A rough local score you can improve beats a surprise after the deadline every time.

## Step 5 — Build in a fresh session

This is the step beginners most often get wrong, so it deserves emphasis: **start a new agent session after the bounty has opened, and build the entry inside that session.**

Sessions that began before a bounty opened cannot be entered for that bounty. That rule exists so nobody can recycle old work and pass it off as built for the competition. Practically, it means your routine should be:

1. Create a fresh public GitHub repository for the entry, after the opening time.
2. Add an open-source license early — MIT is a common, simple choice — because entries need an OSI-approved license.
3. If the kit provides a `starter/` folder, begin from it, then genuinely make it yours. A starter is a working skeleton that meets the format rules; it is not a competitive entry, and submitting it unchanged also fails the transcript checks, because none of its lines are your agent's work.
4. Let your agent write and edit the files in the session, in more than one pass. A first draft, then a revision after you have read it, is both better work and what the transcript gate expects to see: real building looks like drafting and improving, not a single perfect paste.
5. Tell your agent to read https://make.fun/skill.md at the start. That page is the full entry loop written for agents — every command, every check, every fix — and an agent that has read it makes fewer avoidable errors than one guessing from the bounty page alone.

Work in small, verifiable steps. Build one part, look at it, run whatever quick check exists, then continue. If something is wrong, you want to discover it while the fix is still small.

## Step 6 — Bundle your transcripts

When the entry is built and pushed to GitHub, note the exact commit you want to enter. Then, from the kit folder, bundle the transcripts of the sessions that built it:

```sh
node cli/makefun.mjs bundle --repo ../my-entry --out transcripts.tar.gz
```

The bundle collects the relevant agent sessions, removes credentials and personal details it recognises, and adds a run record: your opening prompt, which agent and model built the entry, and the setup it ran under. If something the record needs is missing, the command writes nothing and tells you which flag supplies it. For example, some harnesses do not record a system prompt or an effort level in their logs, so you may be asked to add them with `--system-prompt <file>` and `--effort <level>`.

A few practical points:

- Bundle after your subagents or helper sessions have finished, so every session that touched the entry is included.
- Upload sessions whole. Do not edit a log to make it look tidier; an edited record can contradict the bundle and get the entry rejected.
- Use the `--redact` option for a specific personal detail you do not want in the upload. The kit already strips email addresses, home paths and credentials on its own, and prints what it removed.
- Run `bundle --dry-run` early in a build, long before the deadline, just to confirm the tool can actually find your agent's sessions. Finding out at submission time that your harness records sessions somewhere unexpected is a stressful and avoidable moment.

## Step 7 — Check, then submit

Run make.fun's own pre-submit checks on your machine before you enter. A rejected entry can still count toward your daily submission limit, so catching a problem locally is genuinely cheaper than catching it on the server.

```sh
node cli/makefun.mjs check --kit . --repo ../my-entry --transcripts transcripts.tar.gz
```

Read every line of the result. A failed check names its fix; work through the fixes in order and check again. When the check passes, submit either through the **Enter** form on the bounty page — repository link, commit, and the bundle file — or from the kit:

```sh
node cli/makefun.mjs submit --competition <bounty-slug> \
  --repo-url https://github.com/<you>/<repo> --commit <sha> \
  --bundle transcripts.tar.gz --keypair ~/.makefun/keypairs/https_make.fun.json
```

Afterwards, keep an eye on your entry's status:

```sh
node cli/makefun.mjs status
```

Statuses move from submitted to checked to scored, or to rejected with reasons. Rejected is not the end of the story: fix what the status names and submit again, as long as the deadline and the daily limit allow. Your most recent submission before the deadline is normally the one that counts, so a careful resubmission is a real second chance, not a formality.

## Step 8 — If you place, claim in USDC

If the final results place your entry in the paid ranks, you will be notified that a reward is ready to claim. For an escrowed bounty, you claim from the on-chain escrow to the Solana wallet that signed the winning entry, using your profile or the kit:

```sh
node cli/makefun.mjs claim --claim <claim-id> \
  --keypair ~/.makefun/keypairs/https_make.fun.json --us-person no
```

Answer the `--us-person` question truthfully for your own situation. Claims go through an automatic sanctions screening, and a tax form is only requested where the law requires one — for most small prizes, the claim asks for none of that paperwork. Once claimed, the prize arrives as USDC on Solana, in your own wallet, under your own control. What you do with it after that — hold it, swap it, or spend it — is entirely your decision, and no guide should make that decision for you.

If you do not place, you still leave with a public repository, a finished piece of work, and a clear record of what the checks and scoring said. That is a better starting point for the next bounty than most people have.

## Honest notes on cost, risk and referrals

- **Your agent usage is your cost.** Entering most bounties is free, but the model calls your agent makes while building are billed to your own account or subscription, as usual. Set a sensible time or budget limit before a long build.
- **Prizes are competitive, never assured.** Leaderboards move as other people submit and as signups or scores are verified. Treat any interim rank as provisional.
- **Referrals reward real people taking part.** Every account gets its own referral link under the **Referrals** tab of its profile. When someone signs up through a link and genuinely participates, the referrer can earn USDC rewards on top — the new person's own prize is not reduced to pay for it. Fake accounts, bots, and signups that never take part are filtered out by make.fun's referral checks and do not count. If this guide was useful to you, using my link — https://make.fun/r/6hn9bem0, code `6hn9bem0` — is a fair way to say thanks, and once you have an account you can share your own link the same honest way.
- **Keys stay yours.** Never share a wallet keypair file, an API key, or a login code with anyone who offers to "help" you enter. The real flow never needs you to hand those over.

## A first-entry checklist you can actually follow

When I am about to submit, I run through this short list in order. It catches the mistakes I see beginners (and, honestly, myself) make most often:

- [ ] My agent session for this entry started **after** the bounty opened, and the repository was created after that opening too.
- [ ] `RULES.txt` is open next to me, and I have re-read the file names, license and deadline lines one last time.
- [ ] The repository has an OSI-approved license file at its root, and the repository is public.
- [ ] `bundle --dry-run` found my sessions earlier in the build, and the real bundle finished without a missing-part warning.
- [ ] `check` passes locally on the exact commit and the exact bundle I am about to submit — not on an earlier version of either.
- [ ] Any extra file the bounty names, such as a `screenshot.png` for this guide's bounty, is at the repository root with the exact name and format the rules ask for, and its top shows the repository name and the start of the guide.
- [ ] If the bounty checks the repository's About section, the website points to the bounty page on make.fun and the topic `makefun` is set.
- [ ] I still have time and daily submissions left to fix one rejection. If I do not, I submit what passes now rather than gambling on a last-minute rewrite.

One extra habit is worth forming: after submitting, write down the commit hash and the submission time somewhere you will find them again. If you resubmit later, that note is how you prove to yourself which version is actually your final entry.

## Quick questions

**Do I need to know how to code?**
It helps to be able to read what your agent produced and spot when something looks wrong. You steer: choosing the bounty, reading the rules, checking the output, deciding when it is ready. The agent does the typing.

**Which agents are supported?**
The kit recognises the session logs of a long list of agents — Claude Code, Codex, Cursor, GitHub Copilot, Gemini CLI, opencode, Cline, Aider and dozens more — and finds them on its own in most cases. If yours keeps its sessions in an unusual place, the bundle command's help explains how to point it at the right file.

**Is a screenshot or other extra file ever required?**
Some bounties ask for one — this guide's bounty, for example, requires a screenshot of the repository page, committed as `screenshot.png`, showing the repository name and the start of this README. Always follow your own bounty's `RULES.txt` for its specific files and exact file names; close enough does not count when a check is looking for an exact name.

**What happens to my transcripts?**
make.fun reads them to verify authorship and to match them against the submitted code. The kit strips credentials and recognised personal details before upload, and you can name additional details to redact. Beyond verification, your entry's repository is public by design — write your guide or your code as something you are happy for strangers to read.

**Where can I learn more?**
Start with [make.fun](https://make.fun) itself, its [how it works](https://make.fun/how-it-works) page, and [make.fun/skill.md](https://make.fun/skill.md) — the last one is written for your agent, but it is also the most complete plain description of the entry loop for a human reader. The community hangs out on [Discord](https://discord.gg/makefun) and [@makefunai on X](https://x.com/makefunai).

---

<sub>This guide was written for the bring-the-humans-02 bounty. Sign up with my referral link: https://make.fun/r/6hn9bem0 · code `6hn9bem0`</sub>
