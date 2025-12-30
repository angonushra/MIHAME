<!DOCTYPE html>
<html lang="ha">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>JAMI'AR IHAME - Ilimin Zamani Cikin Hausa</title>
    <link href="https://fonts.googleapis.com/css2?family=Roboto:wght@400;500;700&family=Nunito:wght@400;700&family=Montserrat:wght@400;700&family=Playfair+Display:wght@400;700&family=Open+Sans:wght@400;700&family=Poppins:wght@400;700&display=swap" rel="stylesheet">
    <script src="https://cdn.jsdelivr.net/npm/jspdf@2.5.1/dist/jspdf.umd.min.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/html2canvas@1.4.1/dist/html2canvas.min.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/qrcode@1.5.3/build/qrcode.min.js"></script>
    <style>
        /* CSS styles for the complete platform - PART 1 */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Nunito', sans-serif;
            background-color: #f0f2f5;
            margin: 0;
            padding: 0;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            color: #333;
            transition: background-color 0.3s, color 0.3s, font-size 0.3s;
            line-height: 1.6;
        }

        body.dark-mode {
            background-color: #121212;
            color: #e0e0e0;
        }
        
        body.wallpaper {
            background-size: cover;
            background-position: center;
            background-attachment: fixed;
        }

        .page {
            width: 90%;
            max-width: 500px;
            background-color: #fff;
            padding: 30px;
            border-radius: 10px;
            box-shadow: 0 4px 8px rgba(0,0,0,0.1);
            text-align: center;
            display: none;
            animation: fadeIn 0.5s;
            margin: 20px auto;
            position: relative;
            z-index: 1;
        }
        
        #admin-page .page-content {
            max-width: 800px;
            width: 100%;
        }

        .page.active {
            display: block;
        }
        
        .page.admin-page {
            max-width: 800px;
        }
        
        .page.admin-page .page-content {
            width: 100%;
        }

        body.dark-mode .page {
            background-color: #1e1e1e;
            box-shadow: 0 4px 8px rgba(255,255,255,0.1);
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }

        /* Logo and Header */
        .logo-container {
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            margin-bottom: 20px;
        }
        
        .logo-image {
            width: 150px;
            height: 150px;
            border-radius: 10px;
            object-fit: cover;
            border: 5px solid #006400;
            box-shadow: 0 4px 8px rgba(0,0,0,0.2);
        }
        
        .main-logo {
            font-family: 'Roboto', sans-serif;
            font-size: 2.5em;
            font-weight: bold;
            color: #006400;
            margin-bottom: 10px;
        }

        .ihame-meaning {
            font-size: 0.8em;
            color: #666;
            margin-top: -15px;
            margin-bottom: 20px;
        }

        .social-media {
            margin-top: 10px;
        }
        .social-media a {
            margin: 0 10px;
            font-size: 1.5em;
            color: #006400;
        }

        header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 20px;
        }

        .header-right {
            display: flex;
            align-items: center;
        }

        .header-right p {
            margin-right: 15px;
            font-weight: bold;
        }

        h2 {
            color: #006400;
            margin-bottom: 10px;
        }

        body.dark-mode h2 {
            color: #4CAF50;
        }

        h3 {
            color: #555;
            margin-bottom: 20px;
        }

        body.dark-mode h3 {
            color: #bbb;
        }

        /* Form Inputs and Buttons */
        input, select, button, textarea {
            width: 100%;
            padding: 12px;
            margin-bottom: 15px;
            border: 1px solid #ccc;
            border-radius: 5px;
            box-sizing: border-box;
            font-size: 16px;
        }
        input[type="checkbox"] {
            width: auto;
        }

        input:focus, select:focus, textarea:focus {
            border-color: #006400;
            outline: none;
        }

        button {
            background-color: #006400;
            color: white;
            font-weight: bold;
            border: none;
            cursor: pointer;
            transition: background-color 0.3s;
        }

        button:hover {
            background-color: #004d40;
        }
        
        button.delete-btn {
            background-color: #d9534f;
        }

        button.delete-btn:hover {
            background-color: #c9302c;
        }

        button.disabled {
            background-color: #ccc;
            cursor: not-allowed;
        }

        a {
            color: #006400;
            text-decoration: none;
        }

        a:hover {
            text-decoration: underline;
        }

        .input-group {
            position: relative;
            margin-bottom: 15px;
        }

        .input-group input {
            width: 100%;
            padding-right: 120px;
        }
        .input-group .input-suffix {
            position: absolute;
            top: 50%;
            right: 10px;
            transform: translateY(-50%);
            color: #888;
            pointer-events: none;
            background: #f1f1f1;
            padding: 8px;
            border-radius: 5px;
        }
        
        .lang-select-container {
            margin-bottom: 20px;
            display: flex;
            justify-content: center;
            align-items: center;
        }
        .lang-select-container label {
            margin-right: 10px;
        }

        /* Dashboard Styling */
        .dashboard-content {
            text-align: left;
        }

        .info-card {
            background-color: #e8f5e9;
            border-left: 5px solid #006400;
            padding: 20px;
            border-radius: 5px;
            margin-bottom: 20px;
        }

        body.dark-mode .info-card {
            background-color: #333;
            border-left: 5px solid #4CAF50;
        }

        .progress-bar-container {
            background-color: #ccc;
            border-radius: 5px;
            margin-top: 10px;
            height: 15px;
        }

        .progress-bar {
            height: 100%;
            background-color: #006400;
            border-radius: 5px;
            width: 0;
            transition: width 0.5s ease-in-out;
        }

        .action-buttons button {
            margin-bottom: 10px;
        }

        .back-btn, .profile-btn, .settings-btn, .admin-btn {
            background: none;
            border: none;
            color: #006400;
            font-size: 1.5em;
            cursor: pointer;
            padding: 5px;
        }
        
        .admin-btn {
            display: none;
        }

        body.dark-mode .back-btn, body.dark-mode .profile-btn, body.dark-mode .settings-btn, body.dark-mode .admin-btn {
            color: #4CAF50;
        }

        /* Modules & Courses Lists */
        .course-item, .module-item {
            padding: 15px;
            border-bottom: 1px solid #eee;
            text-align: left;
            cursor: pointer;
            transition: background-color 0.2s;
        }

        .course-item:hover, .module-item:hover {
            background-color: #f1f1f1;
        }

        body.dark-mode .course-item, body.dark-mode .module-item {
            border-bottom: 1px solid #333;
        }
        body.dark-mode .course-item:hover, body.dark-mode .module-item:hover {
            background-color: #222;
        }

        .learning-content {
            text-align: left;
            line-height: 1.6;
        }
        
        .learning-content iframe {
            width: 100%;
            height: 500px;
            border: none;
            border-radius: 8px;
        }

        .navigation-buttons {
            display: flex;
            justify-content: space-between;
            margin-top: 20px;
        }
        .navigation-buttons button {
            width: 48%;
        }

        /* Settings Page */
        .settings-content {
            text-align: left;
        }

        .setting-item {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 20px;
            font-size: 1.1em;
        }

        .setting-item span.emoji {
            margin-right: 10px;
        }
        
        .nested-settings {
            margin-left: 20px;
            margin-top: 10px;
            border-left: 2px solid #eee;
            padding-left: 10px;
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(100px, 1fr));
            gap: 10px;
        }
        
        .nested-settings img {
            width: 100%;
            height: auto;
            border-radius: 5px;
            cursor: pointer;
            transition: transform 0.2s;
        }
        
        .nested-settings img:hover {
            transform: scale(1.05);
        }

        .help-center {
            margin-top: 20px;
        }

        /* Profile Page */
        .profile-content {
            text-align: left;
        }
        .profile-content input, .profile-content p {
            margin-bottom: 10px;
        }

        #signature-image {
            width: 150px;
            height: auto;
            margin-top: 20px;
        }
        .module-item.locked {
            background-color: #ddd;
            color: #888;
            cursor: not-allowed;
        }
        #profile-pic-preview {
            width: 100px;
            height: 100px;
            border-radius: 50%;
            object-fit: cover;
            margin-bottom: 15px;
            border: 2px solid #006400;
        }

        .edit-fields input {
            margin-bottom: 10px;
        }
        
        .quiz-option {
            display: block;
            margin-bottom: 10px;
            padding: 10px;
            border: 1px solid #ccc;
            border-radius: 5px;
            cursor: pointer;
            transition: background-color 0.2s;
        }
        .quiz-option:hover {
            background-color: #f1f1f1;
        }
        .quiz-option.selected {
            background-color: #e8f5e9;
            border-color: #006400;
        }
        .quiz-option.correct {
            background-color: #a5d6a7;
            border-color: #2e7d32;
        }
        .quiz-option.incorrect {
            background-color: #ef9a9a;
            border-color: #c62828;
        }
        .quiz-result {
            margin-top: 20px;
            font-size: 1.2em;
            font-weight: bold;
        }

        #font-style-select {
            font-family: 'Nunito', sans-serif;
        }
        #font-style-select option[value="Nunito, sans-serif"] { font-family: 'Nunito', sans-serif; }
        #font-style-select option[value="Roboto, sans-serif"] { font-family: 'Roboto', sans-serif; }
        #font-style-select option[value="Montserrat, sans-serif"] { font-family: 'Montserrat', sans-serif; }
        #font-style-select option[value="Playfair Display, serif"] { font-family: 'Playfair Display', serif; }
        #font-style-select option[value="Open Sans, sans-serif"] { font-family: 'Open Sans', sans-serif; }
        #font-style-select option[value="Poppins, sans-serif"] { font-family: 'Poppins', sans-serif; }
        
        .brightness-level-input {
            width: 150px;
        }
        
        .points-container {
            display: flex;
            justify-content: space-between;
            margin-top: 10px;
        }
        
        .points-display {
            font-weight: bold;
            color: #006400;
        }
        
        body.dark-mode .points-display {
            color: #4CAF50;
        }
        
        .progress-summary {
            text-align: center;
            margin: 15px 0;
            font-size: 1.1em;
        }
        
        .module-progress {
            display: flex;
            align-items: center;
            justify-content: space-between;
            margin-top: 10px;
        }
        
        .module-progress-bar {
            flex-grow: 1;
            height: 8px;
            background: #ddd;
            border-radius: 4px;
            margin: 0 10px;
            overflow: hidden;
        }
        
        .module-progress-fill {
            height: 100%;
            background: #006400;
            width: 0%;
            transition: width 0.5s;
        }
        
        body.dark-mode .module-progress-fill {
            background: #4CAF50;
        }
        
        .module-progress-text {
            font-size: 0.9em;
            min-width: 60px;
            text-align: right;
        }
        .payment-info {
            background-color: #fff3cd;
            color: #856404;
            padding: 15px;
            border: 1px solid #ffeeba;
            border-radius: 5px;
            margin-top: 15px;
            text-align: left;
        }
        .payment-info a {
            color: #856404;
        }
        .module-title-wrapper {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        .module-checkmark {
            color: #006400;
            font-size: 1.5em;
            font-weight: bold;
        }
        
        .phone-input-container {
            display: flex;
            gap: 10px;
        }
        #country-code {
            width: 30%;
        }
        #reg-phone {
            width: 70%;
        }
        
        .remember-me {
            display: flex;
            align-items: center;
            margin-bottom: 15px;
            justify-content: flex-start;
        }
        .remember-me input {
            width: auto;
            margin-right: 10px;
        }
        
        .admin-table {
            width: 100%;
            border-collapse: collapse;
            margin-top: 20px;
            text-align: left;
        }
        .admin-table th, .admin-table td {
            padding: 10px;
            border: 1px solid #ddd;
        }
        .admin-table th {
            background-color: #f2f2f2;
        }
        body.dark-mode .admin-table th {
            background-color: #333;
        }
        .admin-user-details img {
            width: 100px;
            height: 100px;
            border-radius: 50%;
            object-fit: cover;
            margin-bottom: 15px;
        }
        
        .student-details {
            text-align: left;
            padding-top: 10px;
        }
        
        .admin-stats {
            display: flex;
            justify-content: space-around;
            text-align: center;
            margin-bottom: 20px;
        }
        
        .admin-stat-card {
            background: #e8f5e9;
            padding: 20px;
            border-radius: 8px;
            width: 45%;
        }
        
        .admin-stat-card h3 {
            margin: 0;
            font-size: 1.2em;
        }
        
        .admin-stat-card p {
            margin: 5px 0 0;
            font-size: 2em;
            font-weight: bold;
            color: #006400;
        }
        
        .edit-profile-btn, .save-profile-btn {
            margin-top: 10px;
        }
        
        .profile-edit-fields {
            display: none;
        }
        .profile-display-fields {
            display: block;
        }
        .profile-edit-fields.active {
            display: block;
        }
        .profile-display-fields.active {
            display: none;
        }
        
        .landing-page button {
            margin: 10px 0;
        }
        
        .pending-registrations {
            margin-top: 20px;
            text-align: left;
        }
        
        .pending-user {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 10px;
            border-bottom: 1px solid #eee;
        }
        
        .pending-user-info {
            flex-grow: 1;
        }
        
        .payment-actions {
            display: flex;
            gap: 10px;
        }
        
        .payment-btn {
            padding: 5px 10px;
            font-size: 0.9em;
        }
        
        .reg-number-list {
            margin-top: 20px;
            text-align: left;
        }
        
        .dept-reg-numbers {
            margin-bottom: 20px;
        }
        
        .reg-number-item {
            padding: 5px;
            border-bottom: 1px solid #eee;
        }
        
        .copy-btn {
            background-color: #006400;
            color: white;
            border: none;
            padding: 5px 10px;
            border-radius: 3px;
            cursor: pointer;
            margin-left: 10px;
        }
        
        .whatsapp-btn {
            background-color: #25D366;
            margin-top: 10px;
        }
        
        .whatsapp-btn:hover {
            background-color: #128C7E;
        }
        
        .quiz-management {
            margin-top: 20px;
            text-align: left;
        }
        
        .quiz-form {
            background: #f9f9f9;
            padding: 15px;
            border-radius: 5px;
            margin-bottom: 20px;
        }
        
        .quiz-form input, .quiz-form select {
            margin-bottom: 10px;
        }
        
        .option-input {
            display: flex;
            align-items: center;
            margin-bottom: 10px;
        }
        
        .option-input input {
            flex-grow: 1;
            margin-right: 10px;
        }
        
        .notification-badge {
            background-color: red;
            color: white;
            border-radius: 50%;
            padding: 2px 6px;
            font-size: 0.8em;
            position: absolute;
            top: 0;
            right: 0;
        }
        
        .notification-container {
            position: relative;
        }
        
        .notification-item {
            padding: 10px;
            border-bottom: 1px solid #eee;
            text-align: left;
        }
        
        .notification-time {
            font-size: 0.8em;
            color: #888;
        }
        
        .activity-indicator {
            display: inline-block;
            width: 10px;
            height: 10px;
            border-radius: 50%;
            margin-right: 5px;
        }
        
        .active-now {
            background-color: #4CAF50;
        }
        
        .inactive {
            background-color: #ccc;
        }
        
        /* NEW STYLES FOR THE UPDATED FEATURES */
        
        /* Certificate Page Improvements */
        #certificate-content {
            border: 15px solid #006400;
            padding: 40px;
            margin: 20px auto;
            max-width: 800px;
            background: linear-gradient(135deg, #fff 0%, #f9f9f9 100%);
            box-shadow: 0 10px 30px rgba(0,0,0,0.3);
            position: relative;
            font-family: 'Times New Roman', serif;
        }
        
        .certificate-watermark {
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%) rotate(-45deg);
            font-size: 120px;
            color: rgba(0, 100, 0, 0.1);
            pointer-events: none;
            z-index: 1;
            font-weight: bold;
            white-space: nowrap;
        }
        
        .certificate-logo {
            width: 120px;
            position: absolute;
            top: 20px;
            right: 20px;
            z-index: 2;
        }
        
        .certificate-header {
            text-align: center;
            margin-bottom: 30px;
            padding-bottom: 20px;
            border-bottom: 3px double #006400;
            position: relative;
            z-index: 2;
        }
        
        .certificate-body {
            padding: 30px;
            text-align: center;
            line-height: 2;
            position: relative;
            z-index: 2;
            background: rgba(255,255,255,0.9);
            border-radius: 10px;
        }
        
        .certificate-footer {
            margin-top: 40px;
            display: flex;
            justify-content: space-between;
            position: relative;
            z-index: 2;
        }
        
        .signature-area {
            text-align: center;
            flex: 1;
            margin: 0 20px;
        }
        
        .signature-line {
            border-top: 2px solid #000;
            width: 200px;
            margin: 5px auto;
            padding-top: 5px;
        }
        
        /* Department Chat Styles */
        .chat-container {
            height: 400px;
            border: 1px solid #ddd;
            border-radius: 8px;
            overflow: hidden;
            display: flex;
            flex-direction: column;
            margin-bottom: 20px;
        }
        
        .chat-messages {
            flex: 1;
            padding: 15px;
            overflow-y: auto;
            background-color: #f9f9f9;
        }
        
        .chat-input-container {
            display: flex;
            padding: 10px;
            background-color: #fff;
            border-top: 1px solid #ddd;
        }
        
        .chat-input {
            flex: 1;
            padding: 10px;
            border: 1px solid #ddd;
            border-radius: 20px;
            margin-right: 10px;
        }
        
        .send-chat-btn {
            width: auto;
            padding: 10px 20px;
            border-radius: 20px;
        }
        
        .message {
            margin-bottom: 15px;
            padding: 10px 15px;
            border-radius: 18px;
            max-width: 80%;
            word-wrap: break-word;
        }
        
        .my-message {
            background-color: #DCF8C6;
            margin-left: auto;
            text-align: right;
        }
        
        .their-message {
            background-color: #FFFFFF;
            margin-right: auto;
            border: 1px solid #EEE;
        }
        
        .admin-message {
            border-left: 4px solid #ff9900;
        }
        
        .message-sender {
            font-weight: bold;
            font-size: 0.9em;
            margin-bottom: 5px;
        }
        
        .message-time {
            font-size: 0.7em;
            color: #999;
            margin-top: 5px;
        }
        
        .message-actions {
            display: flex;
            gap: 5px;
            margin-top: 5px;
        }
        
        .message-actions button {
            padding: 3px 8px;
            font-size: 0.7em;
            border: none;
            border-radius: 3px;
            background: #f0f0f0;
            cursor: pointer;
        }
        
        /* Module Selection Page */
        .module-selection-container {
            text-align: left;
            margin-bottom: 20px;
        }
        
        .module-checkbox {
            margin-right: 10px;
        }
        
        .module-select-item {
            padding: 10px;
            border-bottom: 1px solid #eee;
            display: flex;
            align-items: center;
        }
        
        /* Admin Student Photo Size Fix */
        #student-pic-display {
            width: 80px;
            height: 80px;
            border-radius: 50%;
            object-fit: cover;
            margin-bottom: 15px;
        }
        
        /* WhatsApp Registration Button */
        .whatsapp-reg-btn {
            background-color: #25D366;
            margin-top: 10px;
        }
        
        .whatsapp-reg-btn:hover {
            background-color: #128C7E;
        }

        /* Menu Styles */
        .menu-btn {
            background: none;
            border: none;
            color: #006400;
            font-size: 1.5em;
            cursor: pointer;
            padding: 5px;
            display: none;
        }

        body.dark-mode .menu-btn {
            color: #4CAF50;
        }

        .sidebar-menu {
            position: fixed;
            top: 0;
            left: -250px;
            width: 250px;
            height: 100%;
            background-color: #006400;
            color: white;
            transition: left 0.3s;
            padding: 20px;
            overflow-y: auto;
            z-index: 1000;
        }

        .sidebar-menu.active {
            left: 0;
        }

        .menu-item {
            padding: 15px 0;
            border-bottom: 1px solid rgba(255,255,255,0.1);
            cursor: pointer;
            display: flex;
            align-items: center;
        }

        .menu-item:hover {
            background-color: rgba(255,255,255,0.1);
        }

        .menu-item span {
            margin-right: 10px;
        }

        .close-menu {
            position: absolute;
            top: 10px;
            right: 10px;
            background: none;
            border: none;
            color: white;
            font-size: 1.5em;
            cursor: pointer;
        }

        /* Exam Percentage */
        .exam-progress {
            background-color: #e8f5e9;
            border-left: 5px solid #006400;
            padding: 20px;
            border-radius: 5px;
            margin-bottom: 20px;
        }

        body.dark-mode .exam-progress {
            background-color: #333;
            border-left: 5px solid #4CAF50;
        }

        .exam-progress-bar-container {
            background-color: #ccc;
            border-radius: 5px;
            margin-top: 10px;
            height: 15px;
        }

        .exam-progress-bar {
            height: 100%;
            background-color: #006400;
            border-radius: 5px;
            width: 0;
            transition: width 0.5s ease-in-out;
        }

        .exam-percentage-display {
            font-weight: bold;
            color: #006400;
        }

        body.dark-mode .exam-percentage-display {
            color: #4CAF50;
        }

        /* Calculator Styles */
        #calculator-modal {
            display: none;
            position: fixed;
            z-index: 1000;
            left: 0;
            top: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0,0,0,0.5);
            justify-content: center;
            align-items: center;
        }

        .calculator-container {
            background: white;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 0 20px rgba(0,0,0,0.2);
            width: 300px;
            text-align: center;
        }

        .calculator-display {
            width: 100%;
            height: 50px;
            margin-bottom: 10px;
            font-size: 24px;
            text-align: right;
            padding: 10px;
            box-sizing: border-box;
            border: 1px solid #ccc;
            border-radius: 5px;
        }

        .calculator-buttons {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 10px;
        }

        .calculator-btn {
            padding: 15px;
            font-size: 18px;
            background-color: #006400;
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
        }

        .calculator-btn:hover {
            background-color: #004d40;
        }

        .calculator-btn.operator {
            background-color: #4CAF50;
        }

        .calculator-btn.clear {
            background-color: #f44336;
        }

        .calculator-btn.equal {
            grid-column: span 2;
            background-color: #2196F3;
        }

        .calculator-btn.scientific {
            background-color: #4CAF50;
        }

        .calculator-btn.scientific:hover {
            background-color: #45a049;
        }

        .close-calculator {
            position: absolute;
            top: 10px;
            right: 10px;
            font-size: 24px;
            cursor: pointer;
        }

        /* Research Menu Item */
        .research-menu {
            position: fixed;
            bottom: 20px;
            left: 50%;
            transform: translateX(-50%);
            background: #006400;
            color: white;
            padding: 10px 20px;
            border-radius: 25px;
            cursor: pointer;
            z-index: 1000;
            box-shadow: 0 4px 8px rgba(0,0,0,0.3);
        }

        /* AI Teaching Styles */
        .ai-teaching-content {
            background: white;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 4px 8px rgba(0,0,0,0.1);
        }

        .ai-explanation {
            line-height: 1.8;
            margin-bottom: 20px;
        }

        .interactive-quiz {
            background: #f9f9f9;
            padding: 15px;
            border-radius: 8px;
            border-left: 4px solid #006400;
        }

        /* Vocabulary Styles */
        .vocabulary-search {
            margin-bottom: 20px;
        }

        .vocabulary-letter-section {
            margin-bottom: 30px;
        }

        .vocabulary-letter {
            background: #006400;
            color: white;
            padding: 10px 15px;
            border-radius: 5px;
            margin-bottom: 15px;
            font-size: 1.5em;
        }

        .vocabulary-item {
            background: #f9f9f9;
            padding: 15px;
            margin-bottom: 10px;
            border-radius: 5px;
            border-left: 4px solid #006400;
        }

        .vocabulary-word {
            font-weight: bold;
            font-size: 1.2em;
            color: #006400;
            margin-bottom: 8px;
        }

        .vocabulary-meaning, .vocabulary-example, .vocabulary-explanation {
            margin-bottom: 5px;
            line-height: 1.4;
        }

        /* Library Styles */
        .library-item {
            padding: 15px;
            border-bottom: 1px solid #eee;
            text-align: left;
            display: flex;
            align-items: center;
        }

        .library-icon {
            font-size: 2em;
            margin-right: 15px;
            width: 50px;
            text-align: center;
            color: #006400;
        }

        .library-info {
            flex: 1;
        }

        .library-title {
            font-weight: bold;
            margin-bottom: 5px;
        }

        .library-description {
            font-size: 0.9em;
            color: #666;
            margin-bottom: 5px;
        }

        .library-meta {
            display: flex;
            gap: 15px;
            margin: 8px 0;
            font-size: 0.9em;
            color: #666;
        }

        .library-actions {
            display: flex;
            gap: 10px;
            margin-top: 10px;
        }

        .library-download, .library-preview {
            padding: 5px 12px;
            border: none;
            border-radius: 4px;
            cursor: pointer;
            font-size: 0.9em;
        }

        .library-download {
            background: #006400;
            color: white;
        }

        .library-preview {
            background: #f0f0f0;
            color: #333;
        }

        /* Collapsible Menu Styles */
        .collapsible-menu {
            margin-bottom: 10px;
        }

        .collapsible-header {
            padding: 15px 0;
            border-bottom: 1px solid rgba(255,255,255,0.1);
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: space-between;
        }

        .collapsible-content {
            max-height: 0;
            overflow: hidden;
            transition: max-height 0.3s ease;
            margin-left: 20px;
        }

        .collapsible-content.active {
            max-height: 500px;
        }

        /* Rules and Regulations Styles */
        .rules-content {
            text-align: left;
            line-height: 1.6;
        }

        .rules-list {
            margin-bottom: 20px;
        }

        .rules-list li {
            margin-bottom: 10px;
        }

        /* Alert/Sako Page Styles */
        .alert-tabs {
            display: flex;
            margin-bottom: 20px;
            border-bottom: 1px solid #eee;
        }

        .alert-tab {
            padding: 10px 20px;
            cursor: pointer;
            border-bottom: 2px solid transparent;
        }

        .alert-tab.active {
            border-bottom: 2px solid #006400;
            color: #006400;
            font-weight: bold;
        }

        .alert-content {
            display: none;
        }

        .alert-content.active {
            display: block;
        }

        /* Contact Page Styles */
        .contact-options {
            display: flex;
            flex-direction: column;
            gap: 15px;
        }

        .contact-option {
            padding: 15px;
            border: 1px solid #eee;
            border-radius: 8px;
            text-align: left;
            cursor: pointer;
            transition: background-color 0.2s;
        }

        .contact-option:hover {
            background-color: #f9f9f9;
        }

        .contact-option h3 {
            margin: 0 0 10px 0;
            color: #006400;
        }

        /* Search Styles */
        .search-results {
            margin-top: 20px;
            text-align: left;
        }

        .search-result-item {
            padding: 15px;
            border-bottom: 1px solid #eee;
            cursor: pointer;
        }

        .search-result-item:hover {
            background-color: #f1f1f1;
        }

        /* Admin Exam Controls */
        .exam-controls {
            margin-bottom: 20px;
        }

        .exam-status {
            padding: 10px;
            border-radius: 5px;
            margin-bottom: 10px;
            font-weight: bold;
        }

        .exam-status.active {
            background-color: #e8f5e9;
            color: #006400;
        }

        .exam-status.inactive {
            background-color: #ffebee;
            color: #f44336;
        }

        /* Overlay for menu */
        .menu-overlay {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0,0,0,0.5);
            z-index: 999;
            display: none;
        }

        .menu-overlay.active {
            display: block;
        }

        /* Admin Role Specific Styles */
        .admin-role-tabs {
            display: flex;
            flex-wrap: wrap;
            gap: 10px;
            margin-bottom: 20px;
        }

        .admin-role-tab {
            padding: 10px 15px;
            background: #f0f0f0;
            border-radius: 5px;
            cursor: pointer;
            border: 1px solid #ddd;
        }

        .admin-role-tab.active {
            background: #006400;
            color: white;
            border-color: #006400;
        }

        .admin-panel-section {
            display: none;
        }

        .admin-panel-section.active {
            display: block;
        }

        /* Improved Settings Display */
        .settings-display-container {
            background: white;
            border-radius: 8px;
            padding: 20px;
            margin-bottom: 20px;
            box-shadow: 0 2px 4px rgba(0,0,0,0.1);
        }

        .settings-display-container.dark-mode {
            background: #333;
            color: white;
        }

        /* Course Display Improvements */
        .course-display-container {
            background: white;
            border-radius: 8px;
            padding: 20px;
            margin-bottom: 20px;
            box-shadow: 0 2px 4px rgba(0,0,0,0.1);
        }

        .course-date-selector {
            margin-bottom: 20px;
        }

        .course-list {
            display: none;
        }

        .course-list.active {
            display: block;
        }

        /* Report Display Improvements */
        .report-container {
            background: white;
            border-radius: 8px;
            padding: 20px;
            margin-bottom: 20px;
            box-shadow: 0 2px 4px rgba(0,0,0,0.1);
        }

        .report-stats {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 15px;
            margin-bottom: 20px;
        }

        .report-stat-card {
            background: #e8f5e9;
            padding: 15px;
            border-radius: 8px;
            text-align: center;
        }

        .report-stat-card h3 {
            margin: 0 0 10px 0;
            color: #006400;
        }

        .report-stat-card p {
            font-size: 1.5em;
            font-weight: bold;
            margin: 0;
        }

        /* Payment Verification Styles */
        .payment-verification-container {
            background: white;
            border-radius: 8px;
            padding: 20px;
            margin-bottom: 20px;
            box-shadow: 0 2px 4px rgba(0,0,0,0.1);
        }

        .payment-details {
            background: #f9f9f9;
            padding: 15px;
            border-radius: 5px;
            margin-bottom: 15px;
        }

        .qr-code-display {
            text-align: center;
            margin: 20px 0;
        }

        /* AI Chat Styles */
        .ai-chat-container {
            height: 400px;
            border: 1px solid #ddd;
            border-radius: 8px;
            overflow: hidden;
            display: flex;
            flex-direction: column;
            margin-bottom: 20px;
        }

        .ai-chat-messages {
            flex: 1;
            padding: 15px;
            overflow-y: auto;
            background-color: #f9f9f9;
        }

        .ai-chat-input-container {
            display: flex;
            padding: 10px;
            background-color: #fff;
            border-top: 1px solid #ddd;
        }

        .ai-chat-input {
            flex: 1;
            padding: 10px;
            border: 1px solid #ddd;
            border-radius: 20px;
            margin-right: 10px;
        }

        .send-ai-chat-btn {
            width: auto;
            padding: 10px 20px;
            border-radius: 20px;
        }

        .ai-message {
            margin-bottom: 15px;
            padding: 10px 15px;
            border-radius: 18px;
            max-width: 80%;
            word-wrap: break-word;
        }

        .user-message {
            background-color: #DCF8C6;
            margin-left: auto;
            text-align: right;
        }

        .ai-response {
            background-color: #FFFFFF;
            margin-right: auto;
            border: 1px solid #EEE;
        }

        /* Search Bar Styles */
        .search-bar {
            position: relative;
            margin-bottom: 20px;
        }

        .search-input {
            width: 100%;
            padding: 12px 40px 12px 15px;
            border: 1px solid #ddd;
            border-radius: 25px;
            font-size: 16px;
        }

        .search-icon {
            position: absolute;
            right: 15px;
            top: 50%;
            transform: translateY(-50%);
            color: #666;
        }

        /* Forgot Password Styles */
        .forgot-password-container {
            text-align: left;
        }

        .forgot-password-form {
            margin-bottom: 20px;
        }

        .reset-success {
            background: #e8f5e9;
            padding: 15px;
            border-radius: 8px;
            margin-top: 20px;
            border-left: 5px solid #4CAF50;
        }

        /* Admin History Styles */
        .history-container {
            background: white;
            border-radius: 8px;
            padding: 20px;
            margin-bottom: 20px;
            box-shadow: 0 2px 4px rgba(0,0,0,0.1);
        }

        .history-item {
            padding: 15px;
            border-bottom: 1px solid #eee;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .history-details {
            flex: 1;
        }

        .history-actions {
            display: flex;
            gap: 10px;
        }
        
        /* Admin Reference and QR Code System */
        .admin-reference-system {
            background: white;
            border-radius: 8px;
            padding: 20px;
            margin-bottom: 20px;
            box-shadow: 0 2px 4px rgba(0,0,0,0.1);
        }
        
        .reference-form {
            margin-bottom: 20px;
        }
        
        .reference-result {
            margin-top: 20px;
            padding: 15px;
            border-radius: 8px;
            background-color: #e8f5e9;
            border-left: 5px solid #006400;
        }
        
        .qr-code-preview {
            text-align: center;
            margin: 20px 0;
        }
        
        .qr-code-preview img {
            max-width: 200px;
            border: 1px solid #ddd;
            border-radius: 8px;
            padding: 10px;
            background: white;
        }
        
        /* Public Reading System */
        .public-reading-container {
            background: white;
            border-radius: 8px;
            padding: 20px;
            margin-bottom: 20px;
            box-shadow: 0 2px 4px rgba(0,0,0,0.1);
        }
        
        .reading-content {
            line-height: 1.8;
            margin-bottom: 20px;
        }
        
        .reading-navigation {
            display: flex;
            justify-content: space-between;
            margin-top: 20px;
        }
        
        .reading-controls {
            display: flex;
            gap: 10px;
            margin-bottom: 20px;
        }
        
        .reading-controls button {
            width: auto;
            padding: 10px 15px;
        }
        
        /* Font Settings Page */
        .font-settings-container {
            background: white;
            border-radius: 8px;
            padding: 20px;
            margin-bottom: 20px;
            box-shadow: 0 2px 4px rgba(0,0,0,0.1);
        }
        
        .font-preview {
            padding: 20px;
            border: 1px solid #ddd;
            border-radius: 8px;
            margin-top: 20px;
            min-height: 100px;
        }
        
        /* Dark Mode Settings Page */
        .dark-mode-settings-container {
            background: white;
            border-radius: 8px;
            padding: 20px;
            margin-bottom: 20px;
            box-shadow: 0 2px 4px rgba(0,0,0,0.1);
        }
        
        .dark-mode-preview {
            padding: 20px;
            border: 1px solid #ddd;
            border-radius: 8px;
            margin-top: 20px;
            min-height: 100px;
        }
        
        /* Certificate Public View */
        .certificate-public-container {
            background: white;
            border-radius: 8px;
            padding: 20px;
            margin-bottom: 20px;
            box-shadow: 0 2px 4px rgba(0,0,0,0.1);
        }
        
        .certificate-search {
            margin-bottom: 20px;
        }
        
        .certificate-search input {
            margin-bottom: 10px;
        }
        
        /* Calendar Styles */
        .calendar-container {
            background: white;
            border-radius: 8px;
            padding: 20px;
            margin-bottom: 20px;
            box-shadow: 0 2px 4px rgba(0,0,0,0.1);
        }
        
        .calendar-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 15px;
        }
        
        .calendar-grid {
            display: grid;
            grid-template-columns: repeat(7, 1fr);
            gap: 5px;
        }
        
        .calendar-day {
            padding: 10px;
            text-align: center;
            border-radius: 5px;
            cursor: pointer;
        }
        
        .calendar-day.current {
            background: #e8f5e9;
            color: #006400;
            font-weight: bold;
        }
        
        .calendar-day.study-day {
            background: #006400;
            color: white;
        }
        
        .calendar-day.past {
            opacity: 0.5;
        }
        
        .calendar-day.future {
            background: #f0f0f0;
        }
        
        /* AI Teacher Styles */
        .ai-teacher-container {
            background: white;
            border-radius: 8px;
            padding: 20px;
            margin-bottom: 20px;
            box-shadow: 0 2px 4px rgba(0,0,0,0.1);
        }
        
        .ai-teacher-response {
            background: #f9f9f9;
            padding: 15px;
            border-radius: 8px;
            margin-bottom: 15px;
            border-left: 4px solid #006400;
        }
        
        .ai-teacher-actions {
            display: flex;
            gap: 10px;
            margin-top: 15px;
        }
        
        .ai-teacher-actions button {
            width: auto;
            padding: 8px 15px;
        }
        
        /* Notepad Styles */
        .notepad-container {
            background: white;
            border-radius: 8px;
            padding: 20px;
            margin-bottom: 20px;
            box-shadow: 0 2px 4px rgba(0,0,0,0.1);
        }
        
        .notepad-content {
            min-height: 200px;
            border: 1px solid #ddd;
            border-radius: 5px;
            padding: 15px;
            margin-bottom: 15px;
            font-family: 'Nunito', sans-serif;
        }
        
        .notepad-actions {
            display: flex;
            gap: 10px;
        }
        
        .notepad-actions button {
            width: auto;
            padding: 8px 15px;
        }
        
        /* Enhanced Dashboard Styles */
        .dashboard-stats {
            display: flex;
            justify-content: space-between;
            margin-bottom: 20px;
        }
        
        .dashboard-stat {
            background: #e8f5e9;
            padding: 15px;
            border-radius: 8px;
            text-align: center;
            flex: 1;
            margin: 0 5px;
        }
        
        .dashboard-stat-icon {
            font-size: 2em;
            margin-bottom: 10px;
        }
        
        .dashboard-stat-value {
            font-size: 1.5em;
            font-weight: bold;
            color: #006400;
        }
        
        .dashboard-stat-label {
            font-size: 0.9em;
            color: #666;
        }
        
        /* Enhanced Certificate Styles */
        .certificate-content-improved {
            border: 15px solid #006400;
            padding: 30px;
            margin: 20px auto;
            max-width: 600px;
            background: linear-gradient(135deg, #fff 0%, #f9f9f9 100%);
            box-shadow: 0 10px 30px rgba(0,0,0,0.3);
            position: relative;
            font-family: 'Times New Roman', serif;
            aspect-ratio: 1.414 / 1;
        }
        
        /* Enhanced Chat Styles */
        .chat-media-upload {
            display: flex;
            gap: 10px;
            margin-bottom: 10px;
        }
        
        .chat-media-upload button {
            width: auto;
            padding: 8px 15px;
        }
        
        .chat-media-preview {
            margin-top: 10px;
        }
        
        .chat-media-preview img, .chat-media-preview video, .chat-media-preview audio {
            max-width: 100%;
            border-radius: 8px;
        }
        
        /* Login Type Selection */
        .login-type-selection {
            display: flex;
            gap: 10px;
            margin-bottom: 20px;
        }
        
        .login-type-btn {
            flex: 1;
            padding: 15px;
            border: 2px solid #006400;
            background: white;
            color: #006400;
            border-radius: 8px;
            cursor: pointer;
            font-weight: bold;
            transition: all 0.3s;
        }
        
        .login-type-btn.active {
            background: #006400;
            color: white;
        }
        
        /* Password Reset Styles */
        .password-reset-container {
            background: white;
            border-radius: 8px;
            padding: 20px;
            margin-bottom: 20px;
            box-shadow: 0 2px 4px rgba(0,0,0,0.1);
        }
        
        .password-reset-form {
            margin-bottom: 20px;
        }
        
        /* Admin Alumni Styles */
        .alumni-container {
            background: white;
            border-radius: 8px;
            padding: 20px;
            margin-bottom: 20px;
            box-shadow: 0 2px 4px rgba(0,0,0,0.1);
        }
        
        .alumni-list {
            margin-top: 20px;
        }
        
        .alumni-item {
            padding: 15px;
            border-bottom: 1px solid #eee;
            display: flex;
            align-items: center;
        }
        
        .alumni-photo {
            width: 60px;
            height: 60px;
            border-radius: 50%;
            object-fit: cover;
            margin-right: 15px;
        }
        
        .alumni-info {
            flex: 1;
        }
        
        .alumni-name {
            font-weight: bold;
            margin-bottom: 5px;
        }
        
        .alumni-details {
            font-size: 0.9em;
            color: #666;
        }
        
        .alumni-certificate {
            background: #006400;
            color: white;
            padding: 5px 10px;
            border-radius: 4px;
            font-size: 0.8em;
        }
        
        /* NEW STYLES FOR THE UPDATED FEATURES */
        
        /* AI Content Display */
        .ai-content-display {
            max-height: 400px;
            overflow-y: auto;
            padding: 15px;
            background: #f9f9f9;
            border-radius: 8px;
            margin-bottom: 15px;
            border-left: 4px solid #006400;
        }
        
        .ai-content-display img {
            max-width: 100%;
            height: auto;
            border-radius: 8px;
            margin: 10px 0;
        }
        
        /* Completed Module Indicator */
        .module-completed {
            background-color: #e8f5e9 !important;
            border-left: 5px solid #4CAF50 !important;
        }
        
        .module-completed .module-checkmark {
            color: #4CAF50;
        }
        
        /* History Tracking */
        .history-tracker {
            background: #f9f9f9;
            padding: 15px;
            border-radius: 8px;
            margin-bottom: 20px;
        }
        
        .history-item {
            padding: 10px;
            border-bottom: 1px solid #eee;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        /* Brightness Colors */
        .brightness-colors {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 10px;
            margin-top: 10px;
        }
        
        .brightness-color {
            width: 40px;
            height: 40px;
            border-radius: 50%;
            cursor: pointer;
            border: 2px solid transparent;
        }
        
        .brightness-color.selected {
            border-color: #006400;
        }
        
        .brightness-color.white { background-color: white; }
        .brightness-color.black { background-color: black; }
        .brightness-color.green { background-color: #006400; }
        .brightness-color.grey { background-color: #808080; }
        .brightness-color.brown { background-color: #8B4513; }
        .brightness-color.pink { background-color: #FFC0CB; }
        .brightness-color.purple { background-color: #800080; }
        .brightness-color.red { background-color: #FF0000; }
        .brightness-color.blue { background-color: #0000FF; }
        .brightness-color.yellow { background-color: #FFFF00; }
        .brightness-color.milk { background-color: #FFFDD0; }
        
        /* Reward Display */
        .reward-display {
            font-size: 3em;
            margin: 10px 0;
        }
        
        /* Device Detection */
        .device-warning {
            background: #fff3cd;
            color: #856404;
            padding: 10px;
            border-radius: 5px;
            margin-bottom: 15px;
            text-align: center;
            border: 1px solid #ffeeba;
        }
        
        /* Admin Registration Display */
        .admin-registrations {
            margin-top: 20px;
        }
        
        .registration-item {
            padding: 15px;
            border: 1px solid #ddd;
            border-radius: 8px;
            margin-bottom: 10px;
            background: #f9f9f9;
        }
        
        /* AI Content Processing */
        .ai-content-processed img {
            max-width: 100%;
            height: auto;
            border-radius: 8px;
            margin: 10px 0;
        }
        
        /* Landing Page Image Row */
        .image-row {
            display: flex;
            justify-content: center;
            align-items: center;
            margin-bottom: 25px;
            padding: 0;
        }

        .circle-image {
            width: 90px;
            height: 90px;
            border-radius: 50%;
            object-fit: cover;
            border: 3px solid #f0f0f0;
            box-shadow: 0 2px 5px rgba(0,0,0,0.1);
            margin: 0 10px;
        }
        
        /* Landing Page Main Image */
        .main-image {
            width: 100%;
            border-radius: 8px;
            margin-bottom: 20px;
        }
        
        /* Payment Tier Selection */
        .payment-tier-selection {
            display: flex;
            gap: 10px;
            margin-bottom: 20px;
        }
        
        .payment-tier-btn {
            flex: 1;
            padding: 15px;
            border: 2px solid #006400;
            background: white;
            color: #006400;
            border-radius: 8px;
            cursor: pointer;
            font-weight: bold;
            transition: all 0.3s;
        }
        
        .payment-tier-btn.active {
            background: #006400;
            color: white;
        }
        
        /* Free Tier Timer */
        .free-tier-timer {
            background: #fff3cd;
            color: #856404;
            padding: 10px;
            border-radius: 5px;
            margin-bottom: 15px;
            text-align: center;
            border: 1px solid #ffeeba;
            font-weight: bold;
        }
        
        /* Tier Limitations */
        .tier-limitations {
            background: #f8f9fa;
            padding: 15px;
            border-radius: 8px;
            margin-bottom: 20px;
            border-left: 4px solid #006400;
        }
        
        .tier-limitations ul {
            margin-left: 20px;
            margin-bottom: 10px;
        }
        
        .tier-limitations li {
            margin-bottom: 5px;
        }
        
        /* Banking Information */
        .banking-info {
            background: #e8f5e9;
            padding: 15px;
            border-radius: 8px;
            margin-bottom: 20px;
            border-left: 4px solid #006400;
        }
        
        .banking-details {
            text-align: left;
            margin-top: 10px;
        }
        
        .banking-details p {
            margin-bottom: 5px;
        }
        
        /* Audio Player */
        .audio-player {
            margin: 10px 0;
            text-align: center;
        }
        
        .audio-player button {
            width: auto;
            padding: 8px 15px;
            margin: 0 5px;
        }
        
        /* National Anthem Player */
        .national-anthem-player {
            position: fixed;
            top: 10px;
            right: 10px;
            z-index: 1000;
        }
        
        .mute-btn {
            background: #006400;
            color: white;
            border: none;
            border-radius: 50%;
            width: 40px;
            height: 40px;
            cursor: pointer;
            font-size: 1.2em;
        }
        
        /* University Mission and Vision */
        .mission-vision-container {
            background: white;
            border-radius: 8px;
            padding: 20px;
            margin-bottom: 20px;
            box-shadow: 0 2px 4px rgba(0,0,0,0.1);
            text-align: left;
        }
        
        .mission-vision-container h3 {
            color: #006400;
            margin-bottom: 15px;
            border-bottom: 2px solid #006400;
            padding-bottom: 5px;
        }
        
        .mission-vision-container p {
            margin-bottom: 15px;
            line-height: 1.6;
        }
        
        /* Scientific Calculator Enhancements */
        .scientific-buttons {
            display: grid;
            grid-template-columns: repeat(5, 1fr);
            gap: 5px;
            margin-top: 10px;
        }
        
        /* Currency Converter Styles */
        .converter-container {
            background: white;
            border-radius: 8px;
            padding: 20px;
            margin-bottom: 20px;
            box-shadow: 0 2px 4px rgba(0,0,0,0.1);
        }
        
        .converter-form {
            display: flex;
            flex-direction: column;
            gap: 10px;
        }
        
        .converter-row {
            display: flex;
            gap: 10px;
        }
        
        .converter-row select,
        .converter-row input {
            flex: 1;
        }
        
        /* Measurement Converter Styles */
        .measurement-converter {
            background: white;
            border-radius: 8px;
            padding: 20px;
            margin-bottom: 20px;
            box-shadow: 0 2px 4px rgba(0,0,0,0.1);
        }
        
        .measurement-type-selector {
            display: flex;
            gap: 10px;
            margin-bottom: 15px;
        }
        
        .measurement-type-btn {
            flex: 1;
            padding: 10px;
            border: 1px solid #006400;
            background: white;
            color: #006400;
            border-radius: 5px;
            cursor: pointer;
        }
        
        .measurement-type-btn.active {
            background: #006400;
            color: white;
        }
        
        /* Improved Landing Page */
        .landing-page-content {
            text-align: center;
        }
        
        .landing-page-buttons {
            display: flex;
            flex-direction: column;
            gap: 10px;
            margin-bottom: 20px;
        }
        
        .landing-page-buttons button {
            margin: 0;
        }
        
        /* Enhanced Admin Student Details */
        .admin-student-details {
            background: white;
            border-radius: 8px;
            padding: 20px;
            margin-bottom: 20px;
            box-shadow: 0 2px 4px rgba(0,0,0,0.1);
        }
        
        .admin-student-actions {
            display: flex;
            gap: 10px;
            margin-top: 15px;
        }
        
        .admin-student-actions button {
            width: auto;
            padding: 8px 15px;
        }
        
        /* Improved Vocabulary Search */
        .vocabulary-search-container {
            position: relative;
            margin-bottom: 20px;
        }
        
        .vocabulary-search-input {
            width: 100%;
            padding: 12px 40px 12px 15px;
            border: 1px solid #ddd;
            border-radius: 25px;
            font-size: 16px;
        }
        
        .vocabulary-search-icon {
            position: absolute;
            right: 15px;
            top: 50%;
            transform: translateY(-50%);
            color: #666;
        }
        
        /* Enhanced Group Chat */
        .group-chat-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 15px;
        }
        
        .group-chat-stats {
            font-size: 0.9em;
            color: #666;
        }

        /* NEW: Improved Navigation Buttons */
        .navigation-buttons-improved {
            display: flex;
            justify-content: space-between;
            margin-top: 20px;
            gap: 10px;
        }
        
        .navigation-buttons-improved button {
            flex: 1;
            padding: 12px;
            font-size: 16px;
        }
        
        /* NEW: Course Progress Indicators */
        .course-progress-indicators {
            display: flex;
            justify-content: space-between;
            margin: 15px 0;
        }
        
        .progress-indicator {
            text-align: center;
            flex: 1;
        }
        
        .progress-indicator .icon {
            font-size: 2em;
            margin-bottom: 5px;
        }
        
        /* NEW: AI Teacher Button Position */
        #ai-teacher-btn {
            order: -1;
            margin-bottom: 10px;
        }
        
        /* NEW: Module Status Styles */
        .module-status {
            display: flex;
            align-items: center;
            gap: 10px;
        }
        
        .module-status.completed {
            color: #4CAF50;
        }
        
        .module-status.locked {
            color: #757575;
        }
        
        .module-status.available {
            color: #006400;
        }
        
        /* NEW: Enhanced Calendar */
        .calendar-day.has-class {
            position: relative;
        }
        
        .calendar-day.has-class::after {
            content: '';
            position: absolute;
            bottom: 2px;
            left: 50%;
            transform: translateX(-50%);
            width: 6px;
            height: 6px;
            background-color: #006400;
            border-radius: 50%;
        }
        
        /* NEW: Improved Certificate */
        .certificate-signatures {
            display: flex;
            justify-content: space-between;
            margin-top: 40px;
        }
        
        .certificate-signature {
            text-align: center;
            flex: 1;
        }
        
        .certificate-signature img {
            max-width: 150px;
            height: auto;
            margin-bottom: 10px;
        }
        
        .signature-line {
            border-top: 1px solid #000;
            width: 80%;
            margin: 5px auto;
        }
        
        /* NEW: Tokens Display */
        .tokens-display {
            background: #e8f5e9;
            padding: 15px;
            border-radius: 8px;
            margin-bottom: 20px;
            border-left: 4px solid #006400;
        }
        
        .tokens-info {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        .tokens-count {
            font-size: 1.5em;
            font-weight: bold;
            color: #006400;
        }
        
        .tokens-warning {
            background: #fff3cd;
            color: #856404;
            padding: 10px;
            border-radius: 5px;
            margin-top: 10px;
            border: 1px solid #ffeeba;
            font-size: 0.9em;
        }
        
        /* NEW: Module Access Control */
        .module-access-control {
            margin-bottom: 15px;
            padding: 10px;
            border-radius: 5px;
            background: #f9f9f9;
        }
        
        .access-status {
            display: flex;
            align-items: center;
            justify-content: space-between;
        }
        
        .access-locked {
            color: #f44336;
        }
        
        .access-unlocked {
            color: #4CAF50;
        }
        
        /* NEW: Daily Study Limit */
        .daily-limit-warning {
            background: #ffebee;
            color: #c62828;
            padding: 10px;
            border-radius: 5px;
            margin: 10px 0;
            border: 1px solid #ffcdd2;
            text-align: center;
        }
        
        /* NEW: Reset Timer */
        .reset-timer {
            font-size: 0.9em;
            color: #666;
            margin-top: 5px;
        }

        /* NEW LANDING PAGE STYLES FROM SECOND CODE */
        #landing-page.page {
            max-width: 100%;
            width: 100%;
            padding: 0;
            border-radius: 0;
            box-shadow: none;
            background: none;
        }

        body #landing-page {
            background: linear-gradient(135deg, #0b1a0f 0%, #092413 100%);
            color: white;
            line-height: 1.6;
            min-height: 100vh;
            overflow-x: hidden;
        }

        body.dark-mode #landing-page {
            background: linear-gradient(135deg, #121212 0%, #092413 100%);
        }

        /* Digital Glow Effects */
        .glow-text {
            text-shadow: 0 0 10px #00ff88, 0 0 20px #00ff88, 0 0 30px #00ff88;
            animation: glow 2s ease-in-out infinite alternate;
        }

        @keyframes glow {
            from { text-shadow: 0 0 10px #00ff88, 0 0 20px #00ff88, 0 0 30px #00ff88; }
            to { text-shadow: 0 0 15px #00ff99, 0 0 25px #00ff99, 0 0 35px #00ff99; }
        }

        /* Main Header Section */
        .header-container {
            background: linear-gradient(rgba(0, 0, 0, 0.7), rgba(0, 0, 0, 0.7)), 
                        url('https://i.ibb.co/R4jdrrGw/1760989179001.png');
            background-size: cover;
            background-position: center;
            background-attachment: fixed;
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            text-align: center;
            padding: 20px;
            position: relative;
            overflow: hidden;
        }

        .header-container::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: radial-gradient(circle at center, transparent 0%, rgba(0, 0, 0, 0.9) 100%);
        }

        #landing-page .logo-container {
            position: relative;
            z-index: 2;
            margin-bottom: 30px;
            animation: fadeInDown 1s ease-out;
        }

        #landing-page .main-logo {
            font-size: 4rem;
            font-weight: 900;
            margin-bottom: 10px;
            color: white;
            text-transform: uppercase;
            letter-spacing: 3px;
        }

        #landing-page .ihame-meaning {
            font-size: 1.2rem;
            color: #00ff99;
            font-style: italic;
            margin-bottom: 20px;
        }

        .tagline {
            font-size: 1.5rem;
            max-width: 800px;
            margin: 0 auto 40px;
            color: #ffffff;
            text-shadow: 0 2px 10px rgba(0,0,0,0.5);
            position: relative;
            z-index: 2;
            animation: fadeInUp 1s ease-out 0.5s both;
        }

        /* Button Styles */
        .btn-row {
            display: flex;
            gap: 20px;
            margin-top: 30px;
            flex-wrap: wrap;
            justify-content: center;
            position: relative;
            z-index: 2;
            animation: fadeInUp 1s ease-out 0.8s both;
        }

        .main-btn {
            padding: 18px 40px;
            font-size: 1.2rem;
            font-weight: bold;
            border: none;
            border-radius: 50px;
            cursor: pointer;
            transition: all 0.3s ease;
            text-transform: uppercase;
            letter-spacing: 1px;
            position: relative;
            overflow: hidden;
            min-width: 200px;
        }

        .main-btn.primary {
            background: linear-gradient(45deg, #4169E1, #00ff99);
            color: white;
            box-shadow: 0 5px 20px rgba(65, 105, 225, 0.4);
        }

        .main-btn.secondary {
            background: transparent;
            color: white;
            border: 2px solid #00ff99;
            box-shadow: 0 5px 20px rgba(0, 255, 153, 0.3);
        }

        .main-btn:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 25px rgba(0, 255, 153, 0.5);
        }

        .main-btn.primary:hover {
            background: linear-gradient(45deg, #00ff99, #4169E1);
        }

        .main-btn.secondary:hover {
            background: rgba(0, 255, 153, 0.1);
        }

        /* Featured Images Row */
        #landing-page .image-row {
            display: flex;
            justify-content: center;
            gap: 30px;
            margin: 50px 20px;
            flex-wrap: wrap;
            position: relative;
            z-index: 2;
            animation: fadeInUp 1s ease-out 1.1s both;
        }

        #landing-page .circle-image {
            width: 120px;
            height: 120px;
            border-radius: 50%;
            object-fit: cover;
            border: 4px solid #00ff99;
            box-shadow: 0 0 20px rgba(0, 255, 153, 0.5);
            transition: all 0.3s ease;
        }

        #landing-page .circle-image:hover {
            transform: scale(1.1) rotate(5deg);
            box-shadow: 0 0 30px rgba(0, 255, 153, 0.8);
        }

        /* Mission & Vision Section */
        #landing-page .mission-vision-container {
            background: rgba(9, 36, 19, 0.9);
            border-left: 5px solid #00ff99;
            margin: 40px auto;
            padding: 40px;
            border-radius: 20px;
            max-width: 1000px;
            position: relative;
            z-index: 2;
            animation: fadeInUp 1s ease-out 1.4s both;
            backdrop-filter: blur(10px);
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.3);
        }

        #landing-page .mission-vision-container h3 {
            color: #00ff99;
            font-size: 2rem;
            margin-bottom: 25px;
            text-align: center;
            text-transform: uppercase;
            letter-spacing: 2px;
        }

        #landing-page .mission-vision-container p {
            margin-bottom: 20px;
            font-size: 1.1rem;
            line-height: 1.8;
        }

        #landing-page .mission-vision-container strong {
            color: #00ff99;
        }

        /* Features Section */
        .features-section {
            padding: 60px 20px;
            background: rgba(0, 0, 0, 0.7);
            position: relative;
            z-index: 2;
            animation: fadeInUp 1s ease-out 1.7s both;
        }

        .features-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 30px;
            max-width: 1200px;
            margin: 0 auto;
        }

        .feature-card {
            background: rgba(9, 36, 19, 0.8);
            padding: 30px;
            border-radius: 15px;
            text-align: center;
            transition: all 0.3s ease;
            border: 1px solid transparent;
        }

        .feature-card:hover {
            transform: translateY(-10px);
            border-color: #00ff99;
            box-shadow: 0 10px 30px rgba(0, 255, 153, 0.2);
        }

        .feature-icon {
            font-size: 3rem;
            margin-bottom: 20px;
            color: #00ff99;
        }

        .feature-card h4 {
            color: white;
            font-size: 1.5rem;
            margin-bottom: 15px;
        }

        .feature-card p {
            color: #ccc;
            font-size: 1rem;
        }

        /* Language Selector */
        #landing-page .lang-select-container {
            position: fixed;
            bottom: 20px;
            right: 20px;
            z-index: 1000;
            animation: fadeInUp 1s ease-out 2s both;
        }

        #landing-page .lang-select {
            padding: 10px 20px;
            border-radius: 25px;
            background: rgba(9, 36, 19, 0.9);
            color: white;
            border: 2px solid #00ff99;
            font-size: 1rem;
            cursor: pointer;
            outline: none;
            transition: all 0.3s;
        }

        #landing-page .lang-select:hover {
            background: rgba(0, 255, 153, 0.1);
            box-shadow: 0 0 15px rgba(0, 255, 153, 0.3);
        }

        /* Footer */
        #landing-page .footer {
            text-align: center;
            padding: 30px;
            background: rgba(0, 0, 0, 0.9);
            position: relative;
            z-index: 2;
            margin-top: 60px;
        }

        #landing-page .footer p {
            color: #aaa;
            margin-bottom: 10px;
        }

        /* Animations */
        @keyframes fadeInDown {
            from {
                opacity: 0;
                transform: translateY(-50px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        @keyframes fadeInUp {
            from {
                opacity: 0;
                transform: translateY(50px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        /* Responsive Design for Landing Page */
        @media (max-width: 768px) {
            #landing-page .main-logo {
                font-size: 2.5rem;
            }
            
            .tagline {
                font-size: 1.2rem;
                padding: 0 20px;
            }
            
            .btn-row {
                flex-direction: column;
                align-items: center;
            }
            
            .main-btn {
                width: 100%;
                max-width: 300px;
            }
            
            #landing-page .circle-image {
                width: 100px;
                height: 100px;
            }
            
            #landing-page .mission-vision-container {
                padding: 30px 20px;
                margin: 20px;
            }
            
            .features-grid {
                grid-template-columns: 1fr;
            }
        }

        @media (max-width: 480px) {
            #landing-page .main-logo {
                font-size: 2rem;
            }
            
            #landing-page .ihame-meaning {
                font-size: 1rem;
            }
            
            .tagline {
                font-size: 1rem;
            }
            
            #landing-page .circle-image {
                width: 80px;
                height: 80px;
            }
        }
    </style>
</head>
<body>
    <!-- National Anthem Player -->
    <div class="national-anthem-player">
        <button class="mute-btn" id="mute-anthem">🔇</button>
      <audio id=”anthem” autoplay muted controls>
  <source src=”anthem.m4a” type=”audio/mp4”>
  Browser ɗinka bai goyi bayan audio ba
</audio>
    </div>

    <!-- NEW LANDING PAGE (FROM SECOND CODE) -->
    <div id="landing-page" class="page active">
        <!-- Main Header -->
        <div class="header-container">
            <div class="logo-container">
                <h1 class="main-logo glow-text">JAMI'AR IHAME</h1>
                <p class="ihame-meaning">(Ingantacciyar Hausa A Maimakon English!)</p>
            </div>
            
            <p class="tagline">
                Barka da zuwa dandali na farko da ke koyar da ilimin zamani mai zurfi cikin harshen Hausa. 
                Samar da ingantacciyar ilimi, haɓaka fasaha, da samar da ƙwararrun masana a fannoni daban-daban.
            </p>
            
            <div class="btn-row">
                <button class="main-btn primary" onclick="showPage('register-page')">
                    📚 Fara Karatu Yanzu
                </button>
                <button class="main-btn secondary" onclick="showPage('login-page')">
                    🔐 Shiga Asusunka
                </button>
            </div>
        </div>

        <!-- Featured Images -->
        <div class="image-row">
            <img src="https://i.ibb.co/6752LxTX/Screenshot-20251117-150208.jpg" 
                 alt="Sashen Kimiyya" 
                 class="circle-image">
            <img src="https://i.ibb.co/M5fLBJKQ/gana-j.jpg" 
                 alt="Dalibai masu karatu" 
                 class="circle-image">
            <img src="https://i.ibb.co/F4qJ77CP/File-Flag-of-the-Hausa-people-svg-Wikipedia.jpg" 
                 alt="Tutar Hausawa" 
                 class="circle-image">
            <img src="https://i.ibb.co/R4jdrrGw/1760989179001.png" 
                 alt="Ginin Jami'ar" 
                 class="circle-image">
        </div>

        <!-- Mission & Vision -->
        <div class="mission-vision-container">
            <h3>Manufa da Buri na Jami'ar Ihame</h3>
            
            <p><strong>Manufa:</strong> Samar da ingantacciyar ilimi ta hanyar Hausa, tare da ba da damar koyan fannoni daban-daban na zamani a cikin harshen Hausa. 
               Mu kasance tushen ilimi wanda ke ba da cikakken bayani da ƙwarewa ga al'umma.</p>
            
            <p><strong>Buri:</strong> Zama cibiyar ilimi ta farko da ke ba da cikakken ilimi a cikin harshen Hausa, tare da samar da ƙwararrun masana 
               a fannoni daban-daban waɗanda za su taimaka wajen ci gaban al'umma da ƙasa.</p>
            
            <p><strong>Ƙimar Mu:</strong> 
               <span style="color: #00ff99;">I</span>ngantacciya - 
               <span style="color: #00ff99;">H</span>aɗin Kai - 
               <span style="color: #00ff99;">A</span>l'ada - 
               <span style="color: #00ff99;">M</span>a'ana - 
               <span style="color: #00ff99;">E</span>llah</p>
        </div>

        <!-- Features Section -->
        <div class="features-section">
            <div class="features-grid">
                <div class="feature-card">
                    <div class="feature-icon">💻</div>
                    <h4>Ilimin Zamani</h4>
                    <p>Koyan fannoni na zamani kamar AI, Cybersecurity, Software Engineering da sauransu cikin Hausa</p>
                </div>
                
                <div class="feature-card">
                    <div class="feature-icon">📜</div>
                    <h4>Shaida Ta Hukuma</h4>
                    <p>Samun takardar shaidar kammalawa bayan an kammala karatun a kowane mataki</p>
                </div>
                
                <div class="feature-card">
                    <div class="feature-icon">🤖</div>
                    <h4>Malam AI</h4>
                    <p>Malam na wucin gadi wanda zai koyar da ku kowane darasi a lokacin da kuka zaɓa</p>
                </div>
                
                <div class="feature-card">
                    <div class="feature-icon">💬</div>
                    <h4>Dandalin Tattaunawa</h4>
                    <p>Haɗuwa da sauran dalibai da malamai don tattaunawa da taimakon juna</p>
                </div>
                
                <div class="feature-card">
                    <div class="feature-icon">🌐</div>
                    <h4>A Nesa Ko Kusa</h4>
                    <p>Yi karatu daga ko'ina cikin duniya a lokacin da kuka zaɓa</p>
                </div>
                
                <div class="feature-card">
                    <div class="feature-icon">💼</div>
                    <h4>Damar Aiki</h4>
                    <p>Samun ƙwarewa da ilimin da za su ba ku damar samun aiki ko kasuwanci</p>
                </div>
            </div>
        </div>

        <!-- Language Selector -->
        <div class="lang-select-container">
            <select class="lang-select" onchange="changeLanguage(this.value)">
                <option value="ha" selected>🇳🇬 Hausa</option>
                <option value="en">🇬🇧 English</option>
            </select>
        </div>

        <!-- Footer -->
        <div class="footer">
            <p>© 2024 JAMI'AR IHAME. Duk haƙƙoƙin suna tare da mu.</p>
            <p>Ingantacciyar Hausa A Maimakon English!</p>
            <p>Tuntubemu: abduldocter1@gmail.com | ☎ 707 199 2912</p>
        </div>
    </div>

     <!-- Login Page -->
    <div id="login-page" class="page">
        <header>
            <button class="back-btn" onclick="showPage('landing-page')">←</button>
            <h2 data-lang="login-title">Shiga Asusu</h2>
        </header>
        
        <div class="login-type-selection">
            <button class="login-type-btn active" id="student-login-btn" onclick="selectLoginType('student')">Dalibi</button>
            <button class="login-type-btn" id="admin-login-btn" onclick="selectLoginType('admin')">Admin</button>
        </div>
        
        <div id="student-login-form">
            <input type="text" id="login-regno" data-lang="input-regno" placeholder="Lambar Rajista (Reg. No.)">
            <input type="password" id="login-password" data-lang="input-password" placeholder="Kalmar Sirri">
            <div class="remember-me">
                <input type="checkbox" id="remember-me-checkbox">
                <label for="remember-me-checkbox" data-lang="remember-me">Tuna ni a wannan na'ura</label>
            </div>
            <button onclick="loginUser()" data-lang="login-btn">Shiga</button>
            <p data-lang="register-prompt">Baka da asusu? <a href="#" onclick="showPage('register-page')">Yi Rajista</a></p>
            <p><a href="#" onclick="showPage('forgot-password-page')">Manta kalmar sirri?</a></p>
        </div>
        
        <div id="admin-login-form" style="display: none;">
            <input type="text" id="admin-email" data-lang="input-email" placeholder="Email">
            <input type="password" id="admin-password" data-lang="input-password" placeholder="Password">
            <button onclick="loginAdmin()" data-lang="login-btn">Shiga</button>
        </div>
    </div>
    
    <!-- Forgot Password Page -->
    <div id="forgot-password-page" class="page">
        <header>
            <button class="back-btn" onclick="showPage('login-page')">←</button>
            <h2>Manta Kalmar Sirri</h2>
        </header>
        <div class="password-reset-container">
            <div class="password-reset-form">
                <p>Shigar da email ɗinka don samun sabon kalmar sirri:</p>
                <input type="email" id="forgot-password-email" placeholder="Email">
                <button onclick="resetPassword()">Aika Sabon Kalmar Sirri</button>
            </div>
            <div id="reset-success" class="reset-success" style="display: none;">
                <p>An aika sabon kalmar sirri zuwa email ɗinka. Da fatan za a duba inbox ɗinka.</p>
            </div>
        </div>
    </div>
    
    <!-- Register Page -->
    <div id="register-page" class="page">
        <header>
            <button class="back-btn" onclick="showPage('landing-page')">←</button>
            <h2 data-lang="register-title">Barka da zuwa JAMI'AR IHAME</h2>
        </header>
        <p data-lang="register-subtitle">Yi Rajista don fara karatu</p>
        
        <!-- Payment Tier Selection -->
        <div class="payment-tier-selection">
            <button class="payment-tier-btn active" id="free-tier-btn" onclick="selectPaymentTier('free')">Karatun Wucin Gadi (Free)</button>
            <button class="payment-tier-btn" id="paid-tier-btn" onclick="selectPaymentTier('paid')">Cikakken Karatu (Biya)</button>
        </div>
        
        <input type="text" id="reg-name" data-lang="input-name" placeholder="Cikakken Suna">
        <input type="number" id="reg-birth-year" placeholder="Shekarar Haihuwa">
        <input type="file" id="reg-photo" accept="image/*">
        <input type="email" id="reg-email" data-lang="input-email" placeholder="Email">
        <input type="password" id="reg-password" data-lang="input-password" placeholder="Kalmar Sirri">
        
        <div class="phone-input-container">
            <select id="country-code">
                <option value="+234" selected>+234 (NG) 🇳🇬 Najeriya</option>
            </select>
            <input type="tel" id="reg-phone" placeholder="Lambar Wayar">
        </div>
        
        <input type="text" id="reg-previous-education" placeholder="Inda kika yi karatu a baya">
        
        <select id="reg-education-level">
            <option value="">Matakin Karatu: Wanda ka taba yi</option>
            <option value="lesson">Lesson</option>
            <option value="primary">Primary</option>
            <option value="jss">JSS</option>
            <option value="gss">GSS</option>
            <option value="diploma">Diploma</option>
            <option value="national-diploma">National Diploma</option>
            <option value="highest-diploma">Highest Diploma</option>
            <option value="highest-national-diploma">Highest National Diploma</option>
            <option value="degree">Degree</option>
            <option value="other">Wani daban</option>
        </select>
        
        <select id="reg-faculty" onchange="populateDepartments()" data-lang="select-faculty">
            <option value="">Faculty</option>
        </select>
        
        <select id="reg-department" data-lang="select-dept" disabled>
            <option value="">Department</option>
        </select>
        
        <select id="reg-level">
            <option value="">Level</option>
            <option value="basic">Karamin Mataki/Basic</option>
            <option value="intermediate">Matsakaicin Mataki/Intermediate</option>
            <option value="advance">Babban Mataki/Advance</option>
        </select>
        
        <!-- Study Schedule -->
        <div id="free-study-schedule">
            <select id="reg-study-time-free">
                <option value="">Zabar Lokacin Karatu</option>
                <option value="morning">Safiya</option>
                <option value="afternoon">Rana</option>
                <option value="evening">Yamma</option>
            </select>
            
            <div id="study-days-container-free">
                <label>Zaɓi Ranakun Karatu (4 Ranaku a Sati):</label>
                <div>
                    <input type="checkbox" id="study-monday-free" value="Monday"><label for="study-monday-free">Litinin</label>
                    <input type="checkbox" id="study-tuesday-free" value="Tuesday"><label for="study-tuesday-free">Talata</label>
                    <input type="checkbox" id="study-wednesday-free" value="Wednesday"><label for="study-wednesday-free">Laraba</label>
                    <input type="checkbox" id="study-thursday-free" value="Thursday"><label for="study-thursday-free">Alhamis</label>
                    <input type="checkbox" id="study-friday-free" value="Friday"><label for="study-friday-free">Jumma'a</label>
                    <input type="checkbox" id="study-saturday-free" value="Saturday"><label for="study-saturday-free">Asabar</label>
                    <input type="checkbox" id="study-sunday-free" value="Sunday"><label for="study-sunday-free">Lahadi</label>
                </div>
            </div>
        </div>
        
        <div id="paid-study-schedule" style="display: none;">
            <select id="reg-study-time-paid">
                <option value="">Zabar Lokacin Karatu</option>
                <option value="morning">Safiya</option>
                <option value="afternoon">Rana</option>
                <option value="evening">Yamma</option>
                <option value="anytime">Kowane Lokaci</option>
            </select>
            
            <div id="study-days-container-paid">
                <label>Zaɓi Ranakun Karatu (Duk Ranaku):</label>
                <div>
                    <input type="checkbox" id="study-monday-paid" value="Monday" checked><label for="study-monday-paid">Litinin</label>
                    <input type="checkbox" id="study-tuesday-paid" value="Tuesday" checked><label for="study-tuesday-paid">Talata</label>
                    <input type="checkbox" id="study-wednesday-paid" value="Wednesday" checked><label for="study-wednesday-paid">Laraba</label>
                    <input type="checkbox" id="study-thursday-paid" value="Thursday" checked><label for="study-thursday-paid">Alhamis</label>
                    <input type="checkbox" id="study-friday-paid" value="Friday" checked><label for="study-friday-paid">Jumma'a</label>
                    <input type="checkbox" id="study-saturday-paid" value="Saturday" checked><label for="study-saturday-paid">Asabar</label>
                    <input type="checkbox" id="study-sunday-paid" value="Sunday" checked><label for="study-sunday-paid">Lahadi</label>
                </div>
            </div>
        </div>
        
        <!-- Banking Information for Paid Tier -->
        <div id="banking-info" class="banking-info" style="display: none;">
            <h3>Bayanin Biyan Kuɗi</h3>
            <div class="banking-details">
                <p><strong>Lambar Asusu:</strong> 22213099231</p>
                <p><strong>Banki:</strong> United Bank of Africa (UBA)</p>
                <p><strong>Sunan Mai Asusu:</strong> Abdulhadi Lawal</p>
                <p><strong>Adadin Kuɗi:</strong> <span id="faculty-price">₦0</span></p>
            </div>
            <p>Bayan biyan kuɗi, danna maɓallin WhatsApp don aika hujjar biyan kuɗi.</p>
            <button class="whatsapp-btn" onclick="sendPaymentProof()">Aika Hujjar Biyan Kuɗi ta WhatsApp</button>
        </div>
        
        <div class="payment-info">
            <p data-lang="payment-info">Bayan rajista, za a ba ku cikakkun bayanan biyan kuɗi domin samun lambar rajista.</p>
        </div>
        
        <button onclick="registerUser()" data-lang="register-btn">Shiga yin Register</button>
        <button class="whatsapp-reg-btn" onclick="openWhatsApp()" data-lang="whatsapp-btn">Samun Lambar register</button>
    </div>

    <!-- Dashboard Page -->
    <div id="dashboard-page" class="page">
        <header>
            <button class="menu-btn" onclick="toggleMenu()">⋮</button>
            <img class="logo-image" src="https://i.ibb.co/sdnqkPnP/Royal-Blue-and-Gold-University-Logo-20250822-190530-0000.png" alt="University Logo">
            <div class="header-right">
                <div class="notification-container">
                    <button class="profile-btn" onclick="showPage('profile-page')">👤</button>
                    <span id="notification-badge" class="notification-badge" style="display: none;">0</span>
                </div>
                <button class="settings-btn" onclick="showPage('settings-page')">⚙️</button>
                <button class="admin-btn" onclick="showPage('admin-page')" data-lang="admin-btn">Admin Panel</button>
            </div>
        </header>
        <div class="dashboard-content">
            <!-- Tokens Display -->
            <div class="tokens-display" id="tokens-display">
                <div class="tokens-info">
                    <div>
                        <strong>Tokens na Yau:</strong>
                        <div class="tokens-count" id="tokens-count">0</div>
                    </div>
                    <div>
                        <strong>Darussa na Yau:</strong>
                        <div class="tokens-count" id="lessons-today">0</div>
                    </div>
                </div>
                <div id="tokens-warning" class="tokens-warning" style="display: none;">
                    Ka cinye dukkan tokens na yau. Za ka iya karatu gobe.
                </div>
                <div class="reset-timer" id="reset-timer">Za a sabunta tokens: <span id="reset-time">23:59:59</span></div>
            </div>
            
            <!-- Free Tier Timer -->
            <div id="free-tier-timer" class="free-tier-timer" style="display: none;">
                <p>Lokacin Karatun Wucin Gadi: <span id="timer-display">168:00:00</span></p>
            </div>
            
            <p id="welcome-message" style="text-align: center; font-size: 1.2em; font-weight: bold;"></p>
            
            <div class="dashboard-stats">
                <div class="dashboard-stat">
                    <div class="dashboard-stat-icon">📚</div>
                    <div class="dashboard-stat-value" id="selected-course-short">-</div>
                    <div class="dashboard-stat-label">Darasi</div>
                </div>
                <div class="dashboard-stat">
                    <div class="dashboard-stat-icon">🏆</div>
                    <div class="dashboard-stat-value" id="student-reward">-</div>
                    <div class="dashboard-stat-label">Reward</div>
                </div>
                <div class="dashboard-stat">
                    <div class="dashboard-stat-icon">📅</div>
                    <div class="dashboard-stat-value" id="next-class">-</div>
                    <div class="dashboard-stat-label">Next Class</div>
                </div>
            </div>
            
            <!-- Tier Limitations Notice -->
            <div id="free-tier-limitations" class="tier-limitations" style="display: none;">
                <h3>Iyakar Karatun Wucin Gadi</h3>
                <ul>
                    <li>Darussan farko 3 na kowane sashe kawai</li>
                    <li>800 tokens a kullum</li>
                    <li>Darasi ɗaya a rana</li>
                    <li>Tambayoyi 3 a rana</li>
                    <li>Jarrabawa ɗaya a wata</li>
                    <li>Ba za a iya kammala dukkan darussa ba</li>
                    <li>Ba za a iya samun shaidar kammalawa ba</li>
                </ul>
                <button onclick="upgradeToPaid()">Canja zuwa Cikakken Karatu</button>
            </div>
            
            <div id="paid-tier-benefits" class="tier-limitations" style="display: none; background: #e8f5e9;">
                <h3>Faidodin Cikakken Karatu</h3>
                <ul>
                    <li>2000 tokens a kullum</li>
                    <li>Darasi ɗaya a rana</li>
                    <li>Tambayoyi mara iyaka a rana</li>
                    <li>Jarrabawa mara iyaka</li>
                    <li>Za a iya kammala dukkan darussa 40</li>
                    <li>Za a iya samun shaidar kammalawa</li>
                    <li>Duk modules suna buɗe</li>
                </ul>
            </div>
            
            <div class="info-card">
                <h3 data-lang="selected-course-title">Darasi da ka zaɓa</h3>
                <p id="selected-course-name"></p>
                <div class="points-container">
                    <div>
                        <span data-lang="percentage-label">Kashi:</span>
                        <span id="percentage-display" class="points-display">0%</span>
                    </div>
                </div>
                <div class="progress-bar-container">
                    <div id="progress-bar" class="progress-bar"></div>
                </div>
                <p id="progress-text" data-lang="progress-text">An kammala: 0%</p>
            </div>
            <div class="exam-progress">
                <h3>Percent na Jarabawa</h3>
                <div class="exam-progress-bar-container">
                    <div id="exam-progress-bar" class="exam-progress-bar"></div>
                </div>
                <span id="exam-percentage-display" class="exam-percentage-display">0%</span>
            </div>
            <div class="action-buttons">
                <button id="ai-teacher-btn" onclick="showPage('ai-teacher-page')">Malam AI</button>
                <button onclick="showPage('courses-list-page')" data-lang="courses-list-btn">Darussa</button>
                <button id="certificate-btn" class="disabled" onclick="showPage('certificate-page')" data-lang="certificate-btn">Shaidar Kammalawa</button>
                <button id="daily-quiz-btn" onclick="loadDailyQuiz(); showPage('daily-quiz-page')" data-lang="daily-quiz-btn">Jarabawa na Kullum</button>
                <button onclick="showPage('calendar-page')">Kalanda</button>
            </div>
        </div>
        <div class="help-center">
            <a href="mailto:abduldocter1@gmail.com" data-lang="help-center-text">Help Center</a> | <a href="#" onclick="showPage('help-center-page')">Socials</a>
        </div>
    </div>
    
    <!-- AI Teacher Page -->
    <div id="ai-teacher-page" class="page">
        <header>
            <button class="back-btn" onclick="showPage('dashboard-page')">←</button>
            <h2>Malam AI</h2>
        </header>
        
        <!-- Tokens Warning -->
        <div id="ai-tokens-warning" class="daily-limit-warning" style="display: none;">
            Ka cinye dukkan tokens na yau. Ba za ka iya yin karatu ba sai gobe.
        </div>
        
        <!-- Daily Limit Warning -->
        <div id="daily-limit-warning" class="daily-limit-warning" style="display: none;">
            Ka yi darasi ɗaya a yau. Ba za ka iya ƙara yin karatu ba sai gobe.
        </div>
        
        <div class="ai-teacher-container">
            <!-- Language Selection for AI Teacher -->
            <div class="lang-select-container">
                <label for="ai-lang-select">Harshen Koyarwa:</label>
                <select id="ai-lang-select" onchange="changeAITeacherLanguage(this.value)">
                    <option value="ha" selected>Hausa</option>
                    <option value="en">English</option>
                </select>
            </div>
            
            <!-- Module Access Control -->
            <div class="module-access-control" id="module-access-control">
                <div class="access-status">
                    <span>Damar Karatu na Yau:</span>
                    <span id="access-status" class="access-unlocked">✅ A buɗe</span>
                </div>
                <div class="access-status">
                    <span>Adadin Tokens:</span>
                    <span id="ai-tokens-count">0</span>
                </div>
                <div class="access-status">
                    <span>Darasi na Yau:</span>
                    <span id="ai-lesson-today">0/1</span>
                </div>
            </div>
            
            <div class="level-selection">
                <h3>Zaɓi Level da Zango</h3>
                <select id="ai-level-select">
                    <option value="">Zaɓi Level</option>
                    <option value="basic">Karamin Mataki/Basic</option>
                    <option value="intermediate">Matsakaicin Mataki/Intermediate</option>
                    <option value="advance">Babban Mataki/Advance</option>
                </select>
                <select id="ai-semester-select">
                    <option value="">Zaɓi Zango</option>
                    <option value="zango1">Zango na Farko</option>
                    <option value="zango2">Zango na Biyu</option>
                </select>
                <button onclick="loadAITopics()">Zaɓi Topic</button>
            </div>
            
            <div id="ai-topics-container" style="display: none;">
                <h3>Zaɓi Topic:</h3>
                <div id="ai-topics-list"></div>
            </div>
            
            <div id="ai-teaching-content" style="display: none;">
                <!-- Audio Player for AI Content -->
                <div class="audio-player">
                    <button onclick="playAIContent()">▶️ Karanta</button>
                    <button onclick="pauseAIContent()">⏸️ Tsaya</button>
                    <button onclick="stopAIContent()">⏹️ Daina</button>
                </div>
                
                <div class="ai-content-display" id="ai-teacher-response">
                    <!-- AI teaching content will be displayed here -->
                </div>
                <div class="ai-teacher-actions">
                    <button onclick="regenerateAIResponse()">Regenerate</button>
                    <button onclick="copyAIContent()">Kwafa</button>
                    <button onclick="saveToNotepad()">Ajiye a Notepad</button>
                </div>
                <div class="interactive-quiz" id="ai-quiz-container">
                    <!-- AI quiz will be displayed here -->
                </div>
            </div>
            
            <div id="ai-chat-container" style="display: none;">
                <div class="ai-chat-messages" id="ai-chat-messages">
                    <div class="ai-message ai-response">
                        <div class="message-sender">Malam AI</div>
                        <div class="message-text">Barka da zuwa! Ina iya taimaka muku da kowane darasi. Zaɓi wani topic daga cikin modules ɗin ku ko kuma yi tambaya.</div>
                        <div class="message-time">Yanzu</div>
                    </div>
                </div>
                <div class="ai-chat-input-container">
                    <input type="text" class="ai-chat-input" id="ai-chat-input" placeholder="Yi tambaya ko zaɓi topic...">
                    <button class="send-ai-chat-btn" onclick="sendAIMessage()">Aika</button>
                </div>
            </div>
        </div>
    </div>
    
    <!-- Calendar Page -->
    <div id="calendar-page" class="page">
        <header>
            <button class="back-btn" onclick="showPage('dashboard-page')">←</button>
            <h2>Kalanda</h2>
        </header>
        
        <div class="calendar-container">
            <div class="calendar-header">
                <button onclick="changeCalendarMonth(-1)">←</button>
                <h3 id="calendar-month-year"></h3>
                <button onclick="changeCalendarMonth(1)">→</button>
            </div>
            <div class="calendar-grid" id="calendar-grid">
                <!-- Calendar days will be generated here -->
            </div>
        </div>
        
        <div class="upcoming-classes">
            <h3>Darussan nan gaba</h3>
            <div id="upcoming-classes-list">
                <!-- Upcoming classes will be listed here -->
            </div>
        </div>
    </div>
    
    <!-- Notepad Page -->
    <div id="notepad-page" class="page">
        <header>
            <button class="back-btn" onclick="showPage('dashboard-page')">←</button>
            <h2>Notepad</h2>
        </header>
        
        <div class="notepad-container">
            <div class="notepad-content" id="notepad-content" contenteditable="true">
                <!-- Notepad content will be here -->
            </div>
            <div class="notepad-actions">
                <button onclick="saveNotepad()">Ajiye</button>
                <button id="download-notepad-btn" onclick="downloadNotepad()">Sauke</button>
                <button onclick="clearNotepad()">Share</button>
            </div>
        </div>
    </div>

    <!-- Profile Page -->
    <div id="profile-page" class="page">
        <header>
            <button class="back-btn" onclick="showPage('dashboard-page')">←</button>
            <h2 data-lang="profile-title">Bayanan ka</h2>
        </header>
        <div class="profile-content">
            <img id="profile-pic-preview" src="" alt="Profile Picture">
            <input type="file" id="profile-pic-input" accept="image/*" style="display:none;" onchange="previewProfilePic(event)">
            <button onclick="document.getElementById('profile-pic-input').click()">Zaɓi Hoto</button>
            
            <div id="profile-display-fields" class="profile-display-fields">
                <p><strong data-lang="profile-regno-label">Reg. No:</strong> <span id="profile-regno-display"></span></p>
                <p><strong data-lang="profile-name-label">Suna:</strong> <span id="profile-name-display"></span></p>
                <p><strong data-lang="profile-email-label">Email:</strong> <span id="profile-email-display"></span></p>
                <p><strong data-lang="profile-faculty-label">Faculty:</strong> <span id="profile-faculty-display"></span></p>
                <p><strong data-lang="profile-department-label">Department:</strong> <span id="profile-department-display"></span></p>
                <p><strong data-lang="profile-level-label">Level:</strong> <span id="profile-level-display"></span></p>
                <p><strong>Inda kika yi karatu a baya:</strong> <span id="profile-previous-education-display"></span></p>
                <p><strong>Lokacin Karatu:</strong> <span id="profile-study-time-display"></span></p>
                <p><strong>Ranakun Karatu:</strong> <span id="profile-study-days-display"></span></p>
                <p><strong>Nau'in Karatu:</strong> <span id="profile-tier-display"></span></p>
                <p><strong>Tokens na Yau:</strong> <span id="profile-tokens-display">0</span></p>
                <p><strong>Darussan Yau:</strong> <span id="profile-lessons-today">0/1</span></p>
                <button class="edit-profile-btn" onclick="enableProfileEdit()" data-lang="edit-profile-btn">Gyara Bayanai</button>
                <button class="change-password-btn" onclick="showChangePassword()">Canza Kalmar Sirri</button>
            </div>
            
            <div id="profile-edit-fields" class="profile-edit-fields" style="display: none;">
                <input type="text" id="edit-name" placeholder="Cikakken Suna">
                <input type="email" id="edit-email" placeholder="Email">
                <input type="tel" id="edit-phone" placeholder="Lambar Wayar">
                <button class="save-profile-btn" onclick="saveProfileChanges()" data-lang="save-profile-btn">Ajiye Canje-Canje</button>
                <button class="cancel-edit-btn" onclick="cancelProfileEdit()">Soke</button>
            </div>
            
            <div id="change-password-fields" style="display: none; margin-top: 20px;">
                <h3>Canza Kalmar Sirri</h3>
                <input type="password" id="current-password" placeholder="Tsohon Kalmar Sirri">
                <input type="password" id="new-password" placeholder="Sabuwar Kalmar Sirri">
                <input type="password" id="confirm-password" placeholder="Tabbatar da Sabuwar Kalmar Sirri">
                <button onclick="changePassword()">Canza Kalmar Sirri</button>
                <button onclick="cancelPasswordChange()">Soke</button>
            </div>
        </div>
    </div>
    
    <!-- Admin Page -->
    <div id="admin-page" class="page admin-page">
        <header>
            <button class="back-btn" onclick="showPage('dashboard-page')">←</button>
            <h2 data-lang="admin-title">Admin Dashboard</h2>
            <button onclick="logout()">Fita</button>
        </header>
        <div class="page-content">
            <div class="admin-role-tabs" id="admin-role-tabs">
                <!-- Admin tabs will be dynamically generated based on admin role -->
            </div>
            
            <div id="admin-panel-content">
                <!-- Admin panel content will be dynamically generated -->
            </div>
        </div>
    </div>
    
    <!-- Admin Alumni Page -->
    <div id="admin-alumni-page" class="page admin-page">
        <header>
            <button class="back-btn" onclick="showPage('admin-page')">←</button>
            <h2>Tsofaffin Dalibai (Alumni)</h2>
        </header>
        <div class="alumni-container">
            <h3>Jerin Tsofaffin Dalibai</h3>
            <div class="alumni-list" id="alumni-list">
                <!-- Alumni list will be generated here -->
            </div>
        </div>
    </div>

    <!-- Student Details Page -->
    <div id="student-details-page" class="page">
        <header>
            <button class="back-btn" onclick="showPage('admin-page')">←</button>
            <h2 data-lang="student-details-title">Bayanan Dalibi</h2>
        </header>
        <div class="admin-student-details">
            <img id="student-pic-display" src="" alt="Student Picture">
            <div class="student-details">
                <p><strong data-lang="profile-regno-label">Reg. No:</strong> <span id="student-regno-display"></span></p>
                <p><strong data-lang="profile-name-label">Suna:</strong> <span id="student-name-display"></span></p>
                <p><strong data-lang="profile-email-label">Email:</strong> <span id="student-email-display"></span></p>
                <p><strong data-lang="profile-faculty-label">Faculty:</strong> <span id="student-faculty-display"></span></p>
                <p><strong data-lang="profile-department-label">Department:</strong> <span id="student-department-display"></span></p>
                <p><strong data-lang="profile-level-label">Level:</strong> <span id="student-level-display"></span></p>
                <p><strong>Nau'in Karatu:</strong> <span id="student-tier-display"></span></p>
                <p><strong>Hali:</strong> <span id="student-status-display"><span class="activity-indicator active-now"></span> Active</span></p>
                <p><strong>Kashi na Kammalawa:</strong> <span id="student-progress-display">0%</span></p>
                <p><strong>Maki na Certificate:</strong> <span id="student-certificate-score">-</span></p>
                <p><strong>Tokens na Yau:</strong> <span id="student-tokens-display">0</span></p>
                <p><strong>Darussan Yau:</strong> <span id="student-lessons-today">0/1</span></p>
            </div>
            <div>
                <h3>Aika Sanarwa</h3>
                <input type="text" id="student-notification-message" placeholder="Saƙon sanarwa">
                <button onclick="sendNotificationToStudent()">Aika Sanarwa</button>
            </div>
            <div class="admin-student-actions">
                <h3>Canza Bayanan Dalibi</h3>
                <button onclick="enableStudentEdit()">Canza Bayanai</button>
                <button onclick="resetStudentPassword()">Canza Kalmar Sirri</button>
                <button onclick="changeStudentTier()">Canza Nau'in Karatu</button>
                <button onclick="resetStudentTokens()">Sabunta Tokens</button>
            </div>
        </div>
    </div>

    <!-- Courses List Page -->
    <div id="courses-list-page" class="page">
        <header>
            <button class="back-btn" onclick="showPage('dashboard-page')">←</button>
            <h2 data-lang="all-courses-title">Dukkan Darussa</h2>
            <div class="search-bar">
                <input type="text" class="search-input" id="course-search" placeholder="Nemo darasi...">
                <span class="search-icon">🔍</span>
            </div>
        </header>
        <div class="course-date-selector">
            <label for="course-date-select">Zaɓi Ranar:</label>
            <input type="date" id="course-date-select" onchange="loadCoursesForDate()">
        </div>
        <div id="courses-list-content">
            </div>
    </div>

    <!-- Modules Page -->
    <div id="modules-page" class="page">
        <header>
            <button class="back-btn" onclick="showPage('dashboard-page')">←</button>
            <h2 id="modules-page-title" data-lang="modules-page-title">Modules na Darasi</h2>
            <div class="points-container">
                <div>
                    <span data-lang="percentage-label">Kashi:</span>
                    <span id="module-percentage-display" class="points-display">0%</span>
                </div>
            </div>
        </header>
        <div class="progress-summary">
            <p data-lang="completed-modules-label">Modules da aka kammala:</p>
            <p id="completed-modules-count">0</p>
        </div>
        <div id="modules-list">
            <hr>
        </div>
    </div>

    <!-- Learning Page -->
    <div id="learning-page" class="page">
        <header>
            <button class="back-btn" onclick="showPage('modules-page')">←</button>
            <h2 id="learning-page-title"></h2>
            <div class="module-progress">
                <div class="module-progress-bar">
                    <div id="module-progress-fill" class="module-progress-fill"></div>
                </div>
                <span class="module-progress-text" id="current-module-percentage">0%</span>
            </div>
        </header>
        <div class="learning-content" id="module-content">
            </div>
        <div class="navigation-buttons-improved">
            <button id="prev-lesson-btn" class="disabled" data-lang="prev-btn">Baya</button>
            <button id="next-lesson-btn" data-lang="next-btn">Gaba</button>
        </div>
    </div>

    <!-- Daily Quiz Page -->
    <div id="daily-quiz-page" class="page">
        <header>
            <button class="back-btn" onclick="showPage('dashboard-page')">←</button>
            <h2 data-lang="daily-quiz-title">Jarabawa na Kullum</h2>
        </header>
        <div id="daily-quiz-content">
            </div>
    </div>

    <!-- Certificate Page -->
    <div id="certificate-page" class="page">
        <header>
            <button class="back-btn" onclick="showPage('dashboard-page')">←</button>
            <h2 data-lang="certificate-title">Shaidar Kammalawa</h2>
        </header>
        <div id="certificate-content" class="certificate-content-improved">
            <div class="certificate-watermark">JAMI'AR IHAME</div>
            <img src="https://i.ibb.co/sdnqkPnP/Royal-Blue-and-Gold-University-Logo-20250822-190530-0000.png" alt="University Logo" class="certificate-logo">
            <div class="certificate-header">
                <h1>JAMI'AR IHAME</h1>
                <h3>(Ingantacciyar Hausa A Maimakon Englishi)</h3>
                <p><strong>Lambar Rijista:</strong> <span id="certificate-regno"></span></p>
            </div>
            
            <div class="certificate-body">
                <h3>BAYANIN SAKAMAKO</h3>
                <p>Wannan shaidar ta tabbatar da cewa</p>
                <h2 id="certificate-student-name"></h2>
                <p>Ya kammala ingantaccen shirin karatu kuma ya ci nasara a jarabawar da aka kayyade, an ba shi, bisa ikon Hukumar Ilimi,</p>
                <p><strong>CERTIFICIFICATE</strong> na Jami'ar Ihame a cikin</p>
                <h3 id="certificate-department"></h3>
                <p>A ranar <span id="certificate-date"></span>.</p>
                <p id="certificate-reward"></p>
                <p id="certificate-score"></p>
            </div>
            
            <div class="certificate-signatures">
                <div class="certificate-signature">
                    <img src="https://i.ibb.co/XZk4zjp4/1761211249054.jpg" alt="Sa hannun Shugaban Jami'a">
                    <div class="signature-line"></div>
                    <p>Sa hannun shugaban Jami'a</p>
                    <p><strong>Abdulhadi Lawal</strong></p>
                </div>
                <div class="certificate-signature">
                    <img src="https://i.ibb.co/dsWXSgpX/Screenshot-20250829-114940.jpg" alt="Sa hannun Registrar">
                    <div class="signature-line"></div>
                    <p>Sa hannun Registrar</p>
                    <p><strong>Hibbatullah Musa</strong></p>
                </div>
            </div>
        </div>
        <button onclick="downloadCertificate('image')">Download as Hoto</button>
        <button onclick="downloadCertificate('pdf')">Download as PDF</button>
        <button onclick="printCertificate()">Print</button>
        <button onclick="shareCertificate()">Tura zuwa Sada Zumunta</button>
    </div>

    <!-- Department Chat Page -->
    <div id="department-chat-page" class="page">
        <header>
            <button class="back-btn" onclick="showPage('dashboard-page')">←</button>
            <h2>Tattaunawar Department</h2>
        </header>
        <div class="group-chat-header">
            <div>
                <h3>Group Chat</h3>
                <div class="group-chat-stats" id="group-chat-stats">
                    <!-- Department stats will be displayed here -->
                </div>
            </div>
        </div>
        <div class="chat-container">
            <div class="chat-messages" id="department-chat-messages">
                <p>Zaɓi department daga ƙasa don fara tattaunawa</p>
            </div>
            <div class="chat-media-upload">
                <input type="file" id="chat-media-input" accept="image/*,video/*,audio/*" style="display: none;">
                <button onclick="document.getElementById('chat-media-input').click()">Upload Media</button>
            </div>
            <div class="chat-media-preview" id="chat-media-preview"></div>
            <div class="chat-input-container">
                <input type="text" class="chat-input" id="chat-message-input" placeholder="Rubuta saƙonka anan...">
                <button class="send-chat-btn" onclick="sendChatMessage()">Aika</button>
            </div>
        </div>
        <select id="department-chat-select" onchange="loadDepartmentChat()">
            <option value="">Zaɓi Department</option>
        </select>
    </div>

    <!-- Settings Page -->
    <div id="settings-page" class="page">
        <header>
            <button class="back-btn" onclick="showPage('dashboard-page')">←</button>
            <h2 data-lang="settings-title">Saituna</h2>
        </header>
        <div class="settings-content">
            <div class="settings-display-container" id="settings-display">
                <h3>Display Settings</h3>
                <div class="setting-item">
                    <label for="font-size-select" data-lang="font-size-label">Girman Rubutu:</label>
                    <select id="font-size-select">
                        <option value="16px">Normal</option>
                        <option value="18px">Medium</option>
                        <option value="20px">Large</option>
                    </select>
                </div>
                <div class="setting-item">
                    <label for="font-style-select" data-lang="font-style-label">Nau'in Rubutu:</label>
                    <select id="font-style-select">
                        <option value="Nunito, sans-serif">Nunito</option>
                        <option value="Roboto, sans-serif">Roboto</option>
                        <option value="Montserrat, sans-serif">Montserrat</option>
                        <option value="Playfair Display, serif">Playfair Display</option>
                        <option value="Open Sans, sans-serif">Open Sans</option>
                        <option value="Poppins, sans-serif">Poppins</option>
                    </select>
                </div>
                <div class="setting-item">
                    <label for="brightness-slider" data-lang="brightness-level-label">Hasken Allo:</label>
                    <input type="range" id="brightness-slider" min="0.1" max="1" step="0.1" value="1">
                </div>
                <div class="setting-item">
                    <label for="brightness-color-select">Zaɓi Launi:</label>
                    <div class="brightness-colors">
                        <div class="brightness-color white selected" onclick="selectBrightnessColor('white')"></div>
                        <div class="brightness-color black" onclick="selectBrightnessColor('black')"></div>
                        <div class="brightness-color green" onclick="selectBrightnessColor('green')"></div>
                        <div class="brightness-color grey" onclick="selectBrightnessColor('grey')"></div>
                        <div class="brightness-color brown" onclick="selectBrightnessColor('brown')"></div>
                        <div class="brightness-color pink" onclick="selectBrightnessColor('pink')"></div>
                        <div class="brightness-color purple" onclick="selectBrightnessColor('purple')"></div>
                        <div class="brightness-color red" onclick="selectBrightnessColor('red')"></div>
                        <div class="brightness-color blue" onclick="selectBrightnessColor('blue')"></div>
                        <div class="brightness-color yellow" onclick="selectBrightnessColor('yellow')"></div>
                        <div class="brightness-color milk" onclick="selectBrightnessColor('milk')"></div>
                    </div>
                </div>
                <div class="setting-item">
                    <label for="dark-mode-toggle"><span class="emoji">💡</span> <span data-lang="dark-mode-label">Yanayin Gani (Dark Mode):</span></label>
                    <input type="checkbox" id="dark-mode-toggle">
                </div>
                <div class="setting-item">
                    <span class="emoji">🖼️</span> <span data-lang="wallpaper-label">Hoton Bango</span>
                    <button onclick="showWallpaperOptions()" data-lang="change-btn">Canza</button>
                </div>
                <div id="wallpaper-options" class="nested-settings" style="display:none;">
                    <img src="https://i.ibb.co/0RbrwmSk/house-163526-1280.jpg" onclick="setWallpaper('https://i.ibb.co/0RbrwmSk/house-163526-1280.jpg')">
                    <img src="https://i.ibb.co/wrz8dKYH/garden-with-fance-flowers-33070-4129.jpg" onclick="setWallpaper('https://i.ibb.co/wrz8dKYH/garden-with-fance-flowers-33070-4129.jpg')">
                    <img src="https://i.ibb.co/spkrW0mP/cartoon-boys-characters-playing-ball-with-their-dogs-2-R3-YRHG.jpg" onclick="setWallpaper('https://i.ibb.co/spkrW0mP/cartoon-boys-characters-playing-ball-with-their-dogs-2-R3-YRHG.jpg')">
                    <img src="https://i.ibb.co/849CmTRD/makaranta.jpg" onclick="setWallpaper('https://i.ibb.co/849CmTRD/makaranta.jpg')">
                    <img src="https://i.ibb.co/qYhvLJD8/ai-generated-8862065-1280.jpg" onclick="setWallpaper('https://i.ibb.co/qYhvLJD8/ai-generated-8862065-1280.jpg')">
                </div>
            </div>
            
            <div class="setting-item">
                <span class="emoji">🌐</span> <span data-lang="language-label">Harshe</span>
                <button onclick="showPage('language-page')" data-lang="change-btn">Canza</button>
            </div>
            <div class="setting-item">
                <span class="emoji">⏰</span> <span data-lang="daily-reminder-label">Tunatarwa ta yau da kullun</span>
                <button onclick="setDailyReminder()" data-lang="set-reminder-btn">Saita</button>
            </div>
            <div class="setting-item">
                <span class="emoji">🔗</span> <span data-lang="share-link-label">Raba dandalin IHAME</span>
                <button onclick="shareLink()" data-lang="share-btn">Raba</button>
            </div>
            <div class="setting-item">
                <span class="emoji">📜</span> <span data-lang="privacy-policy-label">Dokokin Sirri</span>
                <button onclick="showPrivacyPolicy()" data-lang="view-btn">Duba</button>
            </div>
            <div class="setting-item">
                <span class="emoji">🗑️</span> <span data-lang="delete-account-label">Share Account</span>
                <button onclick="deleteAccount()" data-lang="delete-btn">Share</button>
            </div>
            <button onclick="logout()"><span class="emoji">🚪</span> <span data-lang="logout-btn">Fita</span></button>
        </div>
    </div>

    <!-- Rewards Page -->
    <div id="rewards-page" class="page">
        <header>
            <button class="back-btn" onclick="showPage('dashboard-page')">←</button>
            <h2>Kyauta/Rewards</h2>
        </header>
        <div id="rewards-content">
            <div class="reward-display" id="current-reward">🪨</div>
            <div class="reward-item">
                <div class="reward-icon">🪨</div>
                <div class="reward-info">
                    <div class="reward-title">Stone/Dutse</div>
                    <div class="reward-description">Zango na 1 - Basic Level</div>
                </div>
            </div>
            <div class="reward-item">
                <div class="reward-icon">🛠️</div>
                <div class="reward-info">
                    <div class="reward-title">Iron/Karfe</div>
                    <div class="reward-description">Zango na 2 - Basic Level</div>
                </div>
            </div>
            <div class="reward-item">
                <div class="reward-icon">🔶</div>
                <div class="reward-info">
                    <div class="reward-title">Copper/Tagulla</div>
                    <div class="reward-description">Zango na 1 - Intermediate Level</div>
                </div>
            </div>
            <div class="reward-item">
                <div class="reward-icon">🔷</div>
                <div class="reward-info">
                    <div class="reward-title">Silver/Azurfa</div>
                    <div class="reward-description">Zango na 2 - Intermediate Level</div>
                </div>
            </div>
            <div class="reward-item">
                <div class="reward-icon">⭐</div>
                <div class="reward-info">
                    <div class="reward-title">Gold/Zinare</div>
                    <div class="reward-description">Zango na 1 - Advance Level</div>
                </div>
            </div>
            <div class="reward-item">
                <div class="reward-icon">💎</div>
                <div class="reward-info">
                    <div class="reward-title">Platinum</div>
                    <div class="reward-description">Zango na 2 - Advance Level</div>
                </div>
            </div>
        </div>
        <div style="margin-top: 20px; text-align: left;">
            <p><strong>Sharuɗɗan Samun Kyauta:</strong></p>
            <ul>
                <li>Dole ne ka kasance kana yin fashin rana ko dayaba a zangon</li>
                <li>Za a baka wannan kyautar ne saboda jajircewa da yayi wajen zuwa makaranta akoda yaushe</li>
                <li>Idan dalibi yana fashi kai ka san darajar makin shi</li>
            </ul>
        </div>
    </div>

    <!-- Vocabulary Page -->
    <div id="vocabulary-page" class="page">
        <header>
            <button class="back-btn" onclick="showPage('dashboard-page')">←</button>
            <h2>Vocabulary/Runbun Kalmomi</h2>
        </header>
        <div class="vocabulary-search-container">
            <input type="text" class="vocabulary-search-input" id="vocabulary-search" placeholder="Nemo kalma...">
            <span class="vocabulary-search-icon">🔍</span>
        </div>
        <div id="vocabulary-content">
            <!-- Vocabulary content will be loaded here -->
        </div>
    </div>

    <!-- Library Page -->
    <div id="library-page" class="page">
        <header>
            <button class="back-btn" onclick="showPage('dashboard-page')">←</button>
            <h2>Library/Dallkin Littattafai</h2>
        </header>
        <div id="library-content">
            <!-- Library content will be loaded here -->
        </div>
    </div>

    <!-- Sidebar Menu -->
    <div class="sidebar-menu" id="sidebar-menu">
        <button class="close-menu" onclick="toggleMenu()">×</button>
        
        <div class="menu-item" onclick="showPage('profile-page')">
            <span>👤</span> Profile din dalibi
        </div>
        
        <div class="menu-item" onclick="inviteFriend()">
            <span>❤️</span> Invite Friend/Gayyaci Abokai
        </div>
        
        <div class="menu-item" onclick="showPage('dashboard-page')">
            <span>🏠</span> Home/Babban Bango
        </div>
        
        <div class="menu-item" onclick="showPage('courses-list-page')">
            <span>📚</span> Course/Karatu
        </div>
        
        <div class="collapsible-menu">
            <div class="collapsible-header" onclick="toggleCollapsible('alert-menu')">
                <span>📢</span> Alert/Sako
                <span>▼</span>
            </div>
            <div class="collapsible-content" id="alert-menu">
                <div class="menu-item" onclick="showPage('department-chat-page')">
                    <span>🗨️</span> Group Chat/Dandamalin Hira
                </div>
                <div class="menu-item" onclick="showPage('alert-page')">
                    <span>📬</span> Message/Sako
                </div>
                <div class="menu-item" onclick="showPage('notifications-page')">
                    <span>📢</span> Notification/Sanarwa
                </div>
                <div class="menu-item" onclick="showPage('history-page')">
                    <span>🕒</span> History
                </div>
            </div>
        </div>
        
        <div class="menu-item" onclick="showPage('daily-quiz-page')">
            <span>🧠</span> Exam/Jarabawa
        </div>
        
        <div class="menu-item" onclick="showPage('certificate-page')">
            <span>🧾</span> Certificate/Takardar Shaida
        </div>
        
        <div class="menu-item" onclick="showPage('rewards-page')">
            <span>🏆</span> Kyauta/Rewards
        </div>
        
        <div class="menu-item" onclick="showPage('vocabulary-page')">
            <span>📖</span> Vocabulary/Runbun Kalmomi
        </div>
        
        <div class="menu-item" onclick="showPage('library-page')">
            <span>📚</span> Library/Dallkin Littattafai
        </div>
        
        <div class="menu-item" onclick="showCalculator()">
            <span>🧮</span> Scientific Calculator
        </div>
        
        <div class="menu-item" onclick="showCurrencyConverter()">
            <span>💰</span> Masu Canza Kudi
        </div>
        
        <div class="menu-item" onclick="showMeasurementConverter()">
            <span>📏</span> Masu Auna Ma'auni
        </div>
        
        <div class="collapsible-menu">
            <div class="collapsible-header" onclick="toggleCollapsible('contact-menu')">
                <span>👨‍💼</span> Contact/Tuntuba
                <span>▼</span>
            </div>
            <div class="collapsible-content" id="contact-menu">
                <div class="menu-item" onclick="showPage('help-center-page')">
                    <span>👨‍💼</span> Help Center/Cibiyar Taimako
                </div>
                <div class="menu-item" onclick="reportIssue()">
                    <span>⚠️</span> Report/Kai Kara
                </div>
            </div>
        </div>
        
        <div class="menu-item" onclick="showPage('rules-page')">
            <span>⚖️</span> Rules and Regulation/Tsari
        </div>
        
        <div class="menu-item" onclick="showPage('settings-page')">
            <span>⚙️</span> Settings and Privacy
        </div>
        
        <div class="menu-item" onclick="showPage('calendar-page')">
            <span>📅</span> Kalanda
        </div>
        
        <div class="menu-item" onclick="showPage('notepad-page')">
            <span>📝</span> Notepad
        </div>
        
        <div class="menu-item" onclick="logout()">
            <span>🗝️</span> Log Out/Fita
        </div>
        
        <div class="menu-item" onclick="deleteAccount()">
            <span>🗑️</span> Delete Account/Goge Account
        </div>
    </div>

    <!-- Research Button -->
    <div class="research-menu" onclick="showResearchTools()">
        Bincike/Research 🔍
    </div>

    <!-- Calculator Modal -->
    <div id="calculator-modal">
        <div class="calculator-container">
            <span class="close-calculator" onclick="closeCalculator()">&times;</span>
            <input type="text" id="calculator-display" class="calculator-display" readonly>
            <div class="calculator-buttons">
                <button class="calculator-btn clear" onclick="clearDisplay()">C</button>
                <button class="calculator-btn operator" onclick="appendToDisplay('(')">(</button>
                <button class="calculator-btn operator" onclick="appendToDisplay(')')">)</button>
                <button class="calculator-btn operator" onclick="appendToDisplay('/')">/</button>
                <button class="calculator-btn" onclick="appendToDisplay('7')">7</button>
                <button class="calculator-btn" onclick="appendToDisplay('8')">8</button>
                <button class="calculator-btn" onclick="appendToDisplay('9')">9</button>
                <button class="calculator-btn operator" onclick="appendToDisplay('*')">*</button>
                <button class="calculator-btn" onclick="appendToDisplay('4')">4</button>
                <button class="calculator-btn" onclick="appendToDisplay('5')">5</button>
                <button class="calculator-btn" onclick="appendToDisplay('6')">6</button>
                <button class="calculator-btn operator" onclick="appendToDisplay('-')">-</button>
                <button class="calculator-btn" onclick="appendToDisplay('1')">1</button>
                <button class="calculator-btn" onclick="appendToDisplay('2')">2</button>
                <button class="calculator-btn" onclick="appendToDisplay('3')">3</button>
                <button class="calculator-btn operator" onclick="appendToDisplay('+')">+</button>
                <button class="calculator-btn" onclick="appendToDisplay('0')">0</button>
                <button class="calculator-btn" onclick="appendToDisplay('.')">.</button>
                <button class="calculator-btn operator" onclick="calculateSquareRoot()">√</button>
                <button class="calculator-btn operator" onclick="calculatePower()">^</button>
                <div class="scientific-buttons">
                    <button class="calculator-btn scientific" onclick="calculateSin()">sin</button>
                    <button class="calculator-btn scientific" onclick="calculateCos()">cos</button>
                    <button class="calculator-btn scientific" onclick="calculateTan()">tan</button>
                    <button class="calculator-btn scientific" onclick="calculateLog()">log</button>
                    <button class="calculator-btn scientific" onclick="calculateLn()">ln</button>
                    <button class="calculator-btn scientific" onclick="calculateFactorial()">x!</button>
                    <button class="calculator-btn scientific" onclick="calculatePi()">π</button>
                    <button class="calculator-btn scientific" onclick="calculateE()">e</button>
                    <button class="calculator-btn scientific" onclick="calculatePercentage()">%</button>
                    <button class="calculator-btn scientific" onclick="calculateMod()">mod</button>
                </div>
                <button class="calculator-btn equal" onclick="calculate()">=</button>
            </div>
        </div>
    </div>

    <!-- Currency Converter Modal -->
    <div id="currency-converter-modal" style="display: none; position: fixed; z-index: 1000; left: 0; top: 0; width: 100%; height: 100%; background-color: rgba(0,0,0,0.5); justify-content: center; align-items: center;">
        <div class="converter-container">
            <span class="close-calculator" onclick="closeCurrencyConverter()">&times;</span>
            <h2>Masu Canza Kudi</h2>
            <div class="converter-form">
                <div class="converter-row">
                    <input type="number" id="currency-amount" placeholder="Adadin kuɗi">
                    <select id="from-currency">
                        <option value="NGN">Naira (NGN)</option>
                        <option value="USD">Dollar (USD)</option>
                        <option value="EUR">Euro (EUR)</option>
                        <option value="GBP">Pound (GBP)</option>
                    </select>
                </div>
                <div class="converter-row">
                    <input type="number" id="converted-amount" placeholder="Adadin da aka canza" readonly>
                    <select id="to-currency">
                        <option value="USD">Dollar (USD)</option>
                        <option value="EUR">Euro (EUR)</option>
                        <option value="GBP">Pound (GBP)</option>
                        <option value="NGN">Naira (NGN)</option>
                    </select>
                </div>
                <button onclick="convertCurrency()">Canza</button>
            </div>
        </div>
    </div>

    <!-- Measurement Converter Modal -->
    <div id="measurement-converter-modal" style="display: none; position: fixed; z-index: 1000; left: 0; top: 0; width: 100%; height: 100%; background-color: rgba(0,0,0,0.5); justify-content: center; align-items: center;">
        <div class="measurement-converter">
            <span class="close-calculator" onclick="closeMeasurementConverter()">&times;</span>
            <h2>Masu Auna Ma'auni</h2>
            <div class="measurement-type-selector">
                <button class="measurement-type-btn active" onclick="selectMeasurementType('length')">Tsawo</button>
                <button class="measurement-type-btn" onclick="selectMeasurementType('weight')">Nauyi</button>
                <button class="measurement-type-btn" onclick="selectMeasurementType('temperature')">Zafi</button>
            </div>
            <div id="length-converter" class="converter-form">
                <div class="converter-row">
                    <input type="number" id="length-value" placeholder="Adadin">
                    <select id="from-length">
                        <option value="meter">Mita</option>
                        <option value="centimeter">Santimita</option>
                        <option value="millimeter">Milimita</option>
                        <option value="kilometer">Kilomita</option>
                        <option value="inch">Inci</option>
                        <option value="foot">Fiti</option>
                        <option value="yard">Yadi</option>
                        <option value="mile">Mail</option>
                    </select>
                </div>
                <div class="converter-row">
                    <input type="number" id="converted-length" placeholder="Adadin da aka canza" readonly>
                    <select id="to-length">
                        <option value="centimeter">Santimita</option>
                        <option value="meter">Mita</option>
                        <option value="millimeter">Milimita</option>
                        <option value="kilometer">Kilomita</option>
                        <option value="inch">Inci</option>
                        <option value="foot">Fiti</option>
                        <option value="yard">Yadi</option>
                        <option value="mile">Mail</option>
                    </select>
                </div>
                <button onclick="convertLength()">Canza</button>
            </div>
            <div id="weight-converter" class="converter-form" style="display: none;">
                <div class="converter-row">
                    <input type="number" id="weight-value" placeholder="Adadin">
                    <select id="from-weight">
                        <option value="kilogram">Kilogiram</option>
                        <option value="gram">Giram</option>
                        <option value="milligram">Miligiram</option>
                        <option value="pound">Lab</option>
                        <option value="ounce">Oun</option>
                    </select>
                </div>
                <div class="converter-row">
                    <input type="number" id="converted-weight" placeholder="Adadin da aka canza" readonly>
                    <select id="to-weight">
                        <option value="gram">Giram</option>
                        <option value="kilogram">Kilogiram</option>
                        <option value="milligram">Miligiram</option>
                        <option value="pound">Lab</option>
                        <option value="ounce">Oun</option>
                    </select>
                </div>
                <button onclick="convertWeight()">Canza</button>
            </div>
            <div id="temperature-converter" class="converter-form" style="display: none;">
                <div class="converter-row">
                    <input type="number" id="temperature-value" placeholder="Adadin">
                    <select id="from-temperature">
                        <option value="celsius">Celsius</option>
                        <option value="fahrenheit">Fahrenheit</option>
                        <option value="kelvin">Kelvin</option>
                    </select>
                </div>
                <div class="converter-row">
                    <input type="number" id="converted-temperature" placeholder="Adadin da aka canza" readonly>
                    <select id="to-temperature">
                        <option value="fahrenheit">Fahrenheit</option>
                        <option value="celsius">Celsius</option>
                        <option value="kelvin">Kelvin</option>
                    </select>
                </div>
                <button onclick="convertTemperature()">Canza</button>
            </div>
        </div>
    </div>

    <script>
        // JavaScript code for the complete platform
        // This includes all functionality for the IHAME University platform

        // Global variables
        let currentUser = null;
        let currentLang = 'ha';
        let allUsers = JSON.parse(localStorage.getItem('allUsers')) || [];
        let pendingRegistrations = JSON.parse(localStorage.getItem('pendingRegistrations')) || [];
        let notifications = JSON.parse(localStorage.getItem('notifications')) || {};
        let userActivity = JSON.parse(localStorage.getItem('userActivity')) || {};
        let departmentQuizzes = JSON.parse(localStorage.getItem('departmentQuizzes')) || {};
        let departmentChats = JSON.parse(localStorage.getItem('departmentChats')) || {};
        let adminHistory = JSON.parse(localStorage.getItem('adminHistory')) || {};
        let paymentReferences = JSON.parse(localStorage.getItem('paymentReferences')) || {};
        let selectedLevel = '';
        let selectedSemester = '';
        let currentModuleIndex = 0;
        let currentChatMessages = [];
        let aiChatHistory = [];
        let currentCalendarMonth = new Date().getMonth();
        let currentCalendarYear = new Date().getFullYear();
        let currentAITopic = '';
        let currentAILevel = '';
        let currentAISemester = '';
        let userDeviceId = localStorage.getItem('userDeviceId') || generateDeviceId();
        let freeTierTimer = null;
        let freeTierTimeLeft = 168 * 60 * 60; // 168 hours in seconds
        let aiTeacherLanguage = 'ha';
        let speechSynthesis = window.speechSynthesis;
        let currentSpeech = null;
        let tokensResetTimer = null;

        // Tokens System
        const TOKENS_FREE_TIER = 800;
        const TOKENS_STANDARD_TIER = 2000;
        const LESSONS_PER_DAY = 1; // Darasi ɗaya a rana don duka tiers
        const AI_COST_PER_TOPIC = 100; // Tokens da ake cinyewa don kowane topic
        const QUIZ_COST_PER_QUESTION = 50; // Tokens da ake cinyewa don kowane tambaya

        const MODULES_BASIC = 12;
        const MODULES_INTERMEDIATE = 14;
        const MODULES_ADVANCE = 14;
        const TOTAL_MODULES = 40;
        const PAYMENT_AMOUNT = 500;
        const SESSION_EXPIRY_DAYS = 30;

        // Faculty Pricing Structure
        const facultyPricing = {
            'Science': 3000,
            'Technology': 2500,
            'Business': 2500,
            'Government': 2500,
            'Arts': 2000,
            'Skills': 1700,
            'Linguistic': 1500,
            'Religion': 1000
        };

        // Admin credentials with specific roles
        const ADMIN_CREDENTIALS = {
            'abduldocter1@gmail.com': { 
                password: 'Docter1#',
                role: 'super_admin',
                permissions: ['all']
            },
            'drmuslaf@gmail.com': { 
                password: 'Docter1@',
                role: 'registrar',
                permissions: ['approve_registrations', 'view_students', 'verify_certificates']
            },
            'angonbushra1@gmail.com': { 
                password: 'Docter1&',
                role: 'monitor',
                permissions: ['view_chats', 'send_messages', 'monitor_groups']
            },
            'doctorate@gmail.com': { 
                password: 'Docter1:',
                role: 'teacher',
                permissions: ['manage_modules', 'create_quizzes', 'grade_students']
            },
            'sheikh001@gmail.com': { 
                password: 'Docter1?',
                role: 'exam_manager',
                permissions: ['create_exams', 'manage_quizzes', 'view_results']
            },
            'hibbaty001@gmail.com': { 
                password: 'Docter1$',
                role: 'librarian',
                permissions: ['manage_library', 'upload_documents', 'categorize_resources']
            }
        };

        // Prevent registration with admin emails
        const ADMIN_EMAILS = Object.keys(ADMIN_CREDENTIALS);

        const departmentsShortcuts = {
            'Medicine and Surgery (MBBS)': 'MBB', 'Nursing Science': 'NUR', 'Pharmacy': 'PHA', 'Medical Laboratory Science': 'MLS',
            'Radiography / Medical Imaging': 'RAD', 'Physiotherapy': 'PHY', 'Dentistry': 'DEN', 'Public Health': 'PUH',
            'Nutrition and Dietetics': 'NUT', 'Anatomy': 'ANA', 'Physiology': 'PHY', 'Biochemistry': 'BIO', 'Health Information Management': 'HIM',
            'Environmental Health Science': 'EHS', 'Optometry': 'OPT', 'Community Health / Primary Health Care': 'CHC', 'Veterinary Medicine': 'VET',
            'Electrical/Electronic Technology': 'EET', 'Mechanical/Production Technology': 'MPT', 'Building Technology': 'BLD',
            'Civil Technology': 'CIV', 'Computer Science / Information Technology': 'CSI', 'Industrial Technology': 'IND',
            'Automobile Technology': 'AUT', 'Welding and Fabrication Technology': 'WFT', 'Renewable Energy Technology': 'RET',
            'Telecommunication Technology': 'TEL', 'Cybersecurity': 'CYS', 'Information Technology': 'IT', 'Artificial Intelligence': 'AIT',
            'Software Engineering': 'SOE', 'Data Science & Analysis': 'DSA', 'Machine Learning': 'MAL', 'Web Development': 'WEB',
            'Business Administration': 'BUS', 'Entrepreneurship & Innovation': 'ENT', 'Finance & Investment': 'FIN', 'Accounting': 'ACC',
            'Marketing (Digital Marketing)': 'MKT', 'Economics': 'ECO', 'E-commerce & Dropshipping': 'ECOM', 'Project Management': 'PJM',
            'Law / Shari\'a': 'LAW', 'Political Science / International Relations': 'POL', 'Psychology': 'PSY', 'Sociology / Social Work': 'SOC',
            'Linguistics / Translation': 'LIN', 'Mass Communication / Journalism': 'MAC', 'Education / Teaching / Curriculum Development': 'EDU',
            'Graphic Design / UI-UX Design': 'GDS', 'Video Production / Film & Media': 'VPM', 'Animation / Game Design': 'AGD',
            'Photography & Editing': 'PHE', 'Music Production / Sound Engineering': 'MPSE',
            // Linguistic Faculty Departments
            'Hausa': 'HSA', 'Fulani': 'FUL', 'Yoruba': 'YOR', 'Igbo': 'IGB', 'English': 'ENG', 'French': 'FRE', 'Arabic': 'ARA',
            'Kanuri': 'KAN', 'Gwari': 'GWA',
            // Religion Faculty Departments
            'Islam': 'ISL', 'Christianity': 'CHR', 'Judaism': 'JUD', 'Hinduism': 'HIN', 'Buddhism': 'BUD', 'Traditional African Religions': 'TAR',
            'Sikhism': 'SIK', 'Baháʼí Faith': 'BAH', 'Jainism': 'JAI', 'Shinto': 'SHI', 'Taoism': 'TAO', 'Zoroastrianism': 'ZOR'
        };

        const facultiesData = {
            'Science': { name: 'Faculty of Science (Kimiya)', departments: [
                { id: '1', title: 'Medicine and Surgery (MBBS)' }, { id: '2', title: 'Nursing Science' }, { id: '3', title: 'Pharmacy' },
                { id: '4', title: 'Medical Laboratory Science' }, { id: '5', title: 'Radiography / Medical Imaging' }, { id: '6', title: 'Physiotherapy' },
                { id: '7', title: 'Dentistry' }, { id: '8', title: 'Public Health' }, { id: '9', title: 'Nutrition and Dietetics' },
                { id: '10', title: 'Anatomy' }, { id: '11', title: 'Physiology' }, { id: '12', title: 'Biochemistry' },
                { id: '13', title: 'Health Information Management' }, { id: '14', title: 'Environmental Health Science' },
                { id: '15', title: 'Optometry' }, { id: '16', title: 'Community Health / Primary Health Care' }, { id: '17', title: 'Veterinary Medicine' }]
            },
            'Technology': { name: 'Faculty of Technology (Fasaha)', departments: [
                { id: '18', title: 'Electrical/Electronic Technology' }, { id: '19', title: 'Mechanical/Production Technology' }, { id: '20', title: 'Building Technology' },
                { id: '21', title: 'Civil Technology' }, { id: '22', title: 'Computer Science / Information Technology' }, { id: '23', title: 'Industrial Technology' },
                { id: '24', title: 'Automobile Technology' }, { id: '25', title: 'Welding and Fabrication Technology' }, { id: '26', title: 'Renewable Energy Technology' },
                { id: '27', title: 'Telecommunication Technology' }, { id: '48', title: 'Cybersecurity' }, { id: '49', title: 'Information Technology' },
                { id: '50', title: 'Artificial Intelligence' }, { id: '51', title: 'Software Engineering' }, { id: '52', title: 'Data Science & Analysis' },
                { id: '53', title: 'Machine Learning' }, { id: '54', title: 'Web Development' }]
            },
            'Business': { name: 'Faculty of Business (Kasuwanci)', departments: [
                { id: '28', title: 'Business Administration' }, { id: '29', title: 'Entrepreneurship & Innovation' }, { id: '30', title: 'Finance & Investment' },
                { id: '31', title: 'Accounting' }, { id: '32', title: 'Marketing (Digital Marketing)' }, { id: '33', title: 'Economics' },
                { id: '34', title: 'E-commerce & Dropshipping' }, { id: '35', title: 'Project Management' }]
            },
            'Government': { name: 'Faculty of Government (Gomnati)', departments: [
                { id: '36', title: 'Law / Shari\'a' }, { id: '37', title: 'Political Science / International Relations' }, { id: '38', title: 'Psychology' },
                { id: '39', title: 'Sociology / Social Work' }, { id: '40', title: 'Linguistics / Translation' }, { id: '41', title: 'Mass Communication / Journalism' },
                { id: '42', title: 'Education / Teaching / Curriculum Development' }]
            },
            'Arts': { name: 'Faculty of Arts (Arts)', departments: [
                { id: '43', title: 'Graphic Design / UI-UX Design' }, { id: '44', title: 'Video Production / Film & Media' }, { id: '45', title: 'Animation / Game Design' },
                { id: '46', title: 'Photography & Editing' }, { id: '47', title: 'Music Production / Sound Engineering' }]
            },
            'Skills': { name: 'Faculty of Special Skills (Sana\'o\'i)', departments: [
                { id: '55', title: 'Graphic Design / UI-UX Design' }, { id: '56', title: 'Video Production / Film & Media' }, { id: '57', title: 'Animation / Game Design' },
                { id: '58', title: 'Photography & Editing' }, { id: '59', title: 'Music Production / Sound Engineering' }]
            },
            'Linguistic': { name: 'Faculty of Linguistic (Harsuna)', departments: [
                { id: '60', title: 'Hausa' }, { id: '61', title: 'Fulani' }, { id: '62', title: 'Yoruba' }, 
                { id: '63', title: 'Igbo' }, { id: '64', title: 'English' }, { id: '65', title: 'French' }, 
                { id: '66', title: 'Arabic' }, { id: '67', title: 'Kanuri' }, { id: '68', title: 'Gwari' }]
            },
            'Religion': { name: 'Faculty of Religion (Addinai)', departments: [
                { id: '69', title: 'Islam' }, { id: '70', title: 'Christianity' }, { id: '71', title: 'Judaism' },
                { id: '72', title: 'Hinduism' }, { id: '73', title: 'Buddhism' }, { id: '74', title: 'Traditional African Religions' },
                { id: '75', title: 'Sikhism' }, { id: '76', title: 'Baháʼí Faith' }, { id: '77', title: 'Jainism' },
                { id: '78', title: 'Shinto' }, { id: '79', title: 'Taoism' }, { id: '80', title: 'Zoroastrianism' }]
            }
        };

        // Department Topics Structure - EXPANDED TO 50 TOPICS
        const departmentTopics = {
            'Hausa': {
                'basic': [
                    "1. Ma'anar Harshe da Tarihin Hausa",
                    "2. Asalin Harshen Hausa da Yankunan da ake amfani da shi", 
                    "3. Haruffan Hausa da yadda ake furta su",
                    "4. Harshe da Lafazi (Sauti da Dabarun Furuci)",
                    "5. Kalmar Hausa da Rukunan Kalmomi",
                    "6. Siffofin Kalmomi – Gajeru da Dogaye",
                    "7. Suna: Ma'ana, Nau'i da Amfani",
                    "8. Aiki (Verbs): Ma'ana da Nau'o'insu",
                    "9. Zance (Sentences): Ginin Jumla a Hausa",
                    "10. Hanyoyin Gaisuwa da Maganganun Yabo",
                    "11. Tambaya da Amsa a Hausa",
                    "12. Karin Magana – Ma'anarsu da Amfaninsu",
                    "13. Tsarin Rubutu: Haruffa da Alamu",
                    "14. Harshe da Al'adu: Gaisuwa da Rabe-rabe",
                    "15. Kalmomin Gida da Na Waje",
                    "16. Harshen Iyali da Na Jama'a",
                    "17. Rubutun Wasika da Hira",
                    "18. Harshen Kasuwanci da Siyasa",
                    "19. Kalmomin Zamani da Na Gargajiya",
                    "20. Harshe da Addini: Kalmomin Musulunci",
                    "21. Harshe da Kimiyya: Kalmomin Ilimi",
                    "22. Harshe da Fasaha: Kalmomin Zamani",
                    "23. Harshen Noma da Dabbobi",
                    "24. Harshen Kiwon Lafiya da Magunguna",
                    "25. Harshen Sufanci da Hikima"
                ],
                'intermediate': [
                    "26. Nahawun Hausa: Ginin Jumla",
                    "27. Jimloli Masu Wakiltar Mutum (Pronominal Sentences)",
                    "28. Amfani da Haruffan Haɗi (Conjunctions)",
                    "29. Tsarin Rubutu: Labari da Wasika", 
                    "30. Salon Magana da Karin Lafazi",
                    "31. Amfani da Kalmomi Bisa Yanayi (Contextual Usage)",
                    "32. Kalmar Aiki da Lokaci (Tense in Hausa)",
                    "33. Siffar Kalmomi (Adjectives da Adverbs)",
                    "34. Harshe da Al'adu: Hanyoyin Magana a Yammaci da Arewa",
                    "35. Salon Hausawa a Koyarwa da Kariya",
                    "36. Dabarun Karatu da Fahimta (Comprehension)",
                    "37. Fassarar Kalma zuwa Kalma (Literal Translation)",
                    "38. Fassarar Ma'ana (Contextual Translation)",
                    "39. Rubutun Hikaya da Gajerun Labarai",
                    "40. Harshen Waƙa da Rubutun Waƙoƙi",
                    "41. Harshen Jarida da Labarai",
                    "42. Harshen Rediyo da Talabijin",
                    "43. Harshen Kasuwanci da Talla",
                    "44. Harshen Siyasa da Jama'a",
                    "45. Harshen Ilimi da Koyarwa",
                    "46. Harshen Shari'a da Doka",
                    "47. Harshen Kiwon Lafiya da Magani",
                    "48. Harshen Aikin Gona da Noma",
                    "49. Harshen Sufanci da Tasawwufi",
                    "50. Harshen Zamani da Fasaha"
                ],
                'advance': [
                    "51. Balagar Hausa: Tsarin Magana Mai Dacewa (Ma'ani, Bayan & Badi')",
                    "52. Salon Rubutu: Waƙa da Wasan Kwaikwayo",
                    "53. Nazarin Adabin Gargajiya",
                    "54. Nazarin Adabin Zamani (Littattafan Hausa)",
                    "55. Salon Zance da Tsarinsa (Speech Art & Oratory)", 
                    "56. Harshe da Siyasa (Political Discourse in Hausa)",
                    "57. Harshe da Addini (Hausa Islamic Literature)",
                    "58. Amfani da Hausar Kasuwanci da Fasaha",
                    "59. Harshe da Fasahar Zamani (Digital Hausa)",
                    "60. Nazarin Karin Magana da Hikima",
                    "61. Harshe da Haɗin Al'umma (Sociolinguistics of Hausa)",
                    "62. Fassarar Rubuce-Rubucen Kimiyya da Addini",
                    "63. Rubutun Bincike da Ƙididdiga (Research Writing)",
                    "64. Kammalawa: Nazarin Gabaɗaya da Ayyukan Aiki (Final Project)",
                    "65. Harshen Gudanarwa da Gudanar da Ayyuka",
                    "66. Harshen Tattalin Arziki da Kuɗi",
                    "67. Harshen Fasaha da Injiniya",
                    "68. Harshen Ilimin Duniya da Harkokin Ƙasashen Duniya",
                    "69. Harshen Ilimin Halitta da Muhalli",
                    "70. Harshen Ilimin Tarihi da Al'adu",
                    "71. Harshen Ilimin Zamani da Ci Gaba",
                    "72. Harshen Ilimin Zamani da Duniya",
                    "73. Harshen Ilimin Zamani da Al'umma",
                    "74. Harshen Ilimin Zamani da Siyasa",
                    "75. Harshen Ilimin Zamani da Tattalin Arziki"
                ]
            }
        };

        // Vocabulary Data
        const vocabularyData = {
            'A': [
                { word: 'Aiki', meaning: 'Work/Labor', example: 'Yana aiki a banki.', explanation: 'Aiki yana nufin ayyukan da mutum ke yi don samun kuɗi.' },
                { word: 'Abinci', meaning: 'Food', example: 'Abincin yau da daddawa ne.', explanation: 'Abinci shine abubuwan da mutum ke ci don rayuwa.' },
                { word: 'Aure', meaning: 'Marriage', example: 'Auren su ya yi shekara biyu.', explanation: 'Aure shine haɗuwar namiji da mace bisa doka da al\'ada.' }
            ],
            'B': [
                { word: 'Baki', meaning: 'Guest/Stranger', example: 'Muna da baki a gida.', explanation: 'Baki shine mutumin da ba na gida ba.' },
                { word: 'Bara', meaning: 'Last year', example: 'Bara na yi tafiya Kano.', explanation: 'Bara yana nufin shekarar da ta gabata.' },
                { word: 'Bayan', meaning: 'After/Behind', example: 'Zan zo bayan lokaci.', explanation: 'Bayan yana nufin lokacin da ya wuce ko wurin da yake baya.' }
            ]
        };

        // Library Data
        const libraryData = [
            {
                id: 1,
                title: "Nazarin Hausa - Mataki na Farko",
                description: "Littafin nazarin harshen Hausa na mataki na farko",
                fileType: "pdf",
                uploadDate: "2024-01-15",
                department: "Hausa",
                level: "basic"
            },
            {
                id: 2, 
                title: "Fulatanci for Beginners",
                description: "Littafin koyon Fulatanci na masu farawa",
                fileType: "pdf",
                uploadDate: "2024-01-10",
                department: "Fulani",
                level: "basic"
            }
        ];

        const translations = {
            ha: {
                'welcome-title': 'Barka da zuwa JAMI\'AR IHAME', 'ihame-meaning': '(Ingantacciyar Hausa A Maimakon Englishi)',
                'welcome-text': 'Wannan itace Dandamali na farko Dake koyar da ilimummuka na zamani masu zurfin da Hausa bayan kammala karatu sai aba dalibi takardar kammala karatu.',
                'register-btn': 'Shiga yin Register', 'login-prompt': 'Tuni kana da asusu? <a href="#" onclick="showPage(\'login-page\')">Shiga</a>',
                'login-title': 'Shiga Asusu', 'login-btn': 'Shiga', 'register-prompt': 'Baka da asusu? <a href="#" onclick="showPage(\'register-page\')">Yi Rajista</a>',
                'register-title': 'Barka da zuwa JAMI\'AR IHAME', 'register-subtitle': 'Yi Rajista don fara karatu', 'select-faculty': 'Zaɓi Faculty',
                'select-dept': 'Zaɓi Department', 'selected-course-title': 'Darasi da ka zaɓa', 'progress-text': 'An kammala: 0%', 'courses-list-btn': 'Darussa',
                'start-learning-btn': 'Fara Karatu', 'certificate-btn': 'Shaidar Kammalawa', 'help-center-text': 'Help Center', 'profile-title': 'Bayanan ka',
                'profile-regno-label': 'Reg. No:', 'profile-name-label': 'Suna:', 'profile-email-label': 'Email:', 'profile-faculty-label': 'Faculty:',
                'profile-department-label': 'Department:', 'profile-level-label': 'Level:', 'all-courses-title': 'Dukkan Darussa',
                'modules-page-title': 'Modules na Darasi', 'prev-btn': 'Baya', 'next-btn': 'Gaba', 'certificate-title': 'Shaidar Kammalawa',
                'congrats-message': 'Taya murna!', 'certificate-payment-text': 'Ka kammala dukkan modules na darasin ka.', 'download-text': 'Ka cancanci sauke shaidar kammalawar ka.',
                'download-btn': 'Sauke Certificate', 'settings-title': 'Saituna', 'dark-mode-label': 'Yanayin Gani (Dark Mode):', 'language-label': 'Harshe',
                'input-name': 'Cikakken Sunan ka', 'input-email': 'Saka Email', 'input-password': 'Kalmar sirri',
                'daily-reminder-label': 'Tunatarwa ta yau da kullun', 'set-reminder-btn': 'Saita', 'share-link-label': 'Raba dandalin IHAME', 'share-btn': 'Raba',
                'privacy-policy-label': 'Dokokin Sirri', 'view-btn': 'Duba', 'delete-account-label': 'Share Account', 'delete-btn': 'Share',
                'logout-btn': 'Fita', 'distinction': 'Distinction', 'upper-credit': 'Upper Credit', 'lower-credit': 'Lower Credit', 'pass': 'An ci jarrabawa',
                'fail': 'An kasa', 'display-title': 'Display', 'font-size-label': 'Girman Rubutu:', 'font-style-label': 'Nau\'in Rubutu:',
                'brightness-level-label': 'Hasken Allo:', 'wallpaper-label': 'Hoton Bango', 'change-btn': 'Canza', 'daily-quiz-title': 'Jarabawa na Kullum',
                'daily-quiz-btn': 'Jarabawa na Kullum', 'percentage-label': 'Kashi:', 'completed-modules-label': 'Modules da aka kammala:',
                'remember-me': 'Tuna ni a wannan na\'ura', 'admin-login-prompt': 'Shiga a matsayin Admin', 'admin-login-title': 'Admin Login',
                'admin-title': 'Admin Dashboard', 'student-list-title': 'Jerin Dalibai', 'table-header-name': 'Suna', 'table-header-regno': 'Lambar Rajista',
                'table-header-action': 'Aiki', 'view-details-btn': 'Duba Bayanai', 'student-details-title': 'Bayanan Dalibi',
                'quiz-already-taken': 'Ka riga ka yi jarabawar yau. Ka dawo gobe.', 'input-regno': 'Lambar Rajista (Reg. No.)',
                'edit-profile-btn': 'Gyara Bayanai', 'save-profile-btn': 'Ajiye Canje-Canje', 'download-text-certificate': 'Lambar rajistarka ta kare bayan an sauke takardar. Da fatan za a sake yin rajista don ci gaba da karatu.',
                'payment-info': 'Bayan rajista, za a ba ku cikakkun bayanan biyan kuɗi domin samun lambar rajista.', 'approve-payment': 'Amince Biya',
                'reject-payment': 'Ƙi Biya', 'whatsapp-btn': 'Samun Lambar register', 'delete-student-btn': 'Share Dalibi', 'certificate-status': 'Hali:',
                'continue-btn': 'Ci gaba', 'save-modules-btn': 'Ajiye zaɓin'
            },
            en: {
                'welcome-title': 'Welcome to JAMI\'AR IHAME', 'ihame-meaning': '(Improved Hausa Instead of English)',
                'welcome-text': 'This is the first platform that teaches modern sciences deeply in Hausa and issues certificates upon completion.',
                'register-btn': 'Register', 'login-prompt': 'Already have an account? <a href="#" onclick="showPage(\'login-page\')">Login</a>',
                'login-title': 'Login', 'login-btn': 'Login', 'register-prompt': 'Don\'t have an account? <a href="#" onclick="showPage(\'register-page\')">Register</a>',
                'register-title': 'Welcome to JAMI\'AR IHAME', 'register-subtitle': 'Register to start learning', 'select-faculty': 'Select Faculty',
                'select-dept': 'Select Department', 'selected-course-title': 'Selected Course', 'progress-text': 'Completed: 0%', 'courses-list-btn': 'Courses',
                'start-learning-btn': 'Start Learning', 'certificate-btn': 'Completion Certificate', 'help-center-text': 'Help Center',
                'profile-title': 'Your Profile', 'profile-regno-label': 'Reg. No:', 'profile-name-label': 'Name:', 'profile-email-label': 'Email:',
                'profile-faculty-label': 'Faculty:', 'profile-department-label': 'Department:', 'profile-level-label': 'Level:', 'all-courses-title': 'All Courses',
                'modules-page-title': 'Course Modules', 'prev-btn': 'Previous', 'next-btn': 'Next', 'certificate-title': 'Completion Certificate',
                'congrats-message': 'Congratulations!', 'certificate-payment-text': 'You have completed all modules.', 'download-text': 'You are eligible to download your certificate.',
                'download-btn': 'Download Certificate', 'settings-title': 'Settings', 'dark-mode-label': 'Dark Mode:', 'language-label': 'Language',
                'input-name': 'Enter Your Full Name', 'input-email': 'Enter Email', 'input-password': 'Enter Password',
                'daily-reminder-label': 'Daily Reminder', 'set-reminder-btn': 'Set', 'share-link-label': 'Share IHAME Platform', 'share-btn': 'Share',
                'privacy-policy-label': 'Privacy Policy', 'view-btn': 'View', 'delete-account-label': 'Delete Account', 'delete-btn': 'Delete',
                'logout-btn': 'Logout', 'distinction': 'Distinction', 'upper-credit': 'Upper Credit', 'lower-credit': 'Lower Credit', 'pass': 'Passed',
                'fail': 'Failed', 'display-title': 'Display', 'font-size-label': 'Font Size:', 'font-style-label': 'Font Style:',
                'brightness-level-label': 'Brightness Level:', 'wallpaper-label': 'Wallpaper', 'change-btn': 'Change', 'daily-quiz-title': 'Daily Quiz',
                'daily-quiz-btn': 'Daily Quiz', 'percentage-label': 'Percentage:', 'completed-modules-label': 'Completed Modules:',
                'remember-me': 'Remember me on this device', 'admin-login-prompt': 'Login as Admin', 'admin-login-title': 'Admin Login',
                'admin-title': 'Admin Dashboard', 'student-list-title': 'Student List', 'table-header-name': 'Name', 'table-header-regno': 'Reg. No.',
                'table-header-action': 'Action', 'view-details-btn': 'View Details', 'student-details-title': 'Student Details',
                'quiz-already-taken': 'You have already taken the daily quiz. Come back tomorrow.', 'input-regno': 'Registration Number (Reg. No.)',
                'edit-profile-btn': 'Edit Profile', 'save-profile-btn': 'Save Changes', 'download-text-certificate': 'Your registration number has expired upon certificate download. Please re-register to continue your studies.',
                'payment-info': 'After registration, you will receive payment details to get your registration number.', 'approve-payment': 'Approve Payment',
                'reject-payment': 'Reject Payment', 'whatsapp-btn': 'Get Registration Number', 'delete-student-btn': 'Delete Student', 'certificate-status': 'Status:',
                'continue-btn': 'Continue', 'save-modules-btn': 'Save Selection'
            }
        };

        const dailyQuizzes = [
            { question: "Wani yare ne ake amfani dashi a Najeriya?", options: ["Yoruba", "Igbo", "Hausa", "Dukansu"], answer: "Dukansu" },
            { question: "Menene babban birnin jihar Kaduna?", options: ["Kaduna", "Kano", "Abuja", "Lagos"], answer: "Kaduna" },
            { question: "Wane ne ya rubuta 'Tafiya Mabudin Ilmi'?", options: ["Usman Dan Fodio", 'Sir Ahmadu Bello', "Abubakar Imam", "Aminu Kano"], answer: "Abubakar Imam" }
        ];

        // Page Navigation System
        const pages = document.querySelectorAll('.page');
        
        function showPage(pageId) {
            pages.forEach(page => page.classList.remove('active'));
            document.getElementById(pageId).classList.add('active');
            
            const menuBtn = document.querySelector('.menu-btn');
            menuBtn.style.display = (pageId === 'dashboard-page') ? 'block' : 'none';
            
            // Page-specific initialization
            if (pageId === 'dashboard-page' && currentUser) updateDashboard();
            if (pageId === 'admin-page' && currentUser && currentUser.role === 'admin') loadAdminDashboard();
            if (pageId === 'profile-page' && currentUser) displayProfile();
            if (pageId === 'courses-list-page') loadCoursesList();
            if (pageId === 'modules-page' && currentUser) loadModules();
            if (pageId === 'notifications-page' && currentUser) loadNotifications();
            if (pageId === 'module-management-page' && currentUser && currentUser.role === 'admin') loadModuleManagement();
            if (pageId === 'certificate-page' && currentUser) loadCertificate();
            if (pageId === 'certificate-public-page') initializeCertificatePublicView();
            if (pageId === 'department-chat-page') loadDepartmentChatOptions();
            if (pageId === 'rewards-page') loadRewards();
            if (pageId === 'vocabulary-page') loadVocabulary();
            if (pageId === 'library-page') loadLibrary();
            if (pageId === 'public-reading-page') initializePublicReading();
            if (pageId === 'alert-page') initializeAlertTabs();
            if (pageId === 'settings-page') initializeSettingsDisplay();
            if (pageId === 'font-settings-page') initializeFontSettings();
            if (pageId === 'dark-mode-settings-page') initializeDarkModeSettings();
            if (pageId === 'ai-teacher-page') initializeAITeacher();
            if (pageId === 'calendar-page') loadCalendar();
            if (pageId === 'notepad-page') loadNotepad();
            if (pageId === 'admin-alumni-page') loadAlumni();
            if (pageId === 'history-page') loadHistory();
        }

        // Menu System
        function toggleMenu() {
            document.getElementById('sidebar-menu').classList.toggle('active');
        }
        
        function toggleCollapsible(menuId) {
            const content = document.getElementById(menuId);
            content.classList.toggle('active');
        }

        // User Management Functions
        function populateFaculties() {
            const facultySelect = document.getElementById('reg-faculty');
            facultySelect.innerHTML = '<option value="">Faculty</option>';
            for (const faculty in facultiesData) {
                const option = document.createElement('option');
                option.value = faculty;
                option.textContent = facultiesData[faculty].name;
                facultySelect.appendChild(option);
            }
        }

        function populateDepartments() {
            const faculty = document.getElementById('reg-faculty').value;
            const deptSelect = document.getElementById('reg-department');
            deptSelect.innerHTML = '<option value="">Zaɓi Department</option>';
            if (faculty) {
                deptSelect.disabled = false;
                facultiesData[faculty].departments.forEach(dept => {
                    const option = document.createElement('option');
                    option.value = dept.title;
                    option.textContent = dept.title;
                    deptSelect.appendChild(option);
                });
                
                // Update faculty price
                updateFacultyPrice(faculty);
            } else {
                deptSelect.disabled = true;
            }
        }

        function updateFacultyPrice(faculty) {
            const price = facultyPricing[faculty] || 0;
            document.getElementById('faculty-price').textContent = `₦${price}`;
        }

        function selectPaymentTier(tier) {
            const freeBtn = document.getElementById('free-tier-btn');
            const paidBtn = document.getElementById('paid-tier-btn');
            const freeSchedule = document.getElementById('free-study-schedule');
            const paidSchedule = document.getElementById('paid-study-schedule');
            const bankingInfo = document.getElementById('banking-info');
            
            if (tier === 'free') {
                freeBtn.classList.add('active');
                paidBtn.classList.remove('active');
                freeSchedule.style.display = 'block';
                paidSchedule.style.display = 'none';
                bankingInfo.style.display = 'none';
            } else {
                freeBtn.classList.remove('active');
                paidBtn.classList.add('active');
                freeSchedule.style.display = 'none';
                paidSchedule.style.display = 'block';
                bankingInfo.style.display = 'block';
                
                // Update faculty price display
                const faculty = document.getElementById('reg-faculty').value;
                if (faculty) {
                    updateFacultyPrice(faculty);
                }
            }
        }

        function registerUser() {
            const name = document.getElementById('reg-name').value;
            const birthYear = document.getElementById('reg-birth-year').value;
            const photo = document.getElementById('reg-photo').files[0];
            const email = document.getElementById('reg-email').value;
            const password = document.getElementById('reg-password').value;
            const phone = document.getElementById('reg-phone').value;
            const previousEducation = document.getElementById('reg-previous-education').value;
            const educationLevel = document.getElementById('reg-education-level').value;
            const faculty = document.getElementById('reg-faculty').value;
            const departmentTitle = document.getElementById('reg-department').value;
            const level = document.getElementById('reg-level').value;
            
            // Determine payment tier
            const isFreeTier = document.getElementById('free-tier-btn').classList.contains('active');
            const studyTime = isFreeTier ? document.getElementById('reg-study-time-free').value : document.getElementById('reg-study-time-paid').value;
            
            let studyDays = [];
            if (isFreeTier) {
                studyDays = Array.from(document.querySelectorAll('#study-days-container-free input[type="checkbox"]:checked')).map(checkbox => checkbox.value);
                if (studyDays.length !== 4) {
                    alert('Da fatan za a zaɓi daidai ranaku 4 don karatun wucin gadi.');
                    return;
                }
            } else {
                studyDays = Array.from(document.querySelectorAll('#study-days-container-paid input[type="checkbox"]:checked')).map(checkbox => checkbox.value);
            }

            // Check if email is an admin email
            if (ADMIN_EMAILS.includes(email)) {
                alert('Ba za a iya yin rajista da email na admin ba. Da fatan za a yi amfani da wani email.');
                return;
            }

            // Check for duplicate registration
            const existingUser = allUsers.find(u => u.email === email || u.phone === phone);
            if (existingUser) {
                alert('An riga an yi rajista da wannan email ko lambar waya.');
                return;
            }

            if (!name || !birthYear || !photo || !email || !password || !phone || !previousEducation || !educationLevel || !faculty || !departmentTitle || !level || !studyTime || studyDays.length === 0) {
                alert('Da fatan za a cika dukkan filaye masu muhimmanci.');
                return;
            }

            const departmentCode = departmentsShortcuts[departmentTitle];
            if (!departmentCode) {
                alert('An zaɓi wani sashe mara inganci. Da fatan za a sake zaɓa.');
                return;
            }

            const pendingRegistration = { 
                name, 
                birthYear, 
                photo: URL.createObjectURL(photo), 
                email, 
                password, 
                phone, 
                previousEducation,
                educationLevel,
                faculty, 
                departmentTitle, 
                departmentCode, 
                level, 
                studyTime, 
                studyDays, 
                date: new Date().toLocaleString(),
                deviceId: userDeviceId,
                paymentTier: isFreeTier ? 'free' : 'paid',
                paymentStatus: isFreeTier ? 'approved' : 'pending'
            };
            pendingRegistrations.push(pendingRegistration);
            localStorage.setItem('pendingRegistrations', JSON.stringify(pendingRegistrations));
            
            if (isFreeTier) {
                alert('An yi rajista cikin nasara! Za ka iya fara karatu nan take.');
                showPage('login-page');
            } else {
                alert('An yi rajista cikin nasara! Da fatan za a biya kuɗin karatu domin samun lambar rajista.');
            }
        }

        function selectLoginType(type) {
            const studentBtn = document.getElementById('student-login-btn');
            const adminBtn = document.getElementById('admin-login-btn');
            const studentForm = document.getElementById('student-login-form');
            const adminForm = document.getElementById('admin-login-form');
            
            if (type === 'student') {
                studentBtn.classList.add('active');
                adminBtn.classList.remove('active');
                studentForm.style.display = 'block';
                adminForm.style.display = 'none';
            } else {
                studentBtn.classList.remove('active');
                adminBtn.classList.add('active');
                studentForm.style.display = 'none';
                adminForm.style.display = 'block';
            }
        }

        function loginUser() {
            const regNo = document.getElementById('login-regno').value.toUpperCase();
            const password = document.getElementById('login-password').value;
            const rememberMe = document.getElementById('remember-me-checkbox').checked;

            // Check device security
            if (!checkDeviceSecurity(regNo)) {
                alert('An gano sabon na\'ura. Da fatan za a tuntubi admin don tabbatarwa.');
                return;
            }

            const user = allUsers.find(u => u.regNo === regNo && u.password === password && u.role === 'user');

            if (user) {
                if (user.status === 'suspended') {
                    alert('An dakatar da asusunka. Tuntuɓi admin.');
                    return;
                }
                currentUser = user;
                
                userActivity[currentUser.regNo] = { 
                    lastLogin: new Date().toISOString(), 
                    status: 'active',
                    deviceId: userDeviceId,
                    loginHistory: userActivity[currentUser.regNo]?.loginHistory || []
                };
                userActivity[currentUser.regNo].loginHistory.push({
                    date: new Date().toISOString(),
                    deviceId: userDeviceId
                });
                localStorage.setItem('userActivity', JSON.stringify(userActivity));
                
                if (rememberMe) {
                    localStorage.setItem('rememberedUser', JSON.stringify({ regNo: user.regNo, password: user.password }));
                } else {
                    localStorage.removeItem('rememberedUser');
                }
                // Save session token with expiry
                const sessionToken = { userId: user.regNo, expiry: new Date().getTime() + (SESSION_EXPIRY_DAYS * 24 * 60 * 60 * 1000) };
                localStorage.setItem('sessionToken', JSON.stringify(sessionToken));
                
                // Start free tier timer if applicable
                if (currentUser.paymentTier === 'free') {
                    startFreeTierTimer();
                }
                
                // Initialize user tokens for the day
                initializeUserTokens();
                
                showPage('dashboard-page');
            } else {
                alert('Lambar rajista ko kalmar sirri ba daidai ba ce.');
            }
        }

        // TOKENS SYSTEM FUNCTIONS
        function initializeUserTokens() {
            if (!currentUser) return;
            
            const today = new Date().toDateString();
            
            // Check if tokens need to be reset for today
            if (!currentUser.tokens || currentUser.tokens.date !== today) {
                const maxTokens = currentUser.paymentTier === 'free' ? TOKENS_FREE_TIER : TOKENS_STANDARD_TIER;
                
                currentUser.tokens = {
                    date: today,
                    remaining: maxTokens,
                    max: maxTokens,
                    lessonsToday: 0,
                    maxLessons: LESSONS_PER_DAY,
                    questionsToday: 0,
                    quizzesToday: 0
                };
                
                updateUserProgress();
            }
            
            // Start tokens reset timer
            startTokensResetTimer();
            
            // Update display
            updateTokensDisplay();
        }

        function updateTokensDisplay() {
            if (!currentUser || !currentUser.tokens) return;
            
            document.getElementById('tokens-count').textContent = currentUser.tokens.remaining;
            document.getElementById('lessons-today').textContent = `${currentUser.tokens.lessonsToday}/${currentUser.tokens.maxLessons}`;
            
            // Show warning if tokens are low
            const warningDiv = document.getElementById('tokens-warning');
            if (currentUser.tokens.remaining <= 0) {
                warningDiv.style.display = 'block';
                warningDiv.textContent = 'Ka cinye dukkan tokens na yau. Ba za ka iya yin karatu ba sai gobe.';
            } else if (currentUser.tokens.remaining <= 200) {
                warningDiv.style.display = 'block';
                warningDiv.textContent = `Tokens na yau sun ragu. Sauran: ${currentUser.tokens.remaining}`;
            } else {
                warningDiv.style.display = 'none';
            }
            
            // Update AI teacher page display
            if (document.getElementById('ai-tokens-count')) {
                document.getElementById('ai-tokens-count').textContent = currentUser.tokens.remaining;
                document.getElementById('ai-lesson-today').textContent = `${currentUser.tokens.lessonsToday}/${currentUser.tokens.maxLessons}`;
                
                // Update access status
                const accessStatus = document.getElementById('access-status');
                const aiWarning = document.getElementById('ai-tokens-warning');
                const dailyWarning = document.getElementById('daily-limit-warning');
                
                if (currentUser.tokens.remaining <= 0) {
                    accessStatus.textContent = '❌ An ƙare tokens';
                    accessStatus.className = 'access-locked';
                    aiWarning.style.display = 'block';
                    dailyWarning.style.display = 'none';
                } else if (currentUser.tokens.lessonsToday >= currentUser.tokens.maxLessons) {
                    accessStatus.textContent = '❌ Ka yi darasi ɗaya a yau';
                    accessStatus.className = 'access-locked';
                    aiWarning.style.display = 'none';
                    dailyWarning.style.display = 'block';
                } else {
                    accessStatus.textContent = '✅ A buɗe';
                    accessStatus.className = 'access-unlocked';
                    aiWarning.style.display = 'none';
                    dailyWarning.style.display = 'none';
                }
            }
            
            // Update profile display
            if (document.getElementById('profile-tokens-display')) {
                document.getElementById('profile-tokens-display').textContent = currentUser.tokens.remaining;
                document.getElementById('profile-lessons-today').textContent = `${currentUser.tokens.lessonsToday}/${currentUser.tokens.maxLessons}`;
            }
        }

        function startTokensResetTimer() {
            if (tokensResetTimer) {
                clearInterval(tokensResetTimer);
            }
            
            // Calculate time until midnight
            const now = new Date();
            const tomorrow = new Date(now);
            tomorrow.setDate(tomorrow.getDate() + 1);
            tomorrow.setHours(0, 0, 0, 0);
            
            const timeUntilReset = tomorrow.getTime() - now.getTime();
            
            // Start countdown
            tokensResetTimer = setInterval(() => {
                const now = new Date();
                const timeLeft = tomorrow.getTime() - now.getTime();
                
                if (timeLeft <= 0) {
                    // Reset tokens for new day
                    if (currentUser && currentUser.tokens) {
                        const maxTokens = currentUser.paymentTier === 'free' ? TOKENS_FREE_TIER : TOKENS_STANDARD_TIER;
                        
                        currentUser.tokens = {
                            date: new Date().toDateString(),
                            remaining: maxTokens,
                            max: maxTokens,
                            lessonsToday: 0,
                            maxLessons: LESSONS_PER_DAY,
                            questionsToday: 0,
                            quizzesToday: 0
                        };
                        
                        updateUserProgress();
                        updateTokensDisplay();
                    }
                    
                    // Reset timer for next day
                    startTokensResetTimer();
                    return;
                }
                
                // Update display
                const hours = Math.floor(timeLeft / (1000 * 60 * 60));
                const minutes = Math.floor((timeLeft % (1000 * 60 * 60)) / (1000 * 60));
                const seconds = Math.floor((timeLeft % (1000 * 60)) / 1000);
                
                if (document.getElementById('reset-time')) {
                    document.getElementById('reset-time').textContent = 
                        `${hours.toString().padStart(2, '0')}:${minutes.toString().padStart(2, '0')}:${seconds.toString().padStart(2, '0')}`;
                }
                
            }, 1000);
        }

        function checkTokensForAI() {
            if (!currentUser || !currentUser.tokens) {
                initializeUserTokens();
            }
            
            const today = new Date().toDateString();
            if (currentUser.tokens.date !== today) {
                initializeUserTokens();
            }
            
            // Check if user has tokens and hasn't exceeded daily lesson limit
            if (currentUser.tokens.remaining <= 0) {
                return { allowed: false, reason: 'Ka cinye dukkan tokens na yau. Ba za ka iya yin karatu ba sai gobe.' };
            }
            
            if (currentUser.tokens.lessonsToday >= currentUser.tokens.maxLessons) {
                return { allowed: false, reason: 'Ka yi darasi ɗaya a yau. Ba za ka iya ƙara yin karatu ba sai gobe.' };
            }
            
            return { allowed: true, reason: '' };
        }

        function deductTokens(amount) {
            if (!currentUser || !currentUser.tokens) return false;
            
            if (currentUser.tokens.remaining >= amount) {
                currentUser.tokens.remaining -= amount;
                currentUser.tokens.lessonsToday += 1;
                updateUserProgress();
                updateTokensDisplay();
                return true;
            }
            
            return false;
        }

        function checkDeviceSecurity(regNo) {
            const user = allUsers.find(u => u.regNo === regNo);
            if (!user) return true;
            
            const activity = userActivity[regNo];
            if (!activity || !activity.deviceId) return true;
            
            return activity.deviceId === userDeviceId;
        }

        function generateDeviceId() {
            const id = 'device_' + Math.random().toString(36).substr(2, 9) + '_' + Date.now();
            localStorage.setItem('userDeviceId', id);
            return id;
        }

        function checkSession() {
            const sessionToken = JSON.parse(localStorage.getItem('sessionToken'));
            if (sessionToken && new Date().getTime() < sessionToken.expiry) {
                const user = allUsers.find(u => u.regNo === sessionToken.userId);
                if (user) {
                    currentUser = user;
                    userActivity[currentUser.regNo] = { 
                        lastLogin: new Date().toISOString(), 
                        status: 'active',
                        deviceId: userDeviceId,
                        loginHistory: userActivity[currentUser.regNo]?.loginHistory || []
                    };
                    localStorage.setItem('userActivity', JSON.stringify(userActivity));
                    
                    // Start free tier timer if applicable
                    if (currentUser.paymentTier === 'free') {
                        startFreeTierTimer();
                    }
                    
                    // Initialize user tokens
                    initializeUserTokens();
                    
                    showPage('dashboard-page');
                    return true;
                }
            }
            return false;
        }

        function startFreeTierTimer() {
            // Load saved timer state
            const savedTimer = localStorage.getItem(`freeTierTimer_${currentUser.regNo}`);
            if (savedTimer) {
                freeTierTimeLeft = parseInt(savedTimer);
            }
            
            // Show timer on dashboard
            document.getElementById('free-tier-timer').style.display = 'block';
            updateTimerDisplay();
            
            // Start countdown
            freeTierTimer = setInterval(() => {
                freeTierTimeLeft--;
                localStorage.setItem(`freeTierTimer_${currentUser.regNo}`, freeTierTimeLeft);
                updateTimerDisplay();
                
                if (freeTierTimeLeft <= 0) {
                    clearInterval(freeTierTimer);
                    alert('Lokacin karatun wucin gadi ya ƙare! Da fatan za a biya kuɗin karatu don ci gaba.');
                    document.getElementById('free-tier-timer').innerHTML = '<p>Lokacin karatun wucin gadi ya ƙare!</p>';
                }
            }, 1000);
        }

        function updateTimerDisplay() {
            const hours = Math.floor(freeTierTimeLeft / 3600);
            const minutes = Math.floor((freeTierTimeLeft % 3600) / 60);
            const seconds = freeTierTimeLeft % 60;
            
            document.getElementById('timer-display').textContent = 
                `${hours.toString().padStart(2, '0')}:${minutes.toString().padStart(2, '0')}:${seconds.toString().padStart(2, '0')}`;
        }

        function loginAdmin() {
            const email = document.getElementById('admin-email').value;
            const password = document.getElementById('admin-password').value;
            
            if (ADMIN_CREDENTIALS[email] && ADMIN_CREDENTIALS[email].password === password) {
                currentUser = { 
                    role: 'admin', 
                    email: email, 
                    name: 'Admin',
                    adminRole: ADMIN_CREDENTIALS[email].role,
                    permissions: ADMIN_CREDENTIALS[email].permissions
                };
                showPage('admin-page');
            } else {
                alert('Email ko kalmar sirri ba daidai ba ce.');
            }
        }

        function updateDashboard() {
            if (currentUser && currentUser.role !== 'admin') {
                document.getElementById('welcome-message').textContent = `${translations[currentLang]['welcome-title']}, ${currentUser.name}!`;
                document.getElementById('selected-course-name').textContent = currentUser.departmentTitle;
                document.getElementById('selected-course-short').textContent = currentUser.departmentCode || '-';
                updateProgress();
                updateExamProgress();
                updateRewardDisplay();
                updateNextClass();
                translatePage(currentLang);
                updateNotificationBadge();
                document.querySelector('.admin-btn').style.display = 'none';
                checkAndUnlockModules();
                
                // Show/hide tier limitations
                if (currentUser.paymentTier === 'free') {
                    document.getElementById('free-tier-limitations').style.display = 'block';
                    document.getElementById('paid-tier-benefits').style.display = 'none';
                    // Disable certain features for free tier
                    document.getElementById('download-notepad-btn').classList.add('disabled');
                } else {
                    document.getElementById('free-tier-limitations').style.display = 'none';
                    document.getElementById('paid-tier-benefits').style.display = 'block';
                    document.getElementById('download-notepad-btn').classList.remove('disabled');
                }
                
                // Update tokens display
                updateTokensDisplay();
                
                // Show device warning if new device
                if (userActivity[currentUser.regNo] && userActivity[currentUser.regNo].deviceId !== userDeviceId) {
                    showDeviceWarning();
                }
            } else if (currentUser && currentUser.role === 'admin') {
                document.querySelector('.admin-btn').style.display = 'block';
            }
        }

        function showDeviceWarning() {
            const warning = document.createElement('div');
            warning.className = 'device-warning';
            warning.innerHTML = '⚠️ An gano sabon na\'ura. Idan ba kai bane, da fatan za a tuntubi admin.';
            document.querySelector('.dashboard-content').prepend(warning);
        }

        function updateProgress() {
            if (currentUser && currentUser.courses && currentUser.courses.length > 0) {
                const course = currentUser.courses[0];
                if (!course.courses) {
                    // Legacy user data structure fix
                    course.courses = [
                        { level: 'basic', zango1: { completedModules: 0, modules: [] }, zango2: { completedModules: 0, modules: [] } },
                        { level: 'intermediate', zango1: { completedModules: 0, modules: [] }, zango2: { completedModules: 0, modules: [] } },
                        { level: 'advance', zango1: { completedModules: 0, modules: [] }, zango2: { completedModules: 0, modules: [] } }
                    ];
                }
                const completedModules = course.courses.reduce((sum, c) => sum + (c.zango1.completedModules || 0) + (c.zango2.completedModules || 0), 0);
                const progressPercent = Math.round((completedModules / TOTAL_MODULES) * 100);
                
                document.getElementById('progress-bar').style.width = `${progressPercent}%`;
                document.getElementById('percentage-display').textContent = `${progressPercent}%`;
                document.getElementById('progress-text').textContent = `${translations[currentLang]['progress-text'].split(':')[0]}: ${progressPercent}%`;
                
                document.getElementById('module-percentage-display').textContent = `${progressPercent}%`;
                document.getElementById('completed-modules-count').textContent = `${completedModules} / ${TOTAL_MODULES}`;

                document.getElementById('certificate-btn').classList.toggle('disabled', progressPercent < 100);
            }
        }

        function updateExamProgress() {
            if (currentUser && currentUser.quizResults) {
                const totalQuizzes = Object.keys(currentUser.quizResults).length;
                const passedQuizzes = Object.values(currentUser.quizResults).filter(result => result.passed).length;
                const examPercent = totalQuizzes > 0 ? Math.round((passedQuizzes / totalQuizzes) * 100) : 0;
                
                document.getElementById('exam-progress-bar').style.width = `${examPercent}%`;
                document.getElementById('exam-percentage-display').textContent = `${examPercent}%`;
            }
        }

        function updateRewardDisplay() {
            if (currentUser) {
                const progress = calculateUserProgress();
                let reward = '🪨';
                
                if (progress >= 90) reward = '💎';
                else if (progress >= 75) reward = '⭐';
                else if (progress >= 60) reward = '🔷';
                else if (progress >= 45) reward = '🔶';
                else if (progress >= 30) reward = '🛠️';
                
                document.getElementById('student-reward').textContent = reward;
                document.getElementById('current-reward').textContent = reward;
            }
        }

        function updateNextClass() {
            if (currentUser && currentUser.studyDays) {
                const today = new Date();
                const days = ['Lahadi', 'Litinin', 'Talata', 'Laraba', 'Alhamis', 'Jumma\'a', 'Asabar'];
                const todayIndex = today.getDay();
                
                // Find next study day
                for (let i = 1; i <= 7; i++) {
                    const nextDayIndex = (todayIndex + i) % 7;
                    const nextDayName = days[nextDayIndex];
                    
                    if (currentUser.studyDays.includes(nextDayName)) {
                        const nextDate = new Date(today);
                        nextDate.setDate(today.getDate() + i);
                        document.getElementById('next-class').textContent = nextDate.toLocaleDateString('ha-NG');
                        return;
                    }
                }
                
                document.getElementById('next-class').textContent = '-';
            }
        }

        // AI Teacher Functions - UPDATED WITH TOKENS CHECK
        function initializeAITeacher() {
            // Reset AI teacher state
            document.getElementById('ai-topics-container').style.display = 'none';
            document.getElementById('ai-teaching-content').style.display = 'none';
            document.getElementById('ai-chat-container').style.display = 'none';
            
            // Update tokens display
            updateTokensDisplay();
            
            // Check if user can access AI teacher
            const accessCheck = checkTokensForAI();
            if (!accessCheck.allowed) {
                document.getElementById('ai-tokens-warning').style.display = 'block';
                document.getElementById('ai-tokens-warning').textContent = accessCheck.reason;
            }
        }

        function changeAITeacherLanguage(lang) {
            aiTeacherLanguage = lang;
        }

        function loadAITopics() {
            // Check tokens first
            const accessCheck = checkTokensForAI();
            if (!accessCheck.allowed) {
                alert(accessCheck.reason);
                return;
            }
            
            const level = document.getElementById('ai-level-select').value;
            const semester = document.getElementById('ai-semester-select').value;
            
            if (!level || !semester) {
                alert('Da fatan za a zaɓi level da zango.');
                return;
            }
            
            currentAILevel = level;
            currentAISemester = semester;
            
            const dept = currentUser.departmentTitle;
            const topics = departmentTopics[dept]?.[level];
            
            if (!topics) {
                alert('Babu topics don wannan department da level.');
                return;
            }
            
            const topicsList = document.getElementById('ai-topics-list');
            topicsList.innerHTML = '';
            
            // Filter topics by semester
            const startIndex = semester === 'zango1' ? 0 : 
                             level === 'basic' ? 12 :
                             level === 'intermediate' ? 25 : 25;
            const endIndex = semester === 'zango1' ? 
                           (level === 'basic' ? 12 : 
                            level === 'intermediate' ? 25 : 25) :
                           topics.length;
            
            for (let i = startIndex; i < endIndex; i++) {
                const topicItem = document.createElement('div');
                topicItem.className = 'module-select-item';
                topicItem.innerHTML = `
                    <span>${topics[i]}</span>
                `;
                topicItem.onclick = () => selectAITopic(topics[i], i);
                topicsList.appendChild(topicItem);
            }
            
            document.getElementById('ai-topics-container').style.display = 'block';
        }

        function selectAITopic(topic, index) {
            // Check tokens first
            const accessCheck = checkTokensForAI();
            if (!accessCheck.allowed) {
                alert(accessCheck.reason);
                return;
            }
            
            currentAITopic = topic;
            
            // Check if topic is locked (only available on study days)
            if (!isTopicAvailable(index)) {
                alert('Wannan topic ba a buɗe ba har sai ranar karatunka. Za ka iya aika saƙo zuwa Malam AI don tambaya.');
                document.getElementById('ai-topics-container').style.display = 'none';
                document.getElementById('ai-teaching-content').style.display = 'none';
                document.getElementById('ai-chat-container').style.display = 'block';
                return;
            }
            
            document.getElementById('ai-topics-container').style.display = 'none';
            document.getElementById('ai-teaching-content').style.display = 'block';
            
            // Deduct tokens for AI teaching
            if (deductTokens(AI_COST_PER_TOPIC)) {
                // Generate AI teaching content
                generateAITeaching(topic);
            } else {
                alert('Ba ka da isasshen tokens don yin karatu.');
                showPage('dashboard-page');
            }
        }

        function isTopicAvailable(topicIndex) {
            if (!currentUser || !currentUser.studyDays) return true;
            
            const today = new Date();
            const days = ['Lahadi', 'Litinin', 'Talata', 'Laraba', 'Alhamis', 'Jumma\'a', 'Asabar'];
            const todayName = days[today.getDay()];
            
            // Check if today is a study day
            if (currentUser.studyDays.includes(todayName)) {
                return true;
            }
            
            return false;
        }

        async function generateAITeaching(topic) {
            const responseDiv = document.getElementById('ai-teacher-response');
            responseDiv.innerHTML = '<p>Malam AI yana shirya darasin...</p>';
            
            try {
                // Use the OpenRouter API
                const apiResponse = await fetch('https://openrouter.ai/api/v1/chat/completions', {
                    method: 'POST',
                    headers: {
                        'Authorization': 'Bearer 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',
                        'Content-Type': 'application/json',
                    },
                    body: JSON.stringify({
                        model: 'openai/gpt-4o',
                        messages: [
                            {
                                role: 'user',
                                content: `Koyar da wannan darasin a cikin ${aiTeacherLanguage === 'ha' ? 'Hausa' : 'English'}: ${topic}. Yi amfani da matakin ${currentAILevel}. Ka ba da cikakken bayani, misalai, da hotuna masu dacewa.`
                            }
                        ],
                    }),
                });
                
                const data = await apiResponse.json();
                let aiContent = data.choices[0].message.content;
                
                // Process AI content to handle images properly
                aiContent = processAIContent(aiContent);
                
                responseDiv.innerHTML = `
                    <h3>${topic}</h3>
                    <div class="ai-explanation ai-content-processed">
                        ${aiContent}
                    </div>
                `;
                
                // Generate quiz for the topic
                generateAIQuiz(topic);
                
                // Update user progress
                updateUserAITopicProgress(topic);
                
            } catch (error) {
                console.error('Error calling AI API:', error);
                // Fallback to local content if API fails
                responseDiv.innerHTML = `
                    <h3>${topic}</h3>
                    <div class="ai-explanation">
                        ${generateFallbackAIContent(topic)}
                    </div>
                `;
                generateAIQuiz(topic);
                updateUserAITopicProgress(topic);
            }
        }

        function processAIContent(content) {
            // Process content to handle image links properly
            const imageRegex = /(https?:\/\/[^\s]+\.(jpg|jpeg|png|gif))/gi;
            return content.replace(imageRegex, '<img src="$1" alt="AI Content Image" style="max-width:100%; height:auto; border-radius:8px; margin:10px 0;">');
        }

        function generateFallbackAIContent(topic) {
            // Fallback content when API is not available
            const fallbackContent = {
                "1. Ma'anar Harshe da Tarihin Hausa": `
                    <p><strong>Ma'anar Harshe:</strong> Harshe wani tsari ne na alamomi da alamu da mutane ke amfani da su don sadarwa. 
                    Harshen Hausa yana daga cikin harsunan Chadic na reshen Afro-Asiatic.</p>
                    
                    <p><strong>Tarihin Hausa:</strong> Hausawa sun samo asali ne daga tsohuwar daular Hausa Bakwai: 
                    Daura, Kano, Katsina, Zazzau, Gobir, Rano, da Garun Gabas.</p>
                    
                    <p><strong>Muhimman Bayanai:</strong></p>
                    <ul>
                        <li>Harshen Hausa yana da masu magana sama da miliyan 50 a duniya</li>
                        <li>Ana amfani da shi a Najeriya, Nijar, Ghana, da sauran ƙasashe</li>
                        <li>Yana da rubutu na Larabci (Ajami) da kuma Latin (Boko)</li>
                    </ul>
                    
                    <img src="https://via.placeholder.com/400x200/006400/ffffff?text=Hausa+Language+Map" alt="Taswira na yankunan da ake magana da Hausa">
                `,
                "2. Asalin Harshen Hausa da Yankunan da ake amfani da shi": `
                    <p><strong>Asalin Harshen Hausa:</strong> Harshen Hausa ya samo asali ne daga yankin arewacin Najeriya da kudancin Nijar. 
                    Yana cikin rukunin harsunan Chadic na dangin Afro-Asiatic.</p>
                    
                    <p><strong>Yankunan da ake amfani da shi:</strong> Hausa yare ne na farko a arewacin Najeriya da kudancin Nijar. 
                    Haka kuma ana magana da shi a wasu sassan Kamaru, Chad, da Benin.</p>
                    
                    <p><strong>Muhimman Bayanai:</strong></p>
                    <ul>
                        <li>Hausa yana ɗaya daga cikin manyan harsunan Afirka</li>
                        <li>Yana da matsayin harshen kasuwanci a yankin Sahel</li>
                        <li>Ana amfani da shi a shirye-shiryen rediyo da talabijin a ƙasashe da yawa</li>
                    </ul>
                    
                    <img src="https://via.placeholder.com/400x200/006400/ffffff?text=Hausa+Spread+in+Africa" alt="Taswira na yaduwar harshen Hausa a Afirka">
                `
            };
            
            return fallbackContent[topic] || `<p>Malam AI yana shirya cikakken bayani game da: <strong>${topic}</strong>. 
            Za a ƙara cikakkun bayanai nan gaba.</p>`;
        }

        function generateAIQuiz(topic) {
            const quizContainer = document.getElementById('ai-quiz-container');
            
            // Generate 3 quiz questions for the topic
            const quizQuestions = [
                {
                    question: `Menene muhimmanci game da ${topic.split('. ')[1]}?`,
                    options: ["Muhimmiyar rawa a cikin harshe", "Ba shi da muhimmanci", "Wani abu ne na zamani", "Ba a san shi ba"],
                    answer: 0
                },
                {
                    question: `Yaya ${topic.split('. ')[1]} yake tasiri a cikin harshe?`,
                    options: ["Yana taimakawa fahimtar juna", "Yana dagula fahimta", "Babu tasiri", "Yana sa harshe ya yi wahala"],
                    answer: 0
                },
                {
                    question: `Menene misali na ${topic.split('. ')[1]}?`,
                    options: ["Misalin da ya dace da darasin", "Wani misali mara dacewa", "Babu misali", "Duk misalan suna daidai"],
                    answer: 0
                }
            ];
            
            let quizHTML = '<h4>Tambayoyin Don Tabbatar da Fahimta (3)</h4>';
            
            quizQuestions.forEach((q, index) => {
                quizHTML += `
                    <div class="quiz-question">
                        <p><strong>${index + 1}. ${q.question}</strong></p>
                        ${q.options.map((option, optIndex) => `
                            <div class="quiz-option" onclick="checkAIQuizAnswer(${index}, ${optIndex}, ${q.answer})">
                                ${option}
                            </div>
                        `).join('')}
                        <div id="ai-quiz-result-${index}"></div>
                    </div>
                `;
            });
            
            quizContainer.innerHTML = quizHTML;
        }

        function checkAIQuizAnswer(questionIndex, selectedIndex, correctIndex) {
            const resultDiv = document.getElementById(`ai-quiz-result-${questionIndex}`);
            const options = document.querySelectorAll(`#ai-quiz-container .quiz-question:nth-child(${questionIndex + 2}) .quiz-option`);
            
            options.forEach((option, index) => {
                option.classList.remove('selected', 'correct', 'incorrect');
                if (index === selectedIndex) {
                    option.classList.add('selected');
                    if (index === correctIndex) {
                        option.classList.add('correct');
                        resultDiv.innerHTML = '<p style="color: green;">✅ Daidai! Ka fahimci darasin.</p>';
                        
                        // Award points for correct answer
                        if (currentUser) {
                            currentUser.points = (currentUser.points || 0) + 5;
                            updateUserProgress();
                            updateExamProgress();
                        }
                    } else {
                        option.classList.add('incorrect');
                        resultDiv.innerHTML = '<p style="color: red;">❌ Ba daidai ba. Ka kara karantawa kuma ka sake gwadawa.</p>';
                    }
                } else if (index === correctIndex) {
                    option.classList.add('correct');
                }
            });
        }

        function updateUserAITopicProgress(topic) {
            if (!currentUser.aiProgress) {
                currentUser.aiProgress = {};
            }
            
            if (!currentUser.aiProgress[topic]) {
                currentUser.aiProgress[topic] = {
                    studied: true,
                    date: new Date().toLocaleString(),
                    quizScore: 0
                };
                
                // Update user in storage
                updateUserProgress();
            }
        }

        function regenerateAIResponse() {
            if (currentAITopic) {
                generateAITeaching(currentAITopic);
            }
        }

        function copyAIContent() {
            const aiContent = document.getElementById('ai-teacher-response').innerText;
            navigator.clipboard.writeText(aiContent).then(() => {
                alert('An kwafa bayanin Malam AI!');
            });
        }

        function saveToNotepad() {
            const aiContent = document.getElementById('ai-teacher-response').innerHTML;
            localStorage.setItem('aiNotepad', aiContent);
            alert('An ajiye bayanin a cikin Notepad!');
            showPage('notepad-page');
        }

        function sendAIMessage() {
            const input = document.getElementById('ai-chat-input');
            const message = input.value.trim();
            
            if (!message) return;
            
            // Add user message to chat
            addAIMessage(message, 'user');
            
            // Check if message can be sent (only on study days)
            if (!isTopicAvailable(0)) { // Using 0 as dummy index
                addAIMessage("Na gane tambayar ka. Zan amsa muku ranar karatunka. Za a buɗe wannan topic a ranar da za ka yi karatu.", 'ai');
            } else {
                // Simulate AI response
                setTimeout(() => {
                    const aiResponse = generateAIResponse(message);
                    addAIMessage(aiResponse, 'ai');
                }, 1000);
            }
            
            input.value = '';
        }

        function addAIMessage(message, sender) {
            const chatMessages = document.getElementById('ai-chat-messages');
            const messageDiv = document.createElement('div');
            messageDiv.className = `ai-message ${sender === 'user' ? 'user-message' : 'ai-response'}`;
            messageDiv.innerHTML = `
                <div class="message-sender">${sender === 'user' ? currentUser.name : 'Malam AI'}</div>
                <div class="message-text">${message}</div>
                <div class="message-time">${new Date().toLocaleTimeString()}</div>
            `;
            chatMessages.appendChild(messageDiv);
            chatMessages.scrollTop = chatMessages.scrollHeight;
        }

        function generateAIResponse(message) {
            // Simple AI response simulation
            const responses = [
                "Na gane tambayar ka. Zan yi ƙoƙari in ba ka cikakken bayani.",
                "Wannan tambaya mai kyau ce. Ga bayanina:",
                "Ina fahimtar abin da kake nufi. Ga cikakken bayani:",
                "Wannan batu ne mai muhimmanci. Ga yadda zan iya taimaka:"
            ];
            
            const randomResponse = responses[Math.floor(Math.random() * responses.length)];
            
            return `${randomResponse}\n\nDuk da haka, don cikakken bayani game da wannan batu, da fatan za a duba topic ɗin da ya dace a cikin darussan ku.`;
        }

        // Text-to-Speech Functions
        function playAIContent() {
            const aiContent = document.getElementById('ai-teacher-response').innerText;
            if (speechSynthesis.speaking) {
                speechSynthesis.cancel();
            }
            
            const speech = new SpeechSynthesisUtterance(aiContent);
            speech.lang = aiTeacherLanguage === 'ha' ? 'ha-NG' : 'en-US';
            speech.rate = 0.8;
            speech.pitch = 1;
            
            currentSpeech = speech;
            speechSynthesis.speak(speech);
        }

        function pauseAIContent() {
            if (speechSynthesis.speaking) {
                speechSynthesis.pause();
            }
        }

        function stopAIContent() {
            if (speechSynthesis.speaking) {
                speechSynthesis.cancel();
            }
        }

        // Calendar Functions
        function loadCalendar() {
            updateCalendarHeader();
            generateCalendarGrid();
            loadUpcomingClasses();
        }

        function updateCalendarHeader() {
            const monthNames = [
                "Janairu", "Faburairu", "Maris", "Afirilu", "Mayu", "Yuni",
                "Yuli", "Agusta", "Satumba", "Oktoba", "Nuwamba", "Disamba"
            ];
            
            document.getElementById('calendar-month-year').textContent = 
                `${monthNames[currentCalendarMonth]} ${currentCalendarYear}`;
        }

        function generateCalendarGrid() {
            const calendarGrid = document.getElementById('calendar-grid');
            calendarGrid.innerHTML = '';
            
            // Add day headers
            const dayHeaders = ['L', 'T', 'L', 'A', 'J', 'A', 'L'];
            dayHeaders.forEach(day => {
                const dayHeader = document.createElement('div');
                dayHeader.className = 'calendar-day';
                dayHeader.style.fontWeight = 'bold';
                dayHeader.textContent = day;
                calendarGrid.appendChild(dayHeader);
            });
            
            // Get first day of month
            const firstDay = new Date(currentCalendarYear, currentCalendarMonth, 1).getDay();
            
            // Get days in month
            const daysInMonth = new Date(currentCalendarYear, currentCalendarMonth + 1, 0).getDate();
            
            // Add empty cells for days before first day of month
            for (let i = 0; i < firstDay; i++) {
                const emptyDay = document.createElement('div');
                emptyDay.className = 'calendar-day';
                calendarGrid.appendChild(emptyDay);
            }
            
            // Add days of month
            const today = new Date();
            for (let day = 1; day <= daysInMonth; day++) {
                const dayElement = document.createElement('div');
                dayElement.className = 'calendar-day';
                dayElement.textContent = day;
                
                const currentDate = new Date(currentCalendarYear, currentCalendarMonth, day);
                
                // Check if it's today
                if (currentDate.toDateString() === today.toDateString()) {
                    dayElement.classList.add('current');
                }
                
                // Check if it's a study day
                if (currentUser && currentUser.studyDays) {
                    const days = ['Lahadi', 'Litinin', 'Talata', 'Laraba', 'Alhamis', 'Jumma\'a', 'Asabar'];
                    const dayName = days[currentDate.getDay()];
                    
                    if (currentUser.studyDays.includes(dayName)) {
                        dayElement.classList.add('study-day');
                        dayElement.classList.add('has-class');
                    }
                }
                
                // Check if it's in the past or future
                if (currentDate < today) {
                    dayElement.classList.add('past');
                } else {
                    dayElement.classList.add('future');
                }
                
                calendarGrid.appendChild(dayElement);
            }
        }

        function changeCalendarMonth(direction) {
            currentCalendarMonth += direction;
            
            if (currentCalendarMonth < 0) {
                currentCalendarMonth = 11;
                currentCalendarYear--;
            } else if (currentCalendarMonth > 11) {
                currentCalendarMonth = 0;
                currentCalendarYear++;
            }
            
            loadCalendar();
        }

        function loadUpcomingClasses() {
            const upcomingList = document.getElementById('upcoming-classes-list');
            
            if (!currentUser || !currentUser.studyDays) {
                upcomingList.innerHTML = '<p>Babu darussan nan gaba.</p>';
                return;
            }
            
            const today = new Date();
            const days = ['Lahadi', 'Litinin', 'Talata', 'Laraba', 'Alhamis', 'Jumma\'a', 'Asabar'];
            let upcomingHTML = '';
            let classesFound = 0;
            
            // Find next 5 study days
            for (let i = 1; i <= 30 && classesFound < 5; i++) {
                const nextDate = new Date(today);
                nextDate.setDate(today.getDate() + i);
                const dayName = days[nextDate.getDay()];
                
                if (currentUser.studyDays.includes(dayName)) {
                    upcomingHTML += `
                        <div class="course-item">
                            <h3>Darasi na Yau da Kullum</h3>
                            <p>${nextDate.toLocaleDateString('ha-NG')} (${dayName})</p>
                            <p>Lokaci: ${currentUser.studyTime}</p>
                        </div>
                    `;
                    classesFound++;
                }
            }
            
            upcomingList.innerHTML = upcomingHTML || '<p>Babu darussan nan gaba a wannan watan.</p>';
        }

        // Notepad Functions
        function loadNotepad() {
            const notepadContent = document.getElementById('notepad-content');
            const savedContent = localStorage.getItem('aiNotepad') || '';
            notepadContent.innerHTML = savedContent;
        }

        function saveNotepad() {
            const notepadContent = document.getElementById('notepad-content').innerHTML;
            localStorage.setItem('aiNotepad', notepadContent);
            alert('An ajiye Notepad!');
        }

        function downloadNotepad() {
            // Check if user is on free tier
            if (currentUser && currentUser.paymentTier === 'free') {
                alert('Ba za a iya sauke fayiloli a cikin karatun wucin gadi ba. Da fatan za a biya kuɗin karatu don samun damar saukewa.');
                return;
            }
            
            const notepadContent = document.getElementById('notepad-content').innerText;
            const blob = new Blob([notepadContent], { type: 'text/plain' });
            const url = URL.createObjectURL(blob);
            const a = document.createElement('a');
            a.href = url;
            a.download = `notepad-${currentUser.regNo}.txt`;
            a.click();
            URL.revokeObjectURL(url);
        }

        function clearNotepad() {
            if (confirm('Kana son share duk abin da ke cikin Notepad?')) {
                document.getElementById('notepad-content').innerHTML = '';
                localStorage.removeItem('aiNotepad');
            }
        }

        // Enhanced Certificate System
        function loadCertificate() {
            if (!currentUser) return;
            
            // Check if user has completed all modules
            const progress = calculateUserProgress();
            if (progress < 100) {
                alert('Ba ka kammala dukkan modules ba. Ka kammala karatun kafin ka iya duba certificate.');
                showPage('dashboard-page');
                return;
            }
            
            document.getElementById('certificate-regno').textContent = currentUser.regNo;
            document.getElementById('certificate-student-name').textContent = currentUser.name;
            document.getElementById('certificate-department').textContent = currentUser.departmentTitle;
            document.getElementById('certificate-date').textContent = new Date().toLocaleDateString('ha-NG');
            
            // Calculate reward and score based on performance
            const reward = calculateReward();
            const score = calculateCertificateScore();
            document.getElementById('certificate-reward').textContent = reward;
            document.getElementById('certificate-score').textContent = `Maki: ${score}/100`;
        }

        function calculateCertificateScore() {
            const points = currentUser.points || 0;
            const totalPossiblePoints = 400; // 40 modules × 10 points each
            
            return Math.min(100, Math.round((points / totalPossiblePoints) * 100));
        }

        function calculateReward() {
            const points = currentUser.points || 0;
            const totalPossiblePoints = 400; // 40 modules × 10 points each
            
            const percentage = (points / totalPossiblePoints) * 100;
            
            if (percentage >= 90) return "An ba ka lambar yabo ta Zinare saboda ƙwararren aiki!";
            if (percentage >= 75) return "An ba ka lambar yabo ta Azurfa saboda kyakkyawan aiki!";
            if (percentage >= 60) return "An ba ka lambar yabo ta Tagulla!";
            return "Ka ci nasarar kammala karatun!";
        }

        function downloadCertificate(format) {
            const certificate = document.getElementById('certificate-content');
            
            if (format === 'image') {
                // Convert certificate to image and download
                html2canvas(certificate).then(canvas => {
                    const link = document.createElement('a');
                    link.download = `certificate-${currentUser.regNo}.png`;
                    link.href = canvas.toDataURL();
                    link.click();
                });
            } else if (format === 'pdf') {
                // Generate PDF
                const { jsPDF } = window.jspdf;
                const pdf = new jsPDF('l', 'mm', 'a4');
                
                html2canvas(certificate).then(canvas => {
                    const imgData = canvas.toDataURL('image/png');
                    pdf.addImage(imgData, 'PNG', 10, 10, 280, 190);
                    pdf.save(`certificate-${currentUser.regNo}.pdf`);
                });
            }
        }

        function printCertificate() {
            const certificate = document.getElementById('certificate-content');
            const printWindow = window.open('', '_blank');
            printWindow.document.write(`
                <html>
                    <head>
                        <title>Certificate - ${currentUser.regNo}</title>
                        <style>
                            body { font-family: 'Times New Roman', serif; }
                            .certificate { border: 2px solid #000; padding: 20px; }
                        </style>
                    </head>
                    <body>
                        ${certificate.innerHTML}
                    </body>
                </html>
            `);
            printWindow.print();
            printWindow.close();
        }

        function shareCertificate() {
            if (navigator.share) {
                navigator.share({
                    title: 'My Certificate - Jami\'ar IHAME',
                    text: `Na kammala karatu a Jami'ar IHAME a cikin ${currentUser.departmentTitle}!`,
                    url: window.location.href
                });
            } else {
                alert('Share feature not supported in this browser. Use download instead.');
            }
        }

        // Enhanced Chat System
        function loadDepartmentChatOptions() {
            const select = document.getElementById('department-chat-select');
            select.innerHTML = '<option value="">Zaɓi Department</option>';
            
            if (currentUser && currentUser.departmentTitle) {
                const option = document.createElement('option');
                option.value = currentUser.departmentTitle;
                option.textContent = currentUser.departmentTitle;
                select.appendChild(option);
            }
        }

        function loadDepartmentChat() {
            const dept = document.getElementById('department-chat-select').value;
            if (!dept) return;
            
            const chatMessages = document.getElementById('department-chat-messages');
            chatMessages.innerHTML = '<p>Yana loda saƙonni...</p>';
            
            // Set up media upload
            const mediaInput = document.getElementById('chat-media-input');
            mediaInput.onchange = handleMediaUpload;
            
            // In real implementation, fetch from Node.js API
            setTimeout(() => {
                currentChatMessages = [
                    {
                        id: 1,
                        senderId: 'ADMIN',
                        senderName: 'Admin',
                        message: 'Barka da zuwa dandalin tattaunawa!',
                        timestamp: new Date(Date.now() - 3600000).toLocaleString(),
                        likes: [],
                        edited: false
                    },
                    {
                        id: 2,
                        senderId: 'HSA-2024-0001', 
                        senderName: 'Musa',
                        message: 'Ina tambaya game da darasi na 3.',
                        timestamp: new Date(Date.now() - 1800000).toLocaleString(),
                        likes: ['HSA-2024-0002'],
                        edited: false
                    }
                ];
                
                renderChatMessages();
                
                // Update group chat stats
                updateGroupChatStats(dept);
            }, 1000);
        }

        function updateGroupChatStats(dept) {
            const statsDiv = document.getElementById('group-chat-stats');
            if (!statsDiv) return;
            
            // Count active students in the department
            const activeStudents = allUsers.filter(user => 
                user.role === 'user' && 
                user.departmentTitle === dept && 
                userActivity[user.regNo]?.status === 'active'
            ).length;
            
            statsDiv.innerHTML = `Dalibai: ${activeStudents} | Active: ${activeStudents}`;
        }

        function handleMediaUpload(event) {
            const file = event.target.files[0];
            if (!file) return;
            
            const preview = document.getElementById('chat-media-preview');
            preview.innerHTML = '';
            
            if (file.type.startsWith('image/')) {
                const img = document.createElement('img');
                img.src = URL.createObjectURL(file);
                preview.appendChild(img);
            } else if (file.type.startsWith('video/')) {
                const video = document.createElement('video');
                video.src = URL.createObjectURL(file);
                video.controls = true;
                preview.appendChild(video);
            } else if (file.type.startsWith('audio/')) {
                const audio = document.createElement('audio');
                audio.src = URL.createObjectURL(file);
                audio.controls = true;
                preview.appendChild(audio);
            }
            
            // In real implementation, upload to server and send message with media
        }

        function renderChatMessages() {
            const chatMessages = document.getElementById('department-chat-messages');
            const currentUserId = currentUser?.regNo || '';
            
            chatMessages.innerHTML = currentChatMessages.map(msg => {
                const isMyMessage = msg.senderId === currentUserId;
                const isAdmin = msg.senderId === 'ADMIN';
                
                return `
                    <div class="message ${isMyMessage ? 'my-message' : 'their-message'} ${isAdmin ? 'admin-message' : ''}">
                        <div class="message-sender">${msg.senderName}</div>
                        <div class="message-text" id="message-text-${msg.id}">${msg.message}</div>
                        <div class="message-time">${msg.timestamp} ${msg.edited ? '(An gyara)' : ''}</div>
                        <div class="message-actions">
                            ${!isAdmin ? `<button onclick="likeMessage(${msg.id})">👍 ${msg.likes.length}</button>` : ''}
                            ${isMyMessage ? `
                                <button onclick="editMessage(${msg.id})">Gyara</button>
                                <button onclick="deleteMessage(${msg.id})">Goge</button>
                                <button onclick="forwardMessage(${msg.id})">Tura</button>
                            ` : ''}
                        </div>
                    </div>
                `;
            }).join('');
        }

        function sendChatMessage() {
            const input = document.getElementById('chat-message-input');
            const message = input.value.trim();
            
            if (!message) return;
            
            const newMessage = {
                id: Date.now(),
                senderId: currentUser.regNo,
                senderName: currentUser.name,
                message: message,
                timestamp: new Date().toLocaleString(),
                likes: [],
                edited: false,
                forwarded: false
            };
            
            currentChatMessages.push(newMessage);
            renderChatMessages();
            input.value = '';
            
            // Clear media preview
            document.getElementById('chat-media-preview').innerHTML = '';
            document.getElementById('chat-media-input').value = '';
        }

        // Profile Management Functions
        function displayProfile() {
            if (currentUser) {
                document.getElementById('profile-regno-display').textContent = currentUser.regNo;
                document.getElementById('profile-name-display').textContent = currentUser.name;
                document.getElementById('profile-email-display').textContent = currentUser.email;
                document.getElementById('profile-faculty-display').textContent = currentUser.faculty;
                document.getElementById('profile-department-display').textContent = currentUser.departmentTitle;
                document.getElementById('profile-level-display').textContent = currentUser.level;
                document.getElementById('profile-previous-education-display').textContent = currentUser.previousEducation || 'Ba a shigar ba';
                document.getElementById('profile-study-time-display').textContent = currentUser.studyTime || 'Ba a shigar ba';
                document.getElementById('profile-study-days-display').textContent = currentUser.studyDays ? currentUser.studyDays.join(', ') : 'Ba a shigar ba';
                document.getElementById('profile-tier-display').textContent = currentUser.paymentTier === 'free' ? 'Karatun Wucin Gadi' : 'Cikakken Karatu';
                document.getElementById('profile-pic-preview').src = currentUser.photo;
                
                // Update tokens display
                if (currentUser.tokens) {
                    document.getElementById('profile-tokens-display').textContent = currentUser.tokens.remaining;
                    document.getElementById('profile-lessons-today').textContent = `${currentUser.tokens.lessonsToday}/${currentUser.tokens.maxLessons}`;
                }
                
                // Populate edit fields
                document.getElementById('edit-name').value = currentUser.name;
                document.getElementById('edit-email').value = currentUser.email;
                document.getElementById('edit-phone').value = currentUser.phone;
            }
        }

        function enableProfileEdit() {
            document.getElementById('profile-display-fields').style.display = 'none';
            document.getElementById('profile-edit-fields').style.display = 'block';
        }

        function cancelProfileEdit() {
            document.getElementById('profile-display-fields').style.display = 'block';
            document.getElementById('profile-edit-fields').style.display = 'none';
        }

        function saveProfileChanges() {
            const name = document.getElementById('edit-name').value;
            const email = document.getElementById('edit-email').value;
            const phone = document.getElementById('edit-phone').value;
            
            if (!name || !email) {
                alert('Da fatan za a cika dukkan filaye masu muhimmanci.');
                return;
            }
            
            currentUser.name = name;
            currentUser.email = email;
            currentUser.phone = phone;
            
            // Update user in storage
            updateUserProgress();
            
            alert('An ajiye canje-canjen bayanan ka.');
            displayProfile();
            cancelProfileEdit();
        }

        function showChangePassword() {
            document.getElementById('change-password-fields').style.display = 'block';
        }

        function cancelPasswordChange() {
            document.getElementById('change-password-fields').style.display = 'none';
        }

        function changePassword() {
            const currentPassword = document.getElementById('current-password').value;
            const newPassword = document.getElementById('new-password').value;
            const confirmPassword = document.getElementById('confirm-password').value;
            
            if (!currentPassword || !newPassword || !confirmPassword) {
                alert('Da fatan za a cika dukkan filaye.');
                return;
            }
            
            if (currentPassword !== currentUser.password) {
                alert('Tsohon kalmar sirri ba daidai ba ce.');
                return;
            }
            
            if (newPassword !== confirmPassword) {
                alert('Sabuwar kalmar sirri da tabbatarta ba su dace ba.');
                return;
            }
            
            currentUser.password = newPassword;
            
            // Update user in storage
            updateUserProgress();
            
            alert('An canza kalmar sirri cikin nasara.');
            cancelPasswordChange();
        }

        // Forgot Password System
        function resetPassword() {
            const email = document.getElementById('forgot-password-email').value;
            
            if (!email) {
                alert('Da fatan za a shigar da email ɗinka.');
                return;
            }
            
            // Check if email exists in the system
            const user = allUsers.find(u => u.email === email);
            
            if (user) {
                // Generate new password
                const newPassword = generateRandomPassword();
                
                // Update user password
                user.password = newPassword;
                localStorage.setItem('allUsers', JSON.stringify(allUsers));
                
                // Show success message
                document.getElementById('reset-success').style.display = 'block';
                
                // In a real implementation, send email with new password
                console.log(`New password for ${email}: ${newPassword}`);
            } else {
                alert('Ba a samu asusu da wannan email ba.');
            }
        }

        function generateRandomPassword() {
            const chars = 'ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789';
            let password = '';
            for (let i = 0; i < 8; i++) {
                password += chars.charAt(Math.floor(Math.random() * chars.length));
            }
            return password;
        }

        // Settings Functions
        function initializeSettingsDisplay() {
            // Load saved settings
            const savedFontSize = localStorage.getItem('fontSize') || '16px';
            const savedFontStyle = localStorage.getItem('fontStyle') || 'Nunito, sans-serif';
            const savedBrightness = localStorage.getItem('brightness') || '1';
            const savedBrightnessColor = localStorage.getItem('brightnessColor') || 'white';
            const savedDarkMode = localStorage.getItem('darkMode') === 'true';
            
            document.getElementById('font-size-select').value = savedFontSize;
            document.getElementById('font-style-select').value = savedFontStyle;
            document.getElementById('brightness-slider').value = savedBrightness;
            document.getElementById('dark-mode-toggle').checked = savedDarkMode;
            
            // Select brightness color
            selectBrightnessColor(savedBrightnessColor);
            
            // Apply settings
            applyDisplaySettings();
        }

        function selectBrightnessColor(color) {
            // Remove selected class from all colors
            document.querySelectorAll('.brightness-color').forEach(el => {
                el.classList.remove('selected');
            });
            
            // Add selected class to clicked color
            event.target.classList.add('selected');
            
            // Save selected color
            localStorage.setItem('brightnessColor', color);
            
            // Apply color filter
            applyColorFilter(color);
        }

        function applyColorFilter(color) {
            const colorFilters = {
                'white': 'none',
                'black': 'brightness(0.8) contrast(1.2)',
                'green': 'hue-rotate(90deg) saturate(0.8)',
                'grey': 'grayscale(1) brightness(0.9)',
                'brown': 'sepia(0.5) hue-rotate(-30deg) saturate(1.2)',
                'pink': 'hue-rotate(300deg) saturate(1.5) brightness(1.1)',
                'purple': 'hue-rotate(270deg) saturate(1.3)',
                'red': 'hue-rotate(0deg) saturate(1.5)',
                'blue': 'hue-rotate(210deg) saturate(1.3)',
                'yellow': 'hue-rotate(60deg) saturate(1.5) brightness(1.1)',
                'milk': 'brightness(1.1) contrast(0.9) saturate(0.8)'
            };
            
            document.body.style.filter = colorFilters[color] || 'none';
        }

        function applyDisplaySettings() {
            const fontSize = document.getElementById('font-size-select').value;
            const fontStyle = document.getElementById('font-style-select').value;
            const brightness = document.getElementById('brightness-slider').value;
            const darkMode = document.getElementById('dark-mode-toggle').checked;
            const brightnessColor = localStorage.getItem('brightnessColor') || 'white';
            
            // Apply to document
            document.body.style.fontSize = fontSize;
            document.body.style.fontFamily = fontStyle;
            
            // Apply brightness and color
            applyColorFilter(brightnessColor);
            document.body.style.filter += ` brightness(${brightness})`;
            
            if (darkMode) {
                document.body.classList.add('dark-mode');
            } else {
                document.body.classList.remove('dark-mode');
            }
            
            // Save settings
            localStorage.setItem('fontSize', fontSize);
            localStorage.setItem('fontStyle', fontStyle);
            localStorage.setItem('brightness', brightness);
            localStorage.setItem('darkMode', darkMode);
        }

        // Admin Functions
        function loadAdminDashboard() {
            // Load admin role-specific tabs
            loadAdminRoleTabs();
            
            // Load default admin panel based on role
            loadAdminPanelByRole(currentUser.adminRole);
        }

        function loadAdminRoleTabs() {
            const tabsContainer = document.getElementById('admin-role-tabs');
            tabsContainer.innerHTML = '';
            
            const adminRoles = {
                'super_admin': 'Super Admin',
                'registrar': 'Registrar',
                'monitor': 'Monitor',
                'teacher': 'Teacher',
                'exam_manager': 'Exam Manager',
                'librarian': 'Librarian'
            };
            
            for (const role in adminRoles) {
                if (currentUser.permissions.includes('all') || currentUser.adminRole === role) {
                    const tab = document.createElement('div');
                    tab.className = 'admin-role-tab';
                    tab.textContent = adminRoles[role];
                    tab.onclick = () => loadAdminPanelByRole(role);
                    tabsContainer.appendChild(tab);
                }
            }
            
            // Activate the first tab
            if (tabsContainer.firstChild) {
                tabsContainer.firstChild.classList.add('active');
            }
        }

        function loadAdminPanelByRole(role) {
            const panelContent = document.getElementById('admin-panel-content');
            
            // Remove active class from all tabs
            document.querySelectorAll('.admin-role-tab').forEach(tab => tab.classList.remove('active'));
            // Add active class to clicked tab
            event.target.classList.add('active');
            
            switch(role) {
                case 'super_admin':
                    panelContent.innerHTML = `
                        <div class="admin-stats">
                            <div class="admin-stat-card">
                                <h3>Adadin Dalibai</h3>
                                <p id="total-students">0</p>
                            </div>
                            <div class="admin-stat-card">
                                <h3>Total Kudade (₦)</h3>
                                <p id="total-earnings">0</p>
                            </div>
                            <div class="admin-stat-card">
                                <h3>Masu Biya</h3>
                                <p id="paid-students">0</p>
                            </div>
                            <div class="admin-stat-card">
                                <h3>Masu Karatun Wucin Gadi</h3>
                                <p id="free-students">0</p>
                            </div>
                        </div>
                        
                        <h3>Pending Registrations (Masu jiran biya)</h3>
                        <div id="pending-registrations" class="pending-registrations admin-registrations">
                        </div>
                        
                        <h3>Jerin Dalibai</h3>
                        <table class="admin-table">
                            <thead>
                                <tr>
                                    <th>Suna</th>
                                    <th>Lambar Rajista</th>
                                    <th>Nau'in Karatu</th>
                                    <th>Aiki</th>
                                </tr>
                            </thead>
                            <tbody id="student-list">
                            </tbody>
                        </table>
                        
                        <h3>Tsofaffin Dalibai (Alumni)</h3>
                        <button onclick="showPage('admin-alumni-page')">Duba Alumni</button>
                        
                        <h3>Student Notifications (Sanarwa ga Dalibai)</h3>
                        <div>
                            <input type="text" id="notification-message" placeholder="Saƙon sanarwa">
                            <button onclick="sendNotificationToAll()">Aika wa Duka Dalibai</button>
                        </div>
                    `;
                    loadPendingRegistrations();
                    loadStudentList();
                    loadAdminStats();
                    break;
                    
                case 'registrar':
                    panelContent.innerHTML = `
                        <div class="admin-stats">
                            <div class="admin-stat-card">
                                <h3>Pending Registrations</h3>
                                <p id="pending-count">0</p>
                            </div>
                            <div class="admin-stat-card">
                                <h3>Approved Today</h3>
                                <p id="approved-today">0</p>
                            </div>
                        </div>
                        
                        <h3>Pending Registrations (Masu jiran biya)</h3>
                        <div id="pending-registrations" class="pending-registrations admin-registrations">
                        </div>
                    `;
                    loadPendingRegistrations();
                    break;
                    
                case 'monitor':
                    panelContent.innerHTML = `
                        <h3>Department Chats</h3>
                        <select id="monitor-dept-select" onchange="loadMonitorChat()">
                            <option value="">Zaɓi Department</option>
                        </select>
                        <div class="chat-container">
                            <div class="chat-messages" id="monitor-chat-messages">
                                <p>Zaɓi department daga ƙasa don duba tattaunawa</p>
                            </div>
                        </div>
                        
                        <h3>Send Message to Department</h3>
                        <div>
                            <select id="message-dept-select">
                                <option value="">Zaɓi Department</option>
                            </select>
                            <input type="text" id="admin-message" placeholder="Saƙon admin">
                            <button onclick="sendAdminMessage()">Aika</button>
                        </div>
                    `;
                    // Populate department selects
                    const deptSelect1 = document.getElementById('monitor-dept-select');
                    const deptSelect2 = document.getElementById('message-dept-select');
                    deptSelect1.innerHTML = deptSelect2.innerHTML = '<option value="">Zaɓi Department</option>';
                    for (const faculty in facultiesData) {
                        facultiesData[faculty].departments.forEach(dept => {
                            const option = document.createElement('option');
                            option.value = dept.title;
                            option.textContent = dept.title;
                            deptSelect1.appendChild(option.cloneNode(true));
                            deptSelect2.appendChild(option.cloneNode(true));
                        });
                    }
                    break;
                    
                case 'teacher':
                    panelContent.innerHTML = `
                        <h3>Module Management</h3>
                        <div>
                            <select id="module-level">
                                <option value="basic">Karamin Mataki/Basic</option>
                                <option value="intermediate">Matsakaicin Mataki/Intermediate</option>
                                <option value="advance">Babban Mataki/Advance</option>
                            </select>
                            <select id="module-semester">
                                <option value="zango1">Zango na Farko</option>
                                <option value="zango2">Zango na Biyu</option>
                            </select>
                            <input type="text" id="module-title" placeholder="Module Title">
                            <textarea id="module-content-text" placeholder="Module Content" rows="5"></textarea>
                            <button onclick="addNewModule()">Ƙara Module</button>
                        </div>
                        
                        <h3>Current Modules</h3>
                        <div id="modules-management-list">
                        </div>
                        
                        <h3>Student Progress</h3>
                        <select id="progress-dept-select" onchange="loadStudentProgress()">
                            <option value="">Zaɓi Department</option>
                        </select>
                        <div id="student-progress-list"></div>
                    `;
                    // Populate department select
                    const progressDeptSelect = document.getElementById('progress-dept-select');
                    progressDeptSelect.innerHTML = '<option value="">Zaɓi Department</option>';
                    for (const faculty in facultiesData) {
                        facultiesData[faculty].departments.forEach(dept => {
                            const option = document.createElement('option');
                            option.value = dept.title;
                            option.textContent = dept.title;
                            progressDeptSelect.appendChild(option);
                        });
                    }
                    break;
                    
                case 'exam_manager':
                    panelContent.innerHTML = `
                        <h3>Quiz Management (Gudanar da Jarabawowi)</h3>
                        <div class="quiz-management">
                            <div class="quiz-form">
                                <h4>Ƙara Sabuwar Tambaya</h4>
                                <select id="quiz-dept">
                                    <option value="">Zaɓi Department</option>
                                </select>
                                <input type="text" id="quiz-question" placeholder="Tambaya">
                                <div id="quiz-options">
                                    <div class="option-input">
                                        <input type="text" placeholder="Zaɓi 1">
                                        <input type="radio" name="correct-answer" value="0">
                                    </div>
                                    <div class="option-input">
                                        <input type="text" placeholder="Zaɓi 2">
                                        <input type="radio" name="correct-answer" value="1">
                                    </div>
                                    <div class="option-input">
                                        <input type="text" placeholder="Zaɓi 3">
                                        <input type="radio" name="correct-answer" value="2">
                                    </div>
                                    <div class="option-input">
                                        <input type="text" placeholder="Zaɓi 4">
                                        <input type="radio" name="correct-answer" value="3">
                                    </div>
                                </div>
                                <button onclick="addQuizQuestion()">Ƙara Tambaya</button>
                            </div>
                        </div>
                        
                        <h3>Exam Results</h3>
                        <select id="exam-dept-select" onchange="loadExamResults()">
                            <option value="">Zaɓi Department</option>
                        </select>
                        <div id="exam-results"></div>
                    `;
                    // Populate department selects
                    const quizDeptSelect = document.getElementById('quiz-dept');
                    const examDeptSelect = document.getElementById('exam-dept-select');
                    quizDeptSelect.innerHTML = examDeptSelect.innerHTML = '<option value="">Zaɓi Department</option>';
                    for (const faculty in facultiesData) {
                        facultiesData[faculty].departments.forEach(dept => {
                            const option = document.createElement('option');
                            option.value = dept.title;
                            option.textContent = dept.title;
                            quizDeptSelect.appendChild(option.cloneNode(true));
                            examDeptSelect.appendChild(option.cloneNode(true));
                        });
                    }
                    break;
                    
                case 'librarian':
                    panelContent.innerHTML = `
                        <h3>Library Management (Gudanar da Littattafai)</h3>
                        <div>
                            <input type="text" id="doc-title" placeholder="Sunan Document">
                            <input type="text" id="doc-description" placeholder="Bayanin Document">
                            <input type="file" id="doc-file" accept=".pdf,.doc,.docx,.txt">
                            <select id="doc-department">
                                <option value="">Zaɓi Department</option>
                            </select>
                            <select id="doc-level">
                                <option value="">Zaɓi Level</option>
                                <option value="basic">Basic</option>
                                <option value="intermediate">Intermediate</option>
                                <option value="advance">Advance</option>
                            </select>
                            <button onclick="uploadLibraryDocument()">Ƙara Document</button>
                        </div>
                        
                        <h3>Library Statistics</h3>
                        <div class="admin-stats">
                            <div class="admin-stat-card">
                                <h3>Total Documents</h3>
                                <p id="total-documents">${libraryData.length}</p>
                            </div>
                            <div class="admin-stat-card">
                                <h3>Most Popular</h3>
                                <p id="popular-doc">Nazarin Hausa</p>
                            </div>
                        </div>
                    `;
                    // Populate department select
                    const docDeptSelect = document.getElementById('doc-department');
                    docDeptSelect.innerHTML = '<option value="">Zaɓi Department</option>';
                    for (const faculty in facultiesData) {
                        facultiesData[faculty].departments.forEach(dept => {
                            const option = document.createElement('option');
                            option.value = dept.title;
                            option.textContent = dept.title;
                            docDeptSelect.appendChild(option);
                        });
                    }
                    break;
            }
        }

        function loadPendingRegistrations() {
            const container = document.getElementById('pending-registrations');
            if (!container) return;
            
            if (pendingRegistrations.length === 0) {
                container.innerHTML = '<p>Babu masu jiran biya a yanzu.</p>';
                return;
            }
            
            container.innerHTML = pendingRegistrations.map((reg, index) => `
                <div class="registration-item">
                    <div class="pending-user-info">
                        <p><strong>Suna:</strong> ${reg.name}</p>
                        <p><strong>Email:</strong> ${reg.email}</p>
                        <p><strong>Department:</strong> ${reg.departmentTitle}</p>
                        <p><strong>Level:</strong> ${reg.level}</p>
                        <p><strong>Nau'in Karatu:</strong> ${reg.paymentTier === 'free' ? 'Karatun Wucin Gadi' : 'Cikakken Karatu'}</p>
                        <p><strong>Lokacin Karatu:</strong> ${reg.studyTime}</p>
                        <p><strong>Ranakun Karatu:</strong> ${reg.studyDays.join(', ')}</p>
                        <p><strong>Na'ura:</strong> ${reg.deviceId || 'Ba a gano ba'}</p>
                    </div>
                    <div class="payment-actions">
                        ${reg.paymentTier === 'paid' ? `
                            <button class="payment-btn" onclick="approveRegistration(${index})">Amince Biya</button>
                            <button class="payment-btn delete-btn" onclick="rejectRegistration(${index})">Ƙi Biya</button>
                        ` : `
                            <button class="payment-btn" onclick="approveRegistration(${index})">Amince Rajista</button>
                        `}
                    </div>
                </div>
            `).join('');
        }

        function approveRegistration(index) {
            const reg = pendingRegistrations[index];
            
            // Generate registration number
            const year = new Date().getFullYear();
            const deptCode = reg.departmentCode;
            const sequence = allUsers.filter(u => u.departmentCode === deptCode).length + 1;
            const regNo = `IHAME/${year}/${deptCode}/${sequence.toString().padStart(4, '0')}`;
            
            // Create user object
            const user = {
                regNo: regNo,
                name: reg.name,
                birthYear: reg.birthYear,
                photo: reg.photo,
                email: reg.email,
                password: reg.password,
                phone: reg.phone,
                previousEducation: reg.previousEducation,
                educationLevel: reg.educationLevel,
                faculty: reg.faculty,
                departmentTitle: reg.departmentTitle,
                departmentCode: reg.departmentCode,
                level: reg.level,
                studyTime: reg.studyTime,
                studyDays: reg.studyDays,
                role: 'user',
                status: 'active',
                paymentTier: reg.paymentTier,
                paymentStatus: 'approved',
                registrationDate: new Date().toLocaleString(),
                courses: [{
                    department: reg.departmentTitle,
                    courses: [
                        { level: 'basic', zango1: { completedModules: 0, modules: [] }, zango2: { completedModules: 0, modules: [] } },
                        { level: 'intermediate', zango1: { completedModules: 0, modules: [] }, zango2: { completedModules: 0, modules: [] } },
                        { level: 'advance', zango1: { completedModules: 0, modules: [] }, zango2: { completedModules: 0, modules: [] } }
                    ]
                }],
                points: 0,
                deviceId: reg.deviceId
            };
            
            // Add to all users
            allUsers.push(user);
            localStorage.setItem('allUsers', JSON.stringify(allUsers));
            
            // Remove from pending
            pendingRegistrations.splice(index, 1);
            localStorage.setItem('pendingRegistrations', JSON.stringify(pendingRegistrations));
            
            // Send registration confirmation email
            sendRegistrationEmail(user);
            
            alert(`An amince da rajista! Lambar rajista: ${regNo}`);
            loadPendingRegistrations();
            loadStudentList();
            loadAdminStats();
        }

        function sendRegistrationEmail(user) {
            // In a real implementation, this would send an actual email
            console.log(`Registration confirmation sent to ${user.email}`);
            console.log(`Registration Number: ${user.regNo}`);
            console.log(`Welcome to JAMI'AR IHAME!`);
        }

        function rejectRegistration(index) {
            if (confirm('Kuna da tabbacin cewa kuna son ƙin wannan rajista?')) {
                pendingRegistrations.splice(index, 1);
                localStorage.setItem('pendingRegistrations', JSON.stringify(pendingRegistrations));
                alert('An ƙi rajista.');
                loadPendingRegistrations();
            }
        }

        function loadStudentList() {
            const studentList = document.getElementById('student-list');
            if (!studentList) return;
            
            const students = allUsers.filter(u => u.role === 'user');
            
            if (students.length === 0) {
                studentList.innerHTML = '<tr><td colspan="4">Babu dalibai a yanzu.</td></tr>';
                return;
            }
            
            studentList.innerHTML = students.map(student => `
                <tr>
                    <td>${student.name}</td>
                    <td>${student.regNo}</td>
                    <td>${student.paymentTier === 'free' ? 'Karatun Wucin Gadi' : 'Cikakken Karatu'}</td>
                    <td>
                        <button onclick="viewStudentDetails('${student.regNo}')">Duba Bayanai</button>
                        <button class="delete-btn" onclick="deleteStudent('${student.regNo}')">Share</button>
                    </td>
                </tr>
            `).join('');
        }

        function loadAdminStats() {
            const students = allUsers.filter(u => u.role === 'user');
            const totalStudents = students.length;
            const paidStudents = students.filter(s => s.paymentTier === 'paid').length;
            const freeStudents = students.filter(s => s.paymentTier === 'free').length;
            
            // Calculate total earnings
            let totalEarnings = 0;
            students.forEach(student => {
                if (student.paymentTier === 'paid') {
                    totalEarnings += facultyPricing[student.faculty] || 0;
                }
            });
            
            const pendingCount = pendingRegistrations.length;
            
            document.getElementById('total-students').textContent = totalStudents;
            document.getElementById('total-earnings').textContent = `₦${totalEarnings}`;
            document.getElementById('paid-students').textContent = paidStudents;
            document.getElementById('free-students').textContent = freeStudents;
            document.getElementById('pending-count').textContent = pendingCount;
            document.getElementById('approved-today').textContent = '0'; // Would need to track daily approvals
        }

        function loadAlumni() {
            const alumniList = document.getElementById('alumni-list');
            
            // Filter users who have completed their studies (progress >= 100%)
            const alumni = allUsers.filter(user => {
                if (user.role !== 'user') return false;
                const progress = calculateUserProgressForStudent(user);
                return progress >= 100;
            });
            
            if (alumni.length === 0) {
                alumniList.innerHTML = '<p>Babu tsofaffin dalibai a yanzu.</p>';
                return;
            }
            
            alumniList.innerHTML = alumni.map(user => {
                const progress = calculateUserProgressForStudent(user);
                const score = calculateCertificateScoreForStudent(user);
                
                return `
                    <div class="alumni-item">
                        <img src="${user.photo}" alt="${user.name}" class="alumni-photo">
                        <div class="alumni-info">
                            <div class="alumni-name">${user.name}</div>
                            <div class="alumni-details">
                                <strong>Lambar Rajista:</strong> ${user.regNo} | 
                                <strong>Department:</strong> ${user.departmentTitle} | 
                                <strong>Kashi:</strong> ${progress}% | 
                                <strong>Maki:</strong> ${score}/100
                            </div>
                        </div>
                        <div class="alumni-certificate">An Kammala</div>
                    </div>
                `;
            }).join('');
        }

        function calculateCertificateScoreForStudent(user) {
            const points = user.points || 0;
            const totalPossiblePoints = 400; // 40 modules × 10 points each
            
            return Math.min(100, Math.round((points / totalPossiblePoints) * 100));
        }

        // History Functions
        function loadHistory() {
            const historyContainer = document.getElementById('history-content');
            if (!historyContainer) return;
            
            if (!currentUser || !currentUser.learningHistory) {
                historyContainer.innerHTML = '<p>Babu tarihin karatu a yanzu.</p>';
                return;
            }
            
            const historyHTML = currentUser.learningHistory.map(item => `
                <div class="history-item">
                    <div class="history-details">
                        <strong>${item.topic}</strong>
                        <p>${item.date}</p>
                        <p>Lokaci: ${item.duration} minutes</p>
                    </div>
                    <div class="history-actions">
                        <button onclick="reviewTopic('${item.topic}')">Duba Baya</button>
                    </div>
                </div>
            `).join('');
            
            historyContainer.innerHTML = historyHTML;
        }

        function addToHistory(topic, duration) {
            if (!currentUser.learningHistory) {
                currentUser.learningHistory = [];
            }
            
            currentUser.learningHistory.push({
                topic: topic,
                date: new Date().toLocaleString(),
                duration: duration
            });
            
            updateUserProgress();
        }

        // Module Completion Functions
        function checkAndUnlockModules() {
            // This function would check user progress and unlock next modules
            // based on completed modules and study schedule
        }

        function markModuleCompleted(moduleId) {
            if (!currentUser.courses || currentUser.courses.length === 0) return;
            
            const course = currentUser.courses[0];
            const level = currentUser.level;
            const semester = getCurrentSemester();
            
            // Find the course level
            const courseLevel = course.courses.find(c => c.level === level);
            if (!courseLevel) return;
            
            // Mark module as completed
            const semesterData = courseLevel[semester];
            if (!semesterData.modules.includes(moduleId)) {
                semesterData.modules.push(moduleId);
                semesterData.completedModules = semesterData.modules.length;
            }
            
            // Add to history
            addToHistory(`Module ${moduleId}`, 30); // Assuming 30 minutes per module
            
            updateUserProgress();
        }

        function getCurrentSemester() {
            // Simple semester calculation based on current month
            const month = new Date().getMonth();
            return month < 6 ? 'zango1' : 'zango2';
        }

        // Helper Functions
        function calculateUserProgress() {
            if (!currentUser.courses || currentUser.courses.length === 0) return 0;
            
            const course = currentUser.courses[0];
            if (!course.courses) return 0;
            
            const completedModules = course.courses.reduce((sum, c) => 
                sum + (c.zango1.completedModules || 0) + (c.zango2.completedModules || 0), 0);
            
            return Math.round((completedModules / TOTAL_MODULES) * 100);
        }

        function calculateUserProgressForStudent(user) {
            if (!user.courses || user.courses.length === 0) return 0;
            
            const course = user.courses[0];
            if (!course.courses) return 0;
            
            const completedModules = course.courses.reduce((sum, c) => 
                sum + (c.zango1.completedModules || 0) + (c.zango2.completedModules || 0), 0);
            
            return Math.round((completedModules / TOTAL_MODULES) * 100);
        }

        function updateUserProgress() {
            // Update user in storage
            const userIndex = allUsers.findIndex(u => u.regNo === currentUser.regNo);
            if (userIndex !== -1) {
                allUsers[userIndex] = currentUser;
                localStorage.setItem('allUsers', JSON.stringify(allUsers));
            }
            
            // Update dashboard if on dashboard page
            if (document.getElementById('dashboard-page').classList.contains('active')) {
                updateDashboard();
            }
        }

        function translatePage(lang) {
            currentLang = lang;
            document.querySelectorAll('[data-lang]').forEach(element => {
                const key = element.getAttribute('data-lang');
                if (translations[lang][key]) {
                    if (element.tagName === 'INPUT' || element.tagName === 'BUTTON') {
                        element.placeholder = translations[lang][key];
                    } else {
                        element.innerHTML = translations[lang][key];
                    }
                }
            });
        }

        function changeLanguage(lang) {
            currentLang = lang;
            translatePage(lang);
        }

        function logout() {
            currentUser = null;
            localStorage.removeItem('sessionToken');
            showPage('landing-page');
        }

        // Initialize the application
        document.addEventListener('DOMContentLoaded', function() {
            // Initialize faculties
            populateFaculties();
            
            // Check for remembered user
            const rememberedUser = JSON.parse(localStorage.getItem('rememberedUser'));
            if (rememberedUser) {
                document.getElementById('login-regno').value = rememberedUser.regNo;
                document.getElementById('login-password').value = rememberedUser.password;
                document.getElementById('remember-me-checkbox').checked = true;
            }
            
            // Check session
            if (!checkSession()) {
                showPage('landing-page');
            }
            
            // Initialize settings event listeners
            const fontSizeSelect = document.getElementById('font-size-select');
            const fontStyleSelect = document.getElementById('font-style-select');
            const brightnessSlider = document.getElementById('brightness-slider');
            const darkModeToggle = document.getElementById('dark-mode-toggle');
            
            if (fontSizeSelect) {
                fontSizeSelect.addEventListener('change', applyDisplaySettings);
            }
            if (fontStyleSelect) {
                fontStyleSelect.addEventListener('change', applyDisplaySettings);
            }
            if (brightnessSlider) {
                brightnessSlider.addEventListener('input', applyDisplaySettings);
            }
            if (darkModeToggle) {
                darkModeToggle.addEventListener('change', applyDisplaySettings);
            }
            
            // Initialize course date selector
            const courseDateSelect = document.getElementById('course-date-select');
            if (courseDateSelect) {
                // Set minimum date to today
                const today = new Date().toISOString().split('T')[0];
                courseDateSelect.min = today;
                courseDateSelect.value = today;
            }
            
            // Initialize national anthem
            const nationalAnthem = document.getElementById('national-anthem');
            const muteBtn = document.getElementById('mute-anthem');
            
            // Play national anthem on page load
            nationalAnthem.play().catch(e => console.log('Autoplay prevented:', e));
            
            // Toggle mute/unmute
            muteBtn.addEventListener('click', function() {
                if (nationalAnthem.muted) {
                    nationalAnthem.muted = false;
                    muteBtn.textContent = '🔇';
                } else {
                    nationalAnthem.muted = true;
                    muteBtn.textContent = '🔊';
                }
            });
        });

        // Additional helper functions
        function showWallpaperOptions() {
            const options = document.getElementById('wallpaper-options');
            options.style.display = options.style.display === 'none' ? 'grid' : 'none';
        }

        function setWallpaper(url) {
            document.body.classList.add('wallpaper');
            document.body.style.backgroundImage = `url('${url}')`;
            localStorage.setItem('wallpaper', url);
            document.getElementById('wallpaper-options').style.display = 'none';
        }

        function setDailyReminder() {
            if ("Notification" in window) {
                Notification.requestPermission().then(permission => {
                    if (permission === "granted") {
                        alert('An saita tunatarwa ta yau da kullum.');
                    }
                });
            } else {
                alert('Tunatarwa ba ta goyan baya a wannan burauza.');
            }
        }

        function shareLink() {
            if (navigator.share) {
                navigator.share({
                    title: 'Jami\'ar IHAME',
                    text: 'Ka ga dandalin Jami\'ar IHAME don koyon ilimi mai zurfi da Hausa!',
                    url: window.location.href
                });
            } else {
                alert('Raba ba ya goyan baya a wannan burauza. Kwafa hanyar haɗin: ' + window.location.href);
            }
        }

        function showPrivacyPolicy() {
            alert(`Manufar Sirri ta Jami'ar IHAME:
            
1. Bayanan ku za a adana su cikin aminci
2. Ba za a raba bayanan ku da wani ba
3. Kuna da ikon share asusun ku a kowane lokaci
4. Muna amfani da cookies don inganta aiki
5. Za mu sanar da ku idan akwai canje-canje ga manufofinmu`);
        }

        function deleteAccount() {
            if (confirm('Kuna da tabbacin cewa kuna son share asusun ku? Wannan ba zai iya jurewa ba.')) {
                if (currentUser) {
                    allUsers = allUsers.filter(u => u.regNo !== currentUser.regNo);
                    localStorage.setItem('allUsers', JSON.stringify(allUsers));
                    alert('An share asusun ku.');
                    logout();
                }
            }
        }

        function inviteFriend() {
            const message = "Ka ga dandalin Jami'ar IHAME don koyon ilimi mai zurfi da Hausa! " + window.location.href;
            if (navigator.share) {
                navigator.share({
                    title: 'Gayyaci Abokai zuwa Jami\'ar IHAME',
                    text: message
                });
            } else {
                prompt("Kwafa saƙon nan don aika wa abokanka:", message);
            }
        }

        function reportIssue() {
            const issue = prompt("Rubuta matsalar da kake fuskanta ko shawarar da kake da ita:");
            if (issue) {
                alert('Na gode da kai rahoto. Za mu yi bita da shi.');
                // In real implementation, send to admin
            }
        }

        // Calculator Functions
        function showCalculator() {
            document.getElementById('calculator-modal').style.display = 'flex';
        }

        function closeCalculator() {
            document.getElementById('calculator-modal').style.display = 'none';
        }

        function appendToDisplay(value) {
            document.getElementById('calculator-display').value += value;
        }

        function clearDisplay() {
            document.getElementById('calculator-display').value = '';
        }

        function calculate() {
            try {
                const display = document.getElementById('calculator-display');
                display.value = eval(display.value);
            } catch (error) {
                alert('Lissafi ba daidai ba');
                clearDisplay();
            }
        }

        // Scientific calculator functions
        function calculateSquareRoot() {
            const display = document.getElementById('calculator-display');
            try {
                display.value = Math.sqrt(eval(display.value));
            } catch (error) {
                alert('Lissafi ba daidai ba');
            }
        }

        function calculatePower() {
            const display = document.getElementById('calculator-display');
            display.value += '**';
        }

        function calculateSin() {
            const display = document.getElementById('calculator-display');
            try {
                display.value = Math.sin(eval(display.value));
            } catch (error) {
                alert('Lissafi ba daidai ba');
            }
        }

        function calculateCos() {
            const display = document.getElementById('calculator-display');
            try {
                display.value = Math.cos(eval(display.value));
            } catch (error) {
                alert('Lissafi ba daidai ba');
            }
        }

        function calculateTan() {
            const display = document.getElementById('calculator-display');
            try {
                display.value = Math.tan(eval(display.value));
            } catch (error) {
                alert('Lissafi ba daidai ba');
            }
        }

        function calculateLog() {
            const display = document.getElementById('calculator-display');
            try {
                display.value = Math.log10(eval(display.value));
            } catch (error) {
                alert('Lissafi ba daidai ba');
            }
        }

        // Additional scientific calculator functions
        function calculateLn() {
            const display = document.getElementById('calculator-display');
            try {
                display.value = Math.log(eval(display.value));
            } catch (error) {
                alert('Lissafi ba daidai ba');
            }
        }

        function calculateFactorial() {
            const display = document.getElementById('calculator-display');
            try {
                const num = parseInt(eval(display.value));
                if (num < 0) {
                    alert('Ba za a iya lissafin factorial na lamba mara kyau ba');
                    return;
                }
                let result = 1;
                for (let i = 2; i <= num; i++) {
                    result *= i;
                }
                display.value = result;
            } catch (error) {
                alert('Lissafi ba daidai ba');
            }
        }

        function calculatePi() {
            const display = document.getElementById('calculator-display');
            display.value = Math.PI;
        }

        function calculateE() {
            const display = document.getElementById('calculator-display');
            display.value = Math.E;
        }

        function calculatePercentage() {
            const display = document.getElementById('calculator-display');
            try {
                display.value = eval(display.value) / 100;
            } catch (error) {
                alert('Lissafi ba daidai ba');
            }
        }

        function calculateMod() {
            const display = document.getElementById('calculator-display');
            display.value += '%';
        }

        // Currency Converter
        function showCurrencyConverter() {
            document.getElementById('currency-converter-modal').style.display = 'flex';
        }

        function closeCurrencyConverter() {
            document.getElementById('currency-converter-modal').style.display = 'none';
        }

        function convertCurrency() {
            const amount = parseFloat(document.getElementById('currency-amount').value);
            const fromCurrency = document.getElementById('from-currency').value;
            const toCurrency = document.getElementById('to-currency').value;
            
            if (isNaN(amount)) {
                alert('Da fatan za a shigar da adadin kuɗi.');
                return;
            }
            
            // Simple conversion rates (would need to be updated regularly)
            const rates = {
                'NGN': { 'USD': 0.00067, 'EUR': 0.00062, 'GBP': 0.00053, 'NGN': 1 },
                'USD': { 'NGN': 1500, 'EUR': 0.92, 'GBP': 0.79, 'USD': 1 },
                'EUR': { 'NGN': 1620, 'USD': 1.08, 'GBP': 0.86, 'EUR': 1 },
                'GBP': { 'NGN': 1900, 'USD': 1.27, 'EUR': 1.16, 'GBP': 1 }
            };
            
            const convertedAmount = amount * rates[fromCurrency][toCurrency];
            document.getElementById('converted-amount').value = convertedAmount.toFixed(2);
        }

        // Measurement Converter  
        function showMeasurementConverter() {
            document.getElementById('measurement-converter-modal').style.display = 'flex';
        }

        function closeMeasurementConverter() {
            document.getElementById('measurement-converter-modal').style.display = 'none';
        }

        function selectMeasurementType(type) {
            // Remove active class from all buttons
            document.querySelectorAll('.measurement-type-btn').forEach(btn => {
                btn.classList.remove('active');
            });
            
            // Add active class to clicked button
            event.target.classList.add('active');
            
            // Show selected converter, hide others
            document.getElementById('length-converter').style.display = type === 'length' ? 'block' : 'none';
            document.getElementById('weight-converter').style.display = type === 'weight' ? 'block' : 'none';
            document.getElementById('temperature-converter').style.display = type === 'temperature' ? 'block' : 'none';
        }

        function convertLength() {
            const value = parseFloat(document.getElementById('length-value').value);
            const fromUnit = document.getElementById('from-length').value;
            const toUnit = document.getElementById('to-length').value;
            
            if (isNaN(value)) {
                alert('Da fatan za a shigar da adadin.');
                return;
            }
            
            // Conversion factors to meters
            const toMeter = {
                'meter': 1,
                'centimeter': 0.01,
                'millimeter': 0.001,
                'kilometer': 1000,
                'inch': 0.0254,
                'foot': 0.3048,
                'yard': 0.9144,
                'mile': 1609.34
            };
            
            const valueInMeters = value * toMeter[fromUnit];
            const convertedValue = valueInMeters / toMeter[toUnit];
            
            document.getElementById('converted-length').value = convertedValue.toFixed(4);
        }

        function convertWeight() {
            const value = parseFloat(document.getElementById('weight-value').value);
            const fromUnit = document.getElementById('from-weight').value;
            const toUnit = document.getElementById('to-weight').value;
            
            if (isNaN(value)) {
                alert('Da fatan za a shigar da adadin.');
                return;
            }
            
            // Conversion factors to kilograms
            const toKilogram = {
                'kilogram': 1,
                'gram': 0.001,
                'milligram': 0.000001,
                'pound': 0.453592,
                'ounce': 0.0283495
            };
            
            const valueInKilograms = value * toKilogram[fromUnit];
            const convertedValue = valueInKilograms / toKilogram[toUnit];
            
            document.getElementById('converted-weight').value = convertedValue.toFixed(4);
        }

        function convertTemperature() {
            const value = parseFloat(document.getElementById('temperature-value').value);
            const fromUnit = document.getElementById('from-temperature').value;
            const toUnit = document.getElementById('to-temperature').value;
            
            if (isNaN(value)) {
                alert('Da fatan za a shigar da adadin.');
                return;
            }
            
            let convertedValue;
            
            if (fromUnit === 'celsius') {
                if (toUnit === 'fahrenheit') {
                    convertedValue = (value * 9/5) + 32;
                } else if (toUnit === 'kelvin') {
                    convertedValue = value + 273.15;
                } else {
                    convertedValue = value;
                }
            } else if (fromUnit === 'fahrenheit') {
                if (toUnit === 'celsius') {
                    convertedValue = (value - 32) * 5/9;
                } else if (toUnit === 'kelvin') {
                    convertedValue = (value - 32) * 5/9 + 273.15;
                } else {
                    convertedValue = value;
                }
            } else if (fromUnit === 'kelvin') {
                if (toUnit === 'celsius') {
                    convertedValue = value - 273.15;
                } else if (toUnit === 'fahrenheit') {
                    convertedValue = (value - 273.15) * 9/5 + 32;
                } else {
                    convertedValue = value;
                }
            }
            
            document.getElementById('converted-temperature').value = convertedValue.toFixed(2);
        }

        function showResearchTools() {
            const choice = prompt("Zaɓi kayan aikin bincike:\n1. Calculator\n2. Masu Canza Kudi\n3. Masu Auna Ma'auni");
            
            switch(choice) {
                case '1':
                    showCalculator();
                    break;
                case '2':
                    showCurrencyConverter();
                    break;
                case '3':
                    showMeasurementConverter();
                    break;
            }
        }

        // WhatsApp Integration
        function openWhatsApp() {
            const phone = "2347071992912";
            const message = "Ina son lambar rajista don Jami'ar IHAME";
            window.open(`https://wa.me/${phone}?text=${encodeURIComponent(message)}`, '_blank');
        }

        function sendPaymentProof() {
            const phone = "2347071992912";
            const message = `Ina aika hujjar biyan kuɗin karatu na Jami'ar IHAME. Bayanai:\n- Suna: ${document.getElementById('reg-name').value}\n- Email: ${document.getElementById('reg-email').value}\n- Faculty: ${document.getElementById('reg-faculty').value}\n- Department: ${document.getElementById('reg-department').value}`;
            window.open(`https://wa.me/${phone}?text=${encodeURIComponent(message)}`, '_blank');
        }

        function upgradeToPaid() {
            if (confirm('Kuna son canzawa daga karatun wucin gadi zuwa cikakken karatu?')) {
                showPage('register-page');
                document.getElementById('paid-tier-btn').click();
            }
        }

        // Admin Student Management
        function viewStudentDetails(regNo) {
            const student = allUsers.find(u => u.regNo === regNo);
            if (student) {
                // Store student for details page
                localStorage.setItem('currentStudentView', JSON.stringify(student));
                showPage('student-details-page');
                
                // Update student details display
                setTimeout(() => {
                    if (document.getElementById('student-regno-display')) {
                        document.getElementById('student-regno-display').textContent = student.regNo;
                        document.getElementById('student-name-display').textContent = student.name;
                        document.getElementById('student-email-display').textContent = student.email;
                        document.getElementById('student-faculty-display').textContent = student.faculty;
                        document.getElementById('student-department-display').textContent = student.departmentTitle;
                        document.getElementById('student-level-display').textContent = student.level;
                        document.getElementById('student-tier-display').textContent = student.paymentTier === 'free' ? 'Karatun Wucin Gadi' : 'Cikakken Karatu';
                        document.getElementById('student-pic-display').src = student.photo;
                        
                        // Update progress
                        const progress = calculateUserProgressForStudent(student);
                        document.getElementById('student-progress-display').textContent = `${progress}%`;
                        
                        // Update certificate score
                        const score = calculateCertificateScoreForStudent(student);
                        document.getElementById('student-certificate-score').textContent = `${score}/100`;
                        
                        // Update tokens display
                        if (student.tokens) {
                            document.getElementById('student-tokens-display').textContent = student.tokens.remaining;
                            document.getElementById('student-lessons-today').textContent = `${student.tokens.lessonsToday}/${student.tokens.maxLessons}`;
                        } else {
                            document.getElementById('student-tokens-display').textContent = '0';
                            document.getElementById('student-lessons-today').textContent = '0/1';
                        }
                    }
                }, 100);
            }
        }

        function deleteStudent(regNo) {
            if (confirm('Kuna da tabbacin cewa kuna son share wannan dalibi?')) {
                allUsers = allUsers.filter(u => u.regNo !== regNo);
                localStorage.setItem('allUsers', JSON.stringify(allUsers));
                alert('An share dalibi.');
                loadStudentList();
                loadAdminStats();
            }
        }

        function resetStudentTokens() {
            const student = JSON.parse(localStorage.getItem('currentStudentView'));
            if (student) {
                const maxTokens = student.paymentTier === 'free' ? TOKENS_FREE_TIER : TOKENS_STANDARD_TIER;
                
                // Update student tokens
                const studentIndex = allUsers.findIndex(u => u.regNo === student.regNo);
                if (studentIndex !== -1) {
                    allUsers[studentIndex].tokens = {
                        date: new Date().toDateString(),
                        remaining: maxTokens,
                        max: maxTokens,
                        lessonsToday: 0,
                        maxLessons: LESSONS_PER_DAY,
                        questionsToday: 0,
                        quizzesToday: 0
                    };
                    
                    localStorage.setItem('allUsers', JSON.stringify(allUsers));
                    alert('An sabunta tokens na dalibi.');
                    
                    // Update display
                    document.getElementById('student-tokens-display').textContent = maxTokens;
                    document.getElementById('student-lessons-today').textContent = `0/${LESSONS_PER_DAY}`;
                }
            }
        }

        // Placeholder functions for other admin operations
        function loadModuleManagement() {}
        function loadNotifications() {}
        function loadCoursesList() {}
        function loadModules() {}
        function loadRewards() {}
        function loadVocabulary() {}
        function loadLibrary() {}
        function initializePublicReading() {}
        function initializeAlertTabs() {}
        function initializeFontSettings() {}
        function initializeDarkModeSettings() {}
        function initializeCertificatePublicView() {}
        function updateNotificationBadge() {}
        function loadDailyQuiz() {}
        function previewProfilePic(event) {
            const input = event.target;
            const reader = new FileReader();
            
            reader.onload = function() {
                const img = document.getElementById('profile-pic-preview');
                img.src = reader.result;
            };
            
            if (input.files && input.files[0]) {
                reader.readAsDataURL(input.files[0]);
            }
        }
        function sendNotificationToAll() {
            const message = document.getElementById('notification-message').value;
            if (message) {
                alert(`An aika sanarwa ga dukkan dalibai: "${message}"`);
                document.getElementById('notification-message').value = '';
            }
        }
        function sendNotificationToStudent() {
            const message = document.getElementById('student-notification-message').value;
            if (message) {
                alert(`An aika sanarwa ga dalibi: "${message}"`);
                document.getElementById('student-notification-message').value = '';
            }
        }
        function enableStudentEdit() {
            alert('Wannan fasalin yana cikin ci gaba...');
        }
        function resetStudentPassword() {
            const student = JSON.parse(localStorage.getItem('currentStudentView'));
            if (student) {
                const newPassword = prompt("Shigar da sabuwar kalmar sirri:");
                if (newPassword) {
                    const studentIndex = allUsers.findIndex(u => u.regNo === student.regNo);
                    if (studentIndex !== -1) {
                        allUsers[studentIndex].password = newPassword;
                        localStorage.setItem('allUsers', JSON.stringify(allUsers));
                        alert('An canza kalmar sirrin dalibi.');
                    }
                }
            }
        }
        function changeStudentTier() {
            const student = JSON.parse(localStorage.getItem('currentStudentView'));
            if (student) {
                const newTier = confirm("Kuna son canza dalibi zuwa Cikakken Karatu?");
                if (newTier) {
                    const studentIndex = allUsers.findIndex(u => u.regNo === student.regNo);
                    if (studentIndex !== -1) {
                        allUsers[studentIndex].paymentTier = 'paid';
                        localStorage.setItem('allUsers', JSON.stringify(allUsers));
                        alert('An canza nau\'in karatu na dalibi zuwa Cikakken Karatu.');
                        
                        // Update display
                        document.getElementById('student-tier-display').textContent = 'Cikakken Karatu';
                    }
                }
            }
        }
        function loadCoursesForDate() {}
        function loadMonitorChat() {}
        function sendAdminMessage() {}
        function addNewModule() {}
        function loadStudentProgress() {}
        function addQuizQuestion() {}
        function loadExamResults() {}
        function uploadLibraryDocument() {}
        function likeMessage(id) {}
        function editMessage(id) {}
        function deleteMessage(id) {}
        function forwardMessage(id) {}
        function reviewTopic(topic) {}
    </script>
</body>
</html>
