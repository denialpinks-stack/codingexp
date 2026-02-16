<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>personal · survey flow</title>
  <style>
    /* ---- personal style: soft, modern, with organic touches ---- */
    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
    }

    body {
      background: linear-gradient(145deg, #f6f0e7 0%, #e3d9d0 100%);
      font-family: 'Inter', system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      min-height: 100vh;
      margin: 0;
      padding: 2rem 1rem;
    }

    /* main card */
    #title {
      font-size: 2.4rem;
      font-weight: 600;
      letter-spacing: -0.5px;
      color: #2b2a28;
      text-align: center;
      margin-bottom: 0.25rem;
      text-shadow: 2px 2px 0 rgba(255,255,240,0.6);
    }

    #description {
      text-align: center;
      color: #4f4d4a;
      font-size: 1.1rem;
      font-style: italic;
      margin-bottom: 2rem;
      border-bottom: 2px dotted #bfb6ab;
      padding-bottom: 0.75rem;
      max-width: 600px;
      margin-left: auto;
      margin-right: auto;
    }

    #survey-form {
      background: #ffffffd9;
      backdrop-filter: blur(2px);
      max-width: 720px;
      width: 100%;
      padding: 2.2rem 2rem;
      border-radius: 36px 36px 36px 36px;
      box-shadow: 0 20px 40px -15px #7f6e5f, 0 8px 0 0 #cbbeb2 inset, 0 -2px 0 0 #e5dbd2 inset;
      border: 1px solid #f0e4d8;
      transition: all 0.2s;
    }

    /* label styling for name, email, number */
    #survey-form label {
      font-weight: 550;
      color: #3d3a35;
      display: block;
      margin-top: 1.4rem;
      margin-bottom: 0.3rem;
      font-size: 1.1rem;
      letter-spacing: 0.3px;
    }

    /* first three labels get extra love */
    #name-label, #email-label, #number-label {
      border-left: 6px solid #bc9f8b;
      padding-left: 12px;
    }

    /* inputs, select, textarea */
    input[type="text"],
    input[type="email"],
    input[type="number"],
    select,
    textarea {
      width: 100%;
      padding: 0.9rem 1.2rem;
      font-size: 1rem;
      background: #fefcf9;
      border: 2px solid #ddd2c7;
      border-radius: 30px;
      transition: 0.2s;
      outline: none;
      color: #2e2b27;
      font-family: inherit;
      box-shadow: inset 2px 2px 5px #e0d6cd, inset -2px -2px 5px #fffcf8;
    }

    input:focus,
    select:focus,
    textarea:focus {
      border-color: #b28b7a;
      background: #ffffff;
      box-shadow: 0 0 0 5px #edd9cf80, inset 0 1px 4px #fff;
    }

    /* dropdown arrow style */
    select {
      appearance: none;
      background-image: url('data:image/svg+xml;utf8,<svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="%237c6b5c" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><polyline points="6 9 12 15 18 9"/></svg>');
      background-repeat: no-repeat;
      background-position: right 1.2rem center;
      background-size: 1.2rem;
    }

    /* radio & check groups */
    .radio-group, .checkbox-group {
      margin: 0.8rem 0 1.2rem 0;
      background: #f9f3ed;
      padding: 1rem 1.5rem;
      border-radius: 50px 50px 30px 30px;
      border: 1px solid #e2cfc0;
    }

    .radio-group p, .checkbox-group p {
      font-weight: 600;
      color: #5f5047;
      margin-bottom: 0.5rem;
      font-size: 1.1rem;
    }

    .radio-option, .check-option {
      display: inline-block;
      margin-right: 2rem;
      margin-bottom: 0.3rem;
    }

    .radio-option label, .check-option label {
      display: inline-block;
      margin: 0 0 0 0.3rem !important;
      font-weight: 400;
      color: #4b413a;
      vertical-align: middle;
    }

    input[type="radio"], input[type="checkbox"] {
      accent-color: #a7826f;
      width: 1.2rem;
      height: 1.2rem;
      vertical-align: middle;
    }

    /* textarea */
    textarea {
      min-height: 110px;
      resize: vertical;
      border-radius: 30px;
      padding: 1rem;
    }

    /* submit button */
    #submit {
      background: #a27f6b;
      border: none;
      color: white;
      font-weight: 600;
      font-size: 1.5rem;
      letter-spacing: 2px;
      padding: 1.2rem 2rem;
      width: 100%;
      border-radius: 50px;
      margin-top: 2.5rem;
      cursor: pointer;
      box-shadow: 0 8px 0 #6d5647, 0 4px 15px rgba(0,0,0,0.2);
      transition: 0.07s linear;
      text-transform: uppercase;
      border: 1px solid #cfa48b;
    }

    #submit:hover {
      background: #b48d78;
      transform: translateY(-2px);
      box-shadow: 0 10px 0 #6d5647, 0 6px 18px rgba(0,0,0,0.2);
    }

    #submit:active {
      transform: translateY(6px);
      box-shadow: 0 2px 0 #6d5647, 0 6px 15px rgba(0,0,0,0.1);
    }

    /* small spacing for placeholder */
    ::placeholder {
      color: #aa9f95;
      opacity: 0.7;
      font-style: italic;
    }

    /* make dropdown and textarea consistent */
    #dropdown {
      margin-bottom: 0.5rem;
    }

    /* labels for radio/check inside groups are inline, no extra margin */
    .radio-group label, .checkbox-group label {
      display: inline;
      border-left: none;
      padding-left: 0;
      font-weight: normal;
      margin: 0 0 0 0.3rem;
    }

    /* additional label for comments */
    label[for="comments"] {
      margin-top: 2rem;
      border-left: 6px solid #bc9f8b;
      padding-left: 12px;
    }

    /* small touch for field grouping */
    hr {
      border: 1px dashed #dacbbe;
      margin: 1.5rem 0;
    }

    /* responsive fine-tuning */
    @media (max-width: 550px) {
      #title { font-size: 2rem; }
      #survey-form { padding: 1.5rem; }
      .radio-option, .check-option { display: block; margin: 0.3rem 0; }
    }
  </style>
</head>
<body>
  <h1 id="title">✧･ﾟ: * survey vessel *:･ﾟ✧</h1>
  <p id="description">drop your thoughts — we’re all ears (and databases)</p>

  <form id="survey-form">
    <!-- === NAME field === -->
    <label id="name-label">✒️ what should we call you?</label>
    <input id="name" type="text" placeholder="e.g. Sam, Jordan, or your nickname" required>

    <!-- === EMAIL field === -->
    <label id="email-label">📬 digital mailbox</label>
    <input id="email" type="email" placeholder="your_name@example.com" required>

    <!-- === NUMBER field (with range) === -->
    <label id="number-label">🔢 years you've been coding (approx)</label>
    <input id="number" type="number" min="1" max="80" placeholder="between 1 and 80" step="1">

    <!-- === DROPDOWN (select) === -->
    <label for="dropdown">🌱 how did you find this form?</label>
    <select id="dropdown">
      <option value="placeholder">— choose one —</option>
      <option value="social">instagram / twitter</option>
      <option value="friend">a friend whispered it</option>
      <option value="blog">dev blog or newsletter</option>
    </select>

    <!-- === RADIO group (at least two) === -->
    <div class="radio-group">
      <p>⚡ your coding comfort zone:</p>
      <div class="radio-option">
        <input type="radio" id="beginner" name="exp_level" value="beginner">
        <label for="beginner">🌿 beginner (just starting)</label>
      </div>
      <div class="radio-option">
        <input type="radio" id="intermediate" name="exp_level" value="intermediate">
        <label for="intermediate">🌀 intermediate (building stuff)</label>
      </div>
      <div class="radio-option">
        <input type="radio" id="pro" name="exp_level" value="pro">
        <label for="pro">🔥 pro (I dream in code)</label>
      </div>
    </div>

    <!-- === CHECKBOX group (at least two, each with value) === -->
    <div class="checkbox-group">
      <p>☕ favourite tools / languages (check all that apply)</p>
      <div class="check-option">
        <input type="checkbox" id="html5" value="html5">
        <label for="html5">HTML5</label>
      </div>
      <div class="check-option">
        <input type="checkbox" id="css3" value="css3">
        <label for="css3">CSS3</label>
      </div>
      <div class="check-option">
        <input type="checkbox" id="javascript" value="javascript">
        <label for="javascript">JavaScript</label>
      </div>
      <div class="check-option">
        <input type="checkbox" id="python" value="python">
        <label for="python">Python</label>
      </div>
    </div>

    <!-- === TEXTAREA for additional comments === -->
    <label for="comments">📝 spill the tea (extra thoughts, ideas, feedback)</label>
    <textarea id="comments" placeholder="I'd love to hear about your current project, a favorite resource, or anything..."></textarea>

    <!-- === SUBMIT BUTTON === -->
    <button id="submit" type="submit">✔ send it</button>
  </form>

  <!-- small hidden credit for personality (doesn't affect tests) -->
  <div style="margin-top: 1.2rem; font-size: 0.8rem; color: #8f7e71;">✤ built with curiosity ✤</div>
</body>
</html>
