---
layout: default
title: LifePlanner
description: A practical Markdown-to-calendar tool for keeping everyday tasks under control.
---

<div class="page-header">
  <p class="eyebrow">Planning software</p>
  <h1>Planning my everyday tasks.</h1>
  <p class="lead">Like everyone else, I struggle to keep my tasks under control. LifePlanner turns that everyday list into a simple calendar I can carry with me.</p>
</div>

<div class="prose">
  <p>Putting the rubbish out in time for pickup, washing the car, shopping, putting items up for sale: the list goes on. I have tried several ways to manage it, including filling my mobile phone calendar with reminders and beeps.</p>

  <p>That is why I created LifePlanner. Built with Luna in C#, it reads Markdown files and produces simple, printable HTML files for the week. Carrying my list with me, or keeping it on top of the table, has done wonders for my task discipline.</p>

  <p><a class="card-link" href="https://github.com/redpandoralife/life-planner">View LifePlanner on GitHub</a></p>

  <h2>From Markdown to a working calendar</h2>

  <p>LifePlanner is a .NET 10 console application for turning personal planning notes into a practical, printable schedule. It is written in C# and organized into focused projects: shared contracts and models, core scheduling rules, infrastructure for Markdown and file access, HTML exporters, and a small application layer that composes them through dependency injection.</p>

  <p>Planning data is kept in ordinary Markdown files, organized by category and discovered recursively from an input directory. A task starts with <code>-</code> for an open item or <code>x</code> for a completed item. Optional metadata describes the expected effort, eligible or mandatory days, and dependencies. For example:</p>

  <pre><code>## Todo
- [Mon,Wed,Fri] Read for 30 minutes (30m)
- [|Sat] Clean the kitchen (1)
- Prepare the report (d)
  - Draft the introduction (45m)</code></pre>

  <p>The format also supports nested tasks, recurring weekday or ordinal-day rules, no-estimate tasks using <code>(-)</code>, and annual birthday reminders such as <code>[Aug 18]</code>. The parser validates this metadata and reports source-aware errors before scheduling begins.</p>

  <h2>A plan for the week</h2>

  <p>The scheduler converts the parsed tasks into a calendar aligned to the Monday of the requested week. It respects dependencies, mandatory days, recurring work, task priority, and daily capacity while tracking work that could not be scheduled. Birthday reminders are added as zero-hour entries, and completed tasks are preserved in the Markdown workflow rather than scheduled as new work.</p>

  <p>The final stage renders the plan as lightweight, print-friendly HTML. The standard export produces <code>current.html</code> for the requested week, <code>following.html</code> for the next week, and <code>month.html</code> for the requested month. These pages present pending tasks and day-by-day work with checkboxes, durations, scheduling markers, and birthday information, so the generated calendar can be printed or opened directly in a browser without a separate planning service.</p>

  <p><a class="card-link" href="{{ '/projects/' | relative_url }}">Back to projects</a></p>
</div>
