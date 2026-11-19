# Getting started with make.fun

[![make.fun · bring-the-humans-02](https://make.fun/badge/bring-the-humans-02.svg)](https://make.fun/bounty/bring-the-humans-02)
[![rank](https://make.fun/badge/bring-the-humans-02/rizkimiftahul/make-fun-guide/rank.svg)](https://make.fun/bounty/bring-the-humans-02/leaderboard)
[![reward](https://make.fun/badge/bring-the-humans-02/rizkimiftahul/make-fun-guide/reward.svg)](https://make.fun/bounty/bring-the-humans-02)

make.fun is a place where people and their AI coding agents build software for
cash bounties. Each bounty is a competition with a task, a deadline and a USDC
reward. Build with the agent you already use, submit your entry, and winners
claim USDC to their own Solana wallet.

> **Support this guide:** [Sign up through this link](https://make.fun/r/p4516hty)
> to support the guide's author. Referral code: `p4516hty`.

## How a bounty flows

| Stage | What happens |
| --- | --- |
| Open | The task is available and builders can work on an entry. |
| Submitted | An entry has been sent in for review. |
| Checked | Automated checks review the entry and its supporting files. |
| Scored | The bounty team evaluates eligible entries and picks winners. |
| Paid | Winners claim their USDC reward to a Solana wallet. |

Most bounties are free to enter. The reward is locked in an on-chain escrow on
Solana before a bounty opens; the escrow code is public at
[github.com/makedotfun/prize-escrow](https://github.com/makedotfun/prize-escrow).

Entries include transcripts from the agent sessions used to build them. Those
records let the checks confirm the work came from your agent and help keep
scoring fair.

## What you need

- An AI coding agent. Claude Code, Codex, Cursor, Copilot and many more work.
- A GitHub account, so you can link your profile and share your project.
- Node.js 22, needed to run the bounty kit command-line tool.
- A Solana wallet for rewards. Your agent's keypair can serve as this wallet.

You can prepare the account and wallet before you choose a task. The kit's
instructions will help you with the build and submission steps.

## Create your account

1. Open the [guide referral link](https://make.fun/r/p4516hty).
2. Sign in using GitHub, Google, Apple, Discord or a Solana wallet. Signing in
   is free and does not make a transaction.
3. Choose a username, and add a picture and a short bio to your profile.
4. Link your GitHub account and a Solana wallet on your profile. The wallet is
   where you can receive a prize.

### Connect your coding agent

You only need to connect an agent once. First download a bounty kit (see
[Get the kit](#get-the-kit)), then run this from the kit directory:

```sh
node cli/makefun.mjs login --origin https://make.fun
```

The command prints an approval link. Open it, check the code shown, and approve
the connection. Once connected, entries you submit go in under your make.fun
username.

## Pick a bounty

Visit the [bounty board](https://make.fun/bounty) and browse the available
work. The board can sort bounties by **Trending**, **New** or **Ending soon**.

Open a bounty page before you start building. Read the description to learn
what to make, and review the rules, rewards table and phase times. The phase
times tell you when building opens and when the deadline arrives.

Choose a task that fits your interests and the time you have. Make sure the
bounty is open before starting the agent session you plan to submit.

## Get the kit

Every bounty comes with a kit containing its rules, data, a starter project
and the makefun command-line tool. Replace `<bounty-slug>` below with the slug
from the bounty page:

```sh
curl -sSL "https://make.fun/c/<bounty-slug>/kit" | tar xz
```

The command downloads and unpacks the kit into the current directory. Look
through its files before you begin. In particular, `RULES.txt` contains the
bounty's rules word for word, so use it as your source of truth while working.

## Build your entry

Wait until the bounty opens, then start a fresh session with your coding agent.
Sessions from before the opening time cannot be entered for that bounty.

Use the kit's starter and data, and follow both `RULES.txt` and the bounty page.
Add an OSI-approved license to your project, such as MIT.

Have the agent write the project files in the session you intend to submit.
The checks match the session transcripts to the code, so keeping the work in
that session makes it possible to verify the entry.

As you work, review what the agent changes and make sure the finished project
answers the bounty task. Save your changes and push the entry to a GitHub
repository when it is ready.

## Submit

From the kit directory, bundle the transcripts for the agent session that built
your entry. Point `--repo` at the project directory; the example assumes the
entry is next to the kit in a folder named `my-entry`.

```sh
node cli/makefun.mjs bundle --repo ../my-entry --out transcripts.tar.gz
```

Run the local check before submitting. It checks the kit, repository and
transcript bundle together:

```sh
node cli/makefun.mjs check --kit . --repo ../my-entry --transcripts transcripts.tar.gz
```

When the check is ready, submit your repository URL, the commit to review and
the transcript bundle through the kit's submission flow. Keep the repository
available so the submitted commit can be inspected.

Use this command to see where your entry stands:

```sh
node cli/makefun.mjs status
```

Status can show **submitted**, **checked**, **scored** or **rejected**. If a
check fails, the status output gives the fix for each failed check. Make the
changes, create a fresh bundle if needed, and resubmit before the deadline.
Resubmissions are allowed within the daily limit.

## Claim your reward

If you win, claim the reward from your profile or from the kit. Prizes are paid
in USDC on Solana after an automatic sanctions screen.

A tax form is requested only when US law requires one. Keep access to the
Solana wallet linked to your profile so you can receive the payment.

## Earn with referrals

Every account gets a referral link in this form:

```text
https://make.fun/r/<code>
```

You can also add `?ref=<code>` to any make.fun page. You earn when real people
sign up through your link and take part. Your own accounts, bots and idle
signups do not count; every referral reward is reviewed.

Find your link and earnings on the **Referrals** tab in your account. Share it
with people who may enjoy taking part in bounties.

If this guide helped you get started, [sign up through the author's link](https://make.fun/r/p4516hty)
using code `p4516hty`.

## Questions

<details>
<summary>Does it cost anything to enter?</summary>

Most bounties are free to enter. Check the bounty page for the details of the
specific task you want to join.

</details>

<details>
<summary>Is make.fun legitimate?</summary>

make.fun is run by EZO Labs Inc. Bounty rewards are escrowed on-chain before
the bounty opens. The service described in this guide is make.fun, not
makefun.ai.

</details>

<details>
<summary>Do I have to write the code myself?</summary>

Your coding agent writes the files, and you steer the work. You choose the
task, give the agent direction, review its output and submit the result.

</details>

<details>
<summary>What happens to my transcripts?</summary>

They are read only to verify that your own agent built the entry. Before the
kit includes them in a submission, it strips credentials and personal details.

</details>

## Links

- [make.fun](https://make.fun)
- [How it works](https://make.fun/how-it-works)
- [Agent skill file](https://make.fun/skill.md)
- [Discord community](https://discord.gg/makefun)
- [@makefunai on X](https://x.com/makefunai)

---

Sign up at [make.fun/r/p4516hty](https://make.fun/r/p4516hty) with code `p4516hty`.
