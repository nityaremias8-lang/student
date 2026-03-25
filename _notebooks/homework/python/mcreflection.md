---
layout: post
title: "Relflection"
description: "Breakfast time hits, and in NYC that means one thing: pick your spot and dive in."
permalink: student/mcreflection
parent: "Analytics/Admin"
team: "Nitya"
submodule: 1
author: "Insightful Innocators"
date: 2025-11-20
microblog: true

---

<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>50/67 · My CS Reflection</title>
    <!-- Fonts & Icons -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:opsz,wght@14..32,400;14..32,500;14..32,600;14..32,700&family=Fira+Code:wght@400;500&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            background: #f6f8fa;
            font-family: 'Inter', sans-serif;
            line-height: 1.6;
            color: #1e293b;
            padding: 2rem 1rem;
        }

        .blog-container {
            max-width: 820px;
            margin: 0 auto;
            background: white;
            border-radius: 32px;
            box-shadow: 0 20px 40px -12px rgba(0,20,30,0.15);
            overflow: hidden;
            border: 1px solid #e9edf2;
        }

        .hero {
            background: linear-gradient(135deg, #0b1e33 0%, #1a3650 100%);
            padding: 3rem 2.5rem 2.5rem 2.5rem;
            color: white;
        }

        .hero h1 {
            font-size: 2.6rem;
            font-weight: 700;
            letter-spacing: -0.02em;
            line-height: 1.2;
            margin-bottom: 0.6rem;
        }

        .hero .score-badge {
            display: inline-block;
            background: rgba(255,215,0,0.15);
            backdrop-filter: blur(4px);
            border: 1px solid rgba(255,215,0,0.3);
            padding: 0.5rem 1.2rem;
            border-radius: 60px;
            font-weight: 600;
            font-size: 1.2rem;
            margin: 1rem 0 1.2rem 0;
            color: #ffea9e;
        }

        .hero .meta {
            display: flex;
            gap: 2rem;
            font-size: 0.95rem;
            color: #b6cdff;
            border-top: 1px solid #2f4b6e;
            padding-top: 1.5rem;
            margin-top: 1rem;
        }

        .content {
            padding: 2.5rem;
        }

        .intro p {
            font-size: 1.2rem;
            font-weight: 400;
            color: #2c3e50;
            margin-bottom: 2.2rem;
            background: #f0f4fa;
            padding: 1.5rem 2rem;
            border-radius: 24px;
            border-left: 6px solid #3b82f6;
        }

        h2 {
            font-size: 1.9rem;
            font-weight: 600;
            letter-spacing: -0.01em;
            margin: 2.2rem 0 1rem 0;
            display: flex;
            align-items: center;
            gap: 10px;
        }

        h2 i {
            color: #3b82f6;
            font-size: 2rem;
        }

        h3 {
            font-size: 1.4rem;
            font-weight: 600;
            margin: 1.8rem 0 0.8rem 0;
            color: #0f2b45;
        }

        .question-card {
            background: #f9fcff;
            border-radius: 28px;
            padding: 1.8rem;
            margin: 2rem 0;
            border: 1px solid #dde7f0;
            box-shadow: 0 6px 14px rgba(0,0,0,0.02);
        }

        .q-num {
            font-family: 'Fira Code', monospace;
            font-weight: 600;
            background: #1e2f4a;
            color: white;
            display: inline-block;
            padding: 0.2rem 1rem;
            border-radius: 40px;
            font-size: 0.9rem;
            letter-spacing: 0.3px;
            margin-bottom: 1rem;
        }

        .q-num i {
            margin-right: 6px;
            font-size: 0.8rem;
        }

        .my-answer {
            background: #fee2e2;
            color: #991b1b;
            padding: 0.8rem 1.2rem;
            border-radius: 18px;
            font-weight: 500;
            display: inline-flex;
            align-items: center;
            gap: 8px;
            margin: 0.8rem 0;
        }

        .correct-answer {
            background: #dcfce7;
            color: #14532d;
            padding: 0.8rem 1.2rem;
            border-radius: 18px;
            font-weight: 500;
            display: inline-flex;
            align-items: center;
            gap: 8px;
            margin: 0.3rem 0 1.2rem 0;
        }

        .takeaway {
            background: #e9f2ff;
            border-radius: 20px;
            padding: 1.2rem 1.6rem;
            margin: 1.5rem 0 0.5rem 0;
            border-left: 6px solid #2563eb;
        }

        .takeaway i {
            color: #2563eb;
            margin-right: 8px;
        }

        .code-block {
            background: #0d1f2e;
            color: #d4e6ff;
            padding: 1.2rem 1.5rem;
            border-radius: 18px;
            font-family: 'Fira Code', monospace;
            font-size: 0.9rem;
            overflow-x: auto;
            white-space: pre-wrap;
            word-break: break-word;
            margin: 1.2rem 0;
            border: 1px solid #264a6b;
        }

        .bullet-list {
            list-style: none;
            padding: 0;
        }

        .bullet-list li {
            margin-bottom: 0.8rem;
            display: flex;
            gap: 12px;
            align-items: flex-start;
        }

        .bullet-list li i {
            color: #2563eb;
            margin-top: 4px;
            font-size: 1.1rem;
            min-width: 22px;
        }

        hr {
            border: none;
            border-top: 2px dashed #cddae9;
            margin: 2.8rem 0;
        }

        .closing-note {
            background: #0f202f;
            color: white;
            padding: 2rem 2.5rem;
            border-radius: 28px;
            margin-top: 2.8rem;
            background-image: radial-gradient(circle at 80% 30%, #2b4b6e 0%, #0a1b2c 100%);
        }

        .closing-note p {
            font-size: 1.2rem;
            font-weight: 400;
            opacity: 0.95;
        }

        .footer {
            text-align: center;
            padding: 1.8rem;
            color: #5f7d9c;
            font-size: 0.9rem;
            border-top: 1px solid #e2eaf2;
        }

        @media (max-width: 600px) {
            .hero h1 { font-size: 2rem; }
            .hero { padding: 2rem 1.5rem; }
            .content { padding: 1.8rem; }
        }
    </style>
</head>
<body>
<div class="blog-container">
    <div class="hero">
        <h1>50/67 · My College Board <br>MCQ Reflection</h1>
        <div class="score-badge">
            <i class="fas fa-code" style="margin-right: 8px;"></i> 17 lessons from 17 mistakes
        </div>
        <div class="meta">
            <span><i class="far fa-calendar-alt" style="margin-right: 6px;"></i> March 2, 2026</span>
            <span><i class="far fa-clock"></i> 6 min read</span>
            <span><i class="fas fa-robot"></i> CS precision</span>
        </div>
    </div>

    <div class="content">
        <div class="intro">
            <p>📌 I got my practice MCQ results back: <strong>50 out of 67</strong>. Not terrible, but far from perfect. 
            As I scrolled through the red X’s, a pattern emerged — one that every computer science student eventually faces. 
            Here’s exactly what I learned from each mistake.</p>
        </div>

        <!-- Q6 -->
        <h2><i class="fas fa-robot"></i> Q6 – The robot that fooled me</h2>
        <div class="question-card">
            <div class="q-num"><i class="fas fa-question-circle"></i> QUESTION 6 · ROBOT GRID</div>
            <p><strong>Program I</strong> repeats a fixed sequence twice. <strong>Program II</strong> uses <code>REPEAT UNTIL GoalReached</code> with conditionals. Which works?</p>
            <div class="my-answer"><i class="fas fa-times-circle"></i> My answer: C (both work)</div>
            <div class="correct-answer"><i class="fas fa-check-circle"></i> Correct: B (only Program II works)</div>
            <p>I visualized Program I’s path incorrectly — it seemed right in my head, but tracing step by step proves it never reaches the gray square. Program II’s flexible <code>REPEAT UNTIL</code> with <code>CAN_MOVE</code> handles any path.</p>
            <div class="takeaway">
                <i class="fas fa-lightbulb"></i> <strong>Takeaway:</strong> Don’t just read code — trace it, draw it, step through it. Especially with robots.
            </div>
        </div>

        <!-- Q11 -->
        <h2><i class="fas fa-palette"></i> Q11 – Binary color slip</h2>
        <div class="question-card">
            <div class="q-num"><i class="fas fa-question-circle"></i> QUESTION 11 · RGB BINARY</div>
            <p><code>(11111111, 11111111, 11110000)</code> — what color?</p>
            <div class="my-answer"><i class="fas fa-times-circle"></i> My answer: B (Light yellow)</div>
            <div class="correct-answer"><i class="fas fa-check-circle"></i> Correct: A (Ivory)</div>
            <p>Light yellow is <code>11100000</code> = 224. I misread <code>11110000</code> = 240 → Ivory. Rushed binary conversion.</p>
            <div class="takeaway">
                <i class="fas fa-lightbulb"></i> <strong>Takeaway:</strong> Convert carefully. Double-check each channel. Slow is smooth, smooth is fast.
            </div>
        </div>

        <!-- Q16 -->
        <h2><i class="fas fa-infinity"></i> Q16 – The loop that never dies</h2>
        <div class="question-card">
            <div class="q-num"><i class="fas fa-question-circle"></i> QUESTION 16 · INFINITE LOOP</div>
            <div class="code-block">
index ← LENGTH(wordList)<br>
REPEAT UNTIL (index < 1)<br>
&nbsp;&nbsp; IF (wordList[index] = "the" OR wordList[index] = "a")<br>
&nbsp;&nbsp;&nbsp;&nbsp; REMOVE(wordList, index)<br>
&nbsp;&nbsp; END IF<br>
END REPEAT
            </div>
            <p>Where to insert <code>index ← index – 1</code>?</p>
            <div class="my-answer"><i class="fas fa-times-circle"></i> My answer: C (between lines 6–7)</div>
            <div class="correct-answer"><i class="fas fa-check-circle"></i> Correct: D (between lines 7–8)</div>
            <p>Inserting after the IF block ensures decrement EVERY iteration — not just when a match is found.</p>
            <div class="takeaway">
                <i class="fas fa-lightbulb"></i> <strong>Takeaway:</strong> Loop variables must update in ALL branches. Otherwise → infinite loop.
            </div>
        </div>

        <!-- Q45 -->
        <h2><i class="fas fa-coins"></i> Q45 – Coin flip probability</h2>
        <div class="question-card">
            <div class="q-num"><i class="fas fa-question-circle"></i> QUESTION 45 · COIN SIMULATION</div>
            <p>Fair coin flipped three times; win if all same (HHH or TTT).</p>
            <div class="my-answer"><i class="fas fa-times-circle"></i> My answer: B (random 0–3, win on 0 or 3)</div>
            <div class="correct-answer"><i class="fas fa-check-circle"></i> Correct: D (sum three random 0/1, win if sum=0 or 3)</div>
            <p>B gives 2/4 = 50% win rate. Actual probability = 2/8 = 25%. D matches the distribution.</p>
            <div class="takeaway">
                <i class="fas fa-lightbulb"></i> <strong>Takeaway:</strong> Random ranges must reflect true probability, not just "feeling".
            </div>
        </div>

        <!-- Q51 Creative Commons -->
        <h2><i class="fas fa-copyright"></i> Q51 – Creative Commons mix-up</h2>
        <div class="question-card">
            <div class="q-num"><i class="fas fa-question-circle"></i> QUESTION 51 · CC LICENSES</div>
            <div class="my-answer"><i class="fas fa-times-circle"></i> My answer: B (CC lets you use any copyrighted work)</div>
            <div class="correct-answer"><i class="fas fa-check-circle"></i> Correct: A (creators indicate how works can be used)</div>
            <p>CC doesn’t override existing copyright — it only applies to works published with a CC license.</p>
            <div class="takeaway">
                <i class="fas fa-lightbulb"></i> <strong>Takeaway:</strong> Read the wording: “enables broad access” ≠ “any work is free”.
            </div>
        </div>

        <!-- Q56 execution time -->
        <h2><i class="fas fa-hourglass-half"></i> Q56 – Execution time trap</h2>
        <div class="question-card">
            <div class="q-num"><i class="fas fa-question-circle"></i> QUESTION 56 · PREDICTION CALLS</div>
            <p>Version I: one <code>GetPrediction</code> per id. Version II: two per id + one extra.</p>
            <div class="my-answer"><i class="fas fa-times-circle"></i> My answer: C (II takes ≈1 min more)</div>
            <div class="correct-answer"><i class="fas fa-check-circle"></i> Correct: D (II takes ≈5 min more)</div>
            <p>II calls: 4 ids → 8 calls + 1 final = 9 calls vs I’s 4 calls → 5 extra minutes.</p>
            <div class="takeaway">
                <i class="fas fa-lightbulb"></i> <strong>Takeaway:</strong> Count operations exactly. “Approximately” can hide big differences.
            </div>
        </div>

        <!-- Q58 AnyPairs -->
        <h2><i class="fas fa-code-branch"></i> Q58 – Boolean logic bug</h2>
        <div class="question-card">
            <div class="q-num"><i class="fas fa-question-circle"></i> QUESTION 58 · ANYPAIRS</div>
            <div class="code-block">
PROCEDURE AnyPairs(x, y, z)<br>
&nbsp;&nbsp; IF (x = y) { RETURN true }<br>
&nbsp;&nbsp; ELSE { RETURN (y = z) }<br>
END
            </div>
            <p>Fails when …?</p>
            <div class="my-answer"><i class="fas fa-times-circle"></i> My answer: A ("bat","cat","rat") — actually returns false correctly</div>
            <div class="correct-answer"><i class="fas fa-check-circle"></i> Correct: C ("bat","cat","bat") — returns false but should be true (x=z)</div>
            <p>Procedure only checks x=y or y=z. Misses x=z case when y is different.</p>
            <div class="takeaway">
                <i class="fas fa-lightbulb"></i> <strong>Takeaway:</strong> Test edge cases: all combinations of equality. Don't assume symmetry.
            </div>
        </div>

        <!-- Q59 open source -->
        <h2><i class="fas fa-code"></i> Q59 – Open source myth</h2>
        <div class="question-card">
            <div class="q-num"><i class="fas fa-question-circle"></i> QUESTION 59 · OPEN SOURCE</div>
            <p>Which is NOT an advantage?</p>
            <div class="my-answer"><i class="fas fa-times-circle"></i> My answer: D (can update without original devs) </div>
            <div class="correct-answer"><i class="fas fa-check-circle"></i> Correct: C (original dev provides free support)</div>
            <p>Open source doesn’t guarantee free support — community support, not original dev.</p>
            <div class="takeaway">
                <i class="fas fa-lightbulb"></i> <strong>Takeaway:</strong> Free software ≠ free support. Distinguish product from service.
            </div>
        </div>

        <!-- Q66 perfect numbers -->
        <h2><i class="fas fa-calculator"></i> Q66 – Off-by-one errors</h2>
        <div class="question-card">
            <div class="q-num"><i class="fas fa-question-circle"></i> QUESTION 66 · PERFECT NUMBER COUNTER</div>
            <p>Two lines to remove (select two).</p>
            <div class="my-answer"><i class="fas fa-times-circle"></i> I missed one correct line.</div>
            <div class="correct-answer"><i class="fas fa-check-circle"></i> Remove line 5 (unconditional count++) and line 9 (double increment inside IF).</div>
            <p>Extra increments destroyed the count. Keep only one increment inside IF + one increment outside IF for currentNum.</p>
            <div class="takeaway">
                <i class="fas fa-lightbulb"></i> <strong>Takeaway:</strong> Identify every update to variables — one too many breaks the logic.
            </div>
        </div>

        <!-- NumOccurrences extra question (Q??) but they mentioned two answers -->
        <h2><i class="fas fa-list"></i> NumOccurrences – reset inside loop</h2>
        <div class="question-card">
            <div class="q-num"><i class="fas fa-question-circle"></i> NUMOCCURRENCES BUG</div>
            <div class="code-block">
PROCEDURE NumOccurrences(wordList, targetWord)<br>
&nbsp;&nbsp; count ← 0<br>
&nbsp;&nbsp; FOR EACH word IN wordList<br>
&nbsp;&nbsp;&nbsp;&nbsp; count ← 0            &nbsp;&nbsp;&nbsp;// ← resets every iteration!<br>
&nbsp;&nbsp;&nbsp;&nbsp; IF word = targetWord<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; count ← count + 1<br>
&nbsp;&nbsp;&nbsp;&nbsp; END IF<br>
&nbsp;&nbsp; END FOR<br>
&nbsp;&nbsp; RETURN count<br>
END
            </div>
            <p><strong>When does it fail?</strong> When the target appears more than once (count gets reset). Also if target is the last word? Actually fails for any list where target appears — resets to 0 each time, so final count is 0 or 1. Works only when target appears 0 or 1 times.</p>
            <div class="takeaway">
                <i class="fas fa-lightbulb"></i> <strong>Takeaway:</strong> Initializations belong OUTSIDE loops, unless you really mean to reset.
            </div>
        </div>

        <hr>

        <!-- closing reflection -->
        <div class="closing-note">
            <p style="font-size: 1.5rem; font-weight: 600; margin-bottom: 0.5rem;">✨ 50/67 is not the end</p>
            <p>Every red X taught me something concrete. I used to think "I know this, I just made a careless mistake." But now I see: each mistake points to a subtle hole in my mental model. Tracing, edge cases, probability, binary conversion, loop updates — these are the real skills.</p>
            <p style="margin-top: 1.4rem;">On to the next practice test — slower, more deliberate, and with a notebook full of these lessons.</p>
        </div>

    </div>

    <div class="footer">
        <i class="fas fa-mug-hot"></i> reflected with a cup of coffee · code. learn. repeat.
    </div>
</div>
</body>
</html>