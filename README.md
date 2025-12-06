<!DOCTYPE html>
<html ng-app="healthRecordApp">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Smart Health Record System</title>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/angular.js/1.8.3/angular.min.js"></script>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, sans-serif;
            background: linear-gradient(135deg, #e0f2fe 0%, #c7d2fe 100%);
            min-height: 100vh;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
        }

        /* Navigation */
        .navbar {
            background: white;
            box-shadow: 0 2px 8px rgba(0,0,0,0.1);
            padding: 16px 0;
            margin-bottom: 30px;
        }

        .navbar-content {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .logo {
            display: flex;
            align-items: center;
            font-size: 24px;
            font-weight: bold;
            color: #1f2937;
        }

        .logo span {
            color: #ef4444;
            margin-right: 8px;
        }

        .nav-links {
            display: flex;
            gap: 20px;
            align-items: center;
        }

        .nav-links button {
            background: none;
            border: none;
            padding: 8px 16px;
            cursor: pointer;
            color: #4b5563;
            font-size: 16px;
            transition: color 0.3s;
        }

        .nav-links button:hover {
            color: #2563eb;
        }

        .nav-links button.active {
            color: #2563eb;
            font-weight: 600;
        }

        /* Login/Signup */
        .auth-container {
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            padding: 20px;
        }

        .auth-card {
            background: white;
            border-radius: 16px;
            box-shadow: 0 10px 40px rgba(0,0,0,0.15);
            padding: 40px;
            width: 100%;
            max-width: 450px;
        }

        .auth-header {
            text-align: center;
            margin-bottom: 30px;
        }

        .auth-header h1 {
            font-size: 32px;
            color: #1f2937;
            margin-bottom: 8px;
        }

        .auth-header p {
            color: #6b7280;
            font-size: 14px;
        }

        .form-group {
            margin-bottom: 20px;
        }

        .form-group label {
            display: block;
            margin-bottom: 8px;
            font-weight: 600;
            color: #374151;
        }

        input, select, textarea {
            width: 100%;
            padding: 12px;
            border: 1px solid #d1d5db;
            border-radius: 8px;
            font-size: 14px;
            transition: border-color 0.3s;
        }

        input:focus, select:focus, textarea:focus {
            outline: none;
            border-color: #2563eb;
            box-shadow: 0 0 0 3px rgba(37, 99, 235, 0.1);
        }

        .btn {
            width: 100%;
            padding: 14px;
            border: none;
            border-radius: 8px;
            font-size: 16px;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s;
        }

        .btn-primary {
            background: #2563eb;
            color: white;
        }

        .btn-primary:hover {
            background: #1d4ed8;
        }

        .btn-secondary {
            background: #f3f4f6;
            color: #374151;
        }

        .btn-secondary:hover {
            background: #e5e7eb;
        }

        .btn-danger {
            background: #ef4444;
            color: white;
            padding: 10px 20px;
        }

        .btn-danger:hover {
            background: #dc2626;
        }

        .demo-info {
            margin-top: 20px;
            padding: 16px;
            background: #dbeafe;
            border-radius: 8px;
            font-size: 13px;
        }

        .demo-info p {
            margin-bottom: 4px;
        }

        /* Dashboard */
        .dashboard-header {
            margin-bottom: 30px;
        }

        .dashboard-header h2 {
            font-size: 32px;
            color: #1f2937;
        }

        .record-card {
            background: white;
            border-radius: 12px;
            box-shadow: 0 2px 8px rgba(0,0,0,0.1);
            padding: 24px;
            margin-bottom: 20px;
        }

        .record-header {
            display: flex;
            justify-content: space-between;
            align-items: start;
            margin-bottom: 16px;
        }

        .record-title h3 {
            font-size: 20px;
            color: #1f2937;
            margin-bottom: 4px;
        }

        .record-type {
            color: #6b7280;
            font-size: 13px;
            text-transform: uppercase;
        }

        .record-actions {
            display: flex;
            gap: 8px;
        }

        .icon-btn {
            padding: 8px;
            border: none;
            border-radius: 6px;
            cursor: pointer;
            transition: all 0.3s;
        }

        .icon-btn.view {
            background: #dbeafe;
            color: #2563eb;
        }

        .icon-btn.download {
            background: #d1fae5;
            color: #059669;
        }

        .record-description {
            color: #4b5563;
            margin-bottom: 16px;
            line-height: 1.6;
        }

        .record-date {
            color: #6b7280;
            font-size: 14px;
            margin-bottom: 16px;
        }

        .share-section {
            border-top: 1px solid #e5e7eb;
            padding-top: 16px;
        }

        .share-section p {
            font-weight: 600;
            color: #374151;
            font-size: 14px;
            margin-bottom: 8px;
        }

        .share-controls {
            display: flex;
            gap: 8px;
            margin-bottom: 12px;
        }

        .share-controls input {
            flex: 1;
        }

        .share-controls button {
            padding: 10px 20px;
            background: #2563eb;
            color: white;
            border: none;
            border-radius: 6px;
            cursor: pointer;
            font-size: 14px;
        }

        .share-controls button:hover {
            background: #1d4ed8;
        }

        .shared-list {
            margin-top: 12px;
        }

        .shared-item {
            display: flex;
            justify-content: space-between;
            align-items: center;
            background: #f9fafb;
            padding: 8px 12px;
            border-radius: 6px;
            margin-top: 8px;
        }

        .shared-item span {
            color: #374151;
            font-size: 14px;
        }

        .shared-item button {
            background: none;
            border: none;
            color: #ef4444;
            cursor: pointer;
            font-size: 13px;
        }

        .shared-item button:hover {
            color: #dc2626;
            text-decoration: underline;
        }

        .empty-state {
            background: white;
            border-radius: 12px;
            box-shadow: 0 2px 8px rgba(0,0,0,0.1);
            padding: 60px;
            text-align: center;
        }

        .empty-state svg {
            width: 80px;
            height: 80px;
            color: #d1d5db;
            margin-bottom: 20px;
        }

        .empty-state p {
            color: #6b7280;
            font-size: 18px;
            margin-bottom: 20px;
        }

        /* Emergency Info */
        .alert-box {
            background: #fee2e2;
            border-left: 4px solid #ef4444;
            padding: 16px;
            border-radius: 8px;
            margin-bottom: 30px;
        }

        .alert-box h3 {
            color: #991b1b;
            font-size: 18px;
            margin-bottom: 4px;
        }

        .alert-box p {
            color: #dc2626;
            font-size: 14px;
        }

        .info-section {
            margin-bottom: 24px;
            padding-bottom: 24px;
            border-bottom: 1px solid #e5e7eb;
        }

        .info-section:last-child {
            border-bottom: none;
        }

        .info-section h3 {
            color: #1f2937;
            font-size: 18px;
            margin-bottom: 12px;
        }

        .info-section p {
            color: #4b5563;
            font-size: 16px;
        }

        .blood-group {
            font-size: 36px !important;
            font-weight: bold;
            color: #ef4444;
        }

        .tip-box {
            background: #dbeafe;
            padding: 16px;
            border-radius: 8px;
            margin-top: 30px;
        }

        .tip-box p {
            color: #1e40af;
            font-size: 14px;
        }

        /* Upload */
        .upload-area {
            border: 2px dashed #d1d5db;
            border-radius: 8px;
            padding: 40px;
            text-align: center;
            cursor: pointer;
            transition: border-color 0.3s;
            margin-bottom: 24px;
        }

        .upload-area:hover {
            border-color: #2563eb;
        }

        .upload-area svg {
            width: 64px;
            height: 64px;
            color: #9ca3af;
            margin-bottom: 12px;
        }

        .upload-area p {
            color: #6b7280;
            margin-bottom: 4px;
        }

        .upload-area .note {
            color: #9ca3af;
            font-size: 13px;
        }
    </style>
</head>
<body ng-controller="MainController">

    <!-- Login View -->
    <div ng-if="state.view === 'login'" class="auth-container">
        <div class="auth-card">
            <div class="auth-header">
                <h1><span>❤</span> HealthRecord</h1>
                <p>Secure Medical Records Management</p>
            </div>

            <div class="form-group">
                <input type="email" placeholder="Email" ng-model="authForm.email">
            </div>

            <div class="form-group">
                <input type="password" placeholder="Password" ng-model="authForm.password" ng-keypress="$event.keyCode === 13 && login()">
            </div>

            <button class="btn btn-primary" ng-click="login()">Login</button>
            <button class="btn btn-secondary" style="margin-top: 10px;" ng-click="state.view = 'signup'">Create Account</button>

            <div class="demo-info">
                <p><strong>Demo Accounts:</strong></p>
                <p>Patient: patient@demo.com / patient123</p>
                <p>Doctor: doctor@demo.com / doctor123</p>
            </div>
        </div>
    </div>

    <!-- Signup View -->
    <div ng-if="state.view === 'signup'" class="auth-container">
        <div class="auth-card" style="max-height: 90vh; overflow-y: auto;">
            <div class="auth-header">
                <h1>Create Account</h1>
            </div>

            <div class="form-group">
                <input type="text" placeholder="Full Name" ng-model="authForm.name">
            </div>

            <div class="form-group">
                <input type="email" placeholder="Email" ng-model="authForm.email">
            </div>

            <div class="form-group">
                <input type="password" placeholder="Password" ng-model="authForm.password">
            </div>

            <div class="form-group">
                <select ng-model="authForm.role">
                    <option value="patient">Patient</option>
                    <option value="doctor">Doctor</option>
                </select>
            </div>

            <div ng-if="authForm.role === 'patient'">
                <div class="form-group">
                    <input type="text" placeholder="Blood Group (e.g., O+)" ng-model="authForm.bloodGroup">
                </div>

                <div class="form-group">
                    <input type="text" placeholder="Allergies (if any)" ng-model="authForm.allergies">
                </div>

                <div class="form-group">
                    <input type="tel" placeholder="Emergency Contact" ng-model="authForm.emergencyContact">
                </div>
            </div>

            <button class="btn btn-primary" ng-click="signup()">Sign Up</button>
            <button class="btn btn-secondary" style="margin-top: 10px;" ng-click="state.view = 'login'">Back to Login</button>
        </div>
    </div>

    <!-- Patient Dashboard -->
    <div ng-if="state.view === 'dashboard'">
        <div class="navbar">
            <div class="navbar-content">
                <div class="logo">
                    <span>❤</span> HealthRecord
                </div>
                <div class="nav-links">
                    <button ng-class="{active: state.view === 'dashboard'}" ng-click="state.view = 'dashboard'">Dashboard</button>
                    <button ng-click="state.view = 'upload'">Upload</button>
                    <button ng-click="state.view = 'emergency'">Emergency Info</button>
                    <span>{{currentUser.name}}</span>
                    <button class="btn btn-danger" ng-click="logout()">Logout</button>
                </div>
            </div>
        </div>

        <div class="container">
            <div class="dashboard-header">
                <h2>My Medical Records</h2>
            </div>

            <div ng-if="myRecords.length > 0">
                <div class="record-card" ng-repeat="record in myRecords">
                    <div class="record-header">
                        <div class="record-title">
                            <h3>{{record.title}}</h3>
                            <p class="record-type">{{record.type.replace('_', ' ').toUpperCase()}}</p>
                        </div>
                        <div class="record-actions">
                            <button class="icon-btn view">👁</button>
                            <button class="icon-btn download">⬇</button>
                        </div>
                    </div>

                    <p class="record-description">{{record.description}}</p>
                    <p class="record-date">📅 {{record.date}}</p>

                    <div class="share-section">
                        <p>Share with Doctor:</p>
                        <div class="share-controls">
                            <input type="email" placeholder="doctor@example.com" ng-model="record.shareEmail">
                            <button ng-click="shareAccess(record.id, record.shareEmail)">Grant Access</button>
                        </div>

                        <div class="shared-list">
                            <div class="shared-item" ng-repeat="access in getSharedAccess(record.id)">
                                <span>✓ {{getDoctor(access.doctorId).name}}</span>
                                <button ng-click="revokeAccess(record.id, access.doctorId)">Revoke</button>
                            </div>
                        </div>
                    </div>
                </div>
            </div>

            <div ng-if="myRecords.length === 0" class="empty-state">
                <p>📄</p>
                <p>No records found. Upload your first medical record!</p>
                <button class="btn btn-primary" style="max-width: 200px; margin: 20px auto 0;" ng-click="state.view = 'upload'">Upload Record</button>
            </div>
        </div>
    </div>

    <!-- Upload View -->
    <div ng-if="state.view === 'upload'">
        <div class="navbar">
            <div class="navbar-content">
                <div class="logo">
                    <span>❤</span> HealthRecord
                </div>
                <div class="nav-links">
                    <button ng-click="state.view = 'dashboard'">Dashboard</button>
                    <button ng-class="{active: state.view === 'upload'}" ng-click="state.view = 'upload'">Upload</button>
                    <button ng-click="state.view = 'emergency'">Emergency Info</button>
                    <span>{{currentUser.name}}</span>
                    <button class="btn btn-danger" ng-click="logout()">Logout</button>
                </div>
            </div>
        </div>

        <div class="container" style="max-width: 800px;">
            <div class="dashboard-header">
                <h2>Upload Medical Record</h2>
            </div>

            <div class="record-card">
                <div class="form-group">
                    <label>Record Title</label>
                    <input type="text" ng-model="recordForm.title">
                </div>

                <div class="form-group">
                    <label>Record Type</label>
                    <select ng-model="recordForm.type">
                        <option value="lab_report">Lab Report</option>
                        <option value="prescription">Prescription</option>
                        <option value="imaging">Imaging (X-Ray/MRI/CT)</option>
                        <option value="consultation">Consultation Notes</option>
                        <option value="vaccination">Vaccination Record</option>
                        <option value="other">Other</option>
                    </select>
                </div>

                <div class="form-group">
                    <label>Description</label>
                    <textarea rows="4" ng-model="recordForm.description"></textarea>
                </div>

                <div class="form-group">
                    <label>Date</label>
                    <input type="date" ng-model="recordForm.date">
                </div>

                <div class="form-group">
                    <label>Upload File (PDF/Image)</label>
                    <div class="upload-area">
                        <p>📤</p>
                        <p>Click to upload or drag and drop</p>
                        <p class="note">PDF, JPG, PNG up to 10MB</p>
                    </div>
                </div>

                <button class="btn btn-primary" ng-click="uploadRecord()">➕ Upload Record</button>
            </div>
        </div>
    </div>

    <!-- Emergency Info View -->
    <div ng-if="state.view === 'emergency'">
        <div class="navbar">
            <div class="navbar-content">
                <div class="logo">
                    <span>❤</span> HealthRecord
                </div>
                <div class="nav-links">
                    <button ng-click="state.view = 'dashboard'">Dashboard</button>
                    <button ng-click="state.view = 'upload'">Upload</button>
                    <button ng-class="{active: state.view === 'emergency'}" ng-click="state.view = 'emergency'">Emergency Info</button>
                    <span>{{currentUser.name}}</span>
                    <button class="btn btn-danger" ng-click="logout()">Logout</button>
                </div>
            </div>
        </div>

        <div class="container" style="max-width: 800px;">
            <div class="alert-box">
                <h3>⚠ Emergency Medical Information</h3>
                <p>Critical information for first responders</p>
            </div>

            <div class="record-card">
                <div class="info-section">
                    <h3>Patient Information</h3>
                    <p><strong>Name:</strong> {{currentUser.name}}</p>
                </div>

                <div class="info-section">
                    <h3>🩸 Blood Group</h3>
                    <p class="blood-group">{{currentUser.bloodGroup || 'Not sp            margin-right: 8px;
        }

        .nav-links {
            display: flex;
            gap: 20px;
            align-items: center;
        }

        .nav-links button {
            background: none;
            border: none;
            padding: 8px 16px;
            cursor: pointer;
            color: #4b5563;
            font-size: 16px;
            transition: color 0.3s;
        }

        .nav-links button:hover {
            color: #2563eb;
        }

        .nav-links button.active {
            color: #2563eb;
            font-weight: 600;
        }

        /* Login/Signup */
        .auth-container {
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            padding: 20px;
        }

        .auth-card {
            background: white;
            border-radius: 16px;
            box-shadow: 0 10px 40px rgba(0,0,0,0.15);
            padding: 40px;
            width: 100%;
            max-width: 450px;
        }

        .auth-header {
            text-align: center;
            margin-bottom: 30px;
        }

        .auth-header h1 {
            font-size: 32px;
            color: #1f2937;
            margin-bottom: 8px;
        }

        .auth-header p {
            color: #6b7280;
            font-size: 14px;
        }

        .form-group {
            margin-bottom: 20px;
        }

        .form-group label {
            display: block;
            margin-bottom: 8px;
            font-weight: 600;
            color: #374151;
        }

        input, select, textarea {
            width: 100%;
            padding: 12px;
            border: 1px solid #d1d5db;
            border-radius: 8px;
            font-size: 14px;
            transition: border-color 0.3s;
        }

        input:focus, select:focus, textarea:focus {
            outline: none;
            border-color: #2563eb;
            box-shadow: 0 0 0 3px rgba(37, 99, 235, 0.1);
        }

        .btn {
            width: 100%;
            padding: 14px;
            border: none;
            border-radius: 8px;
            font-size: 16px;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s;
        }

        .btn-primary {
            background: #2563eb;
            color: white;
        }

        .btn-primary:hover {
            background: #1d4ed8;
        }

        .btn-secondary {
            background: #f3f4f6;
            color: #374151;
        }

        .btn-secondary:hover {
            background: #e5e7eb;
        }

        .btn-danger {
            background: #ef4444;
            color: white;
            padding: 10px 20px;
        }

        .btn-danger:hover {
            background: #dc2626;
        }

        .demo-info {
            margin-top: 20px;
            padding: 16px;
            background: #dbeafe;
            border-radius: 8px;
            font-size: 13px;
        }

        .demo-info p {
            margin-bottom: 4px;
        }

        /* Dashboard */
        .dashboard-header {
            margin-bottom: 30px;
        }

        .dashboard-header h2 {
            font-size: 32px;
            color: #1f2937;
        }

        .record-card {
            background: white;
            border-radius: 12px;
            box-shadow: 0 2px 8px rgba(0,0,0,0.1);
            padding: 24px;
            margin-bottom: 20px;
        }

        .record-header {
            display: flex;
            justify-content: space-between;
            align-items: start;
            margin-bottom: 16px;
        }

        .record-title h3 {
            font-size: 20px;
            color: #1f2937;
            margin-bottom: 4px;
        }

        .record-type {
            color: #6b7280;
            font-size: 13px;
            text-transform: uppercase;
        }

        .record-actions {
            display: flex;
            gap: 8px;
        }

        .icon-btn {
            padding: 8px;
            border: none;
            border-radius: 6px;
            cursor: pointer;
            transition: all 0.3s;
        }

        .icon-btn.view {
            background: #dbeafe;
            color: #2563eb;
        }

        .icon-btn.download {
            background: #d1fae5;
            color: #059669;
        }

        .record-description {
            color: #4b5563;
            margin-bottom: 16px;
            line-height: 1.6;
        }

        .record-date {
            color: #6b7280;
            font-size: 14px;
            margin-bottom: 16px;
        }

        .share-section {
            border-top: 1px solid #e5e7eb;
            padding-top: 16px;
        }

        .share-section p {
            font-weight: 600;
            color: #374151;
            font-size: 14px;
            margin-bottom: 8px;
        }

        .share-controls {
            display: flex;
            gap: 8px;
            margin-bottom: 12px;
        }

        .share-controls input {
            flex: 1;
        }

        .share-controls button {
            padding: 10px 20px;
            background: #2563eb;
            color: white;
            border: none;
            border-radius: 6px;
            cursor: pointer;
            font-size: 14px;
        }

        .share-controls button:hover {
            background: #1d4ed8;
        }

        .shared-list {
            margin-top: 12px;
        }

        .shared-item {
            display: flex;
            justify-content: space-between;
            align-items: center;
            background: #f9fafb;
            padding: 8px 12px;
            border-radius: 6px;
            margin-top: 8px;
        }

        .shared-item span {
            color: #374151;
            font-size: 14px;
        }

        .shared-item button {
            background: none;
            border: none;
            color: #ef4444;
            cursor: pointer;
            font-size: 13px;
        }

        .shared-item button:hover {
            color: #dc2626;
            text-decoration: underline;
        }

        .empty-state {
            background: white;
            border-radius: 12px;
            box-shadow: 0 2px 8px rgba(0,0,0,0.1);
            padding: 60px;
            text-align: center;
        }

        .empty-state svg {
            width: 80px;
            height: 80px;
            color: #d1d5db;
            margin-bottom: 20px;
        }

        .empty-state p {
            color: #6b7280;
            font-size: 18px;
            margin-bottom: 20px;
        }

        /* Emergency Info */
        .alert-box {
            background: #fee2e2;
            border-left: 4px solid #ef4444;
            padding: 16px;
            border-radius: 8px;
            margin-bottom: 30px;
        }

        .alert-box h3 {
            color: #991b1b;
            font-size: 18px;
            margin-bottom: 4px;
        }

        .alert-box p {
            color: #dc2626;
            font-size: 14px;
        }

        .info-section {
            margin-bottom: 24px;
            padding-bottom: 24px;
            border-bottom: 1px solid #e5e7eb;
        }

        .info-section:last-child {
            border-bottom: none;
        }

        .info-section h3 {
            color: #1f2937;
            font-size: 18px;
            margin-bottom: 12px;
        }

        .info-section p {
            color: #4b5563;
            font-size: 16px;
        }

        .blood-group {
            font-size: 36px !important;
            font-weight: bold;
            color: #ef4444;
        }

        .tip-box {
            background: #dbeafe;
            padding: 16px;
            border-radius: 8px;
            margin-top: 30px;
        }

        .tip-box p {
            color: #1e40af;
            font-size: 14px;
        }

        /* Upload */
        .upload-area {
            border: 2px dashed #d1d5db;
            border-radius: 8px;
            padding: 40px;
            text-align: center;
            cursor: pointer;
            transition: border-color 0.3s;
            margin-bottom: 24px;
        }

        .upload-area:hover {
            border-color: #2563eb;
        }

        .upload-area svg {
            width: 64px;
            height: 64px;
            color: #9ca3af;
            margin-bottom: 12px;
        }

        .upload-area p {
            color: #6b7280;
            margin-bottom: 4px;
        }

        .upload-area .note {
            color: #9ca3af;
            font-size: 13px;
        }
    </style>
</head>
<body ng-controller="MainController">

    <!-- Login View -->
    <div ng-if="view === 'login'" class="auth-container">
        <div class="auth-card">
            <div class="auth-header">
                <h1><span>❤</span> HealthRecord</h1>
                <p>Secure Medical Records Management</p>
            </div>

            <div class="form-group">
                <input type="email" placeholder="Email" ng-model="authForm.email">
            </div>

            <div class="form-group">
                <input type="password" placeholder="Password" ng-model="authForm.password" ng-keypress="$event.keyCode === 13 && login()">
            </div>

            <button class="btn btn-primary" ng-click="login()">Login</button>
            <button class="btn btn-secondary" style="margin-top: 10px;" ng-click="view = 'signup'">Create Account</button>

            <div class="demo-info">
                <p><strong>Demo Accounts:</strong></p>
                <p>Patient: patient@demo.com / patient123</p>
                <p>Doctor: doctor@demo.com / doctor123</p>
            </div>
        </div>
    </div>

    <!-- Signup View -->
    <div ng-if="view === 'signup'" class="auth-container">
        <div class="auth-card" style="max-height: 90vh; overflow-y: auto;">
            <div class="auth-header">
                <h1>Create Account</h1>
            </div>

            <div class="form-group">
                <input type="text" placeholder="Full Name" ng-model="authForm.name">
            </div>

            <div class="form-group">
                <input type="email" placeholder="Email" ng-model="authForm.email">
            </div>

            <div class="form-group">
                <input type="password" placeholder="Password" ng-model="authForm.password">
            </div>

            <div class="form-group">
                <select ng-model="authForm.role">
                    <option value="patient">Patient</option>
                    <option value="doctor">Doctor</option>
                </select>
            </div>

            <div ng-if="authForm.role === 'patient'">
                <div class="form-group">
                    <input type="text" placeholder="Blood Group (e.g., O+)" ng-model="authForm.bloodGroup">
                </div>

                <div class="form-group">
                    <input type="text" placeholder="Allergies (if any)" ng-model="authForm.allergies">
                </div>

                <div class="form-group">
                    <input type="tel" placeholder="Emergency Contact" ng-model="authForm.emergencyContact">
                </div>
            </div>

            <button class="btn btn-primary" ng-click="signup()">Sign Up</button>
            <button class="btn btn-secondary" style="margin-top: 10px;" ng-click="view = 'login'">Back to Login</button>
        </div>
    </div>

    <!-- Patient Dashboard -->
    <div ng-if="view === 'dashboard'">
        <div class="navbar">
            <div class="navbar-content">
                <div class="logo">
                    <span>❤</span> HealthRecord
                </div>
                <div class="nav-links">
                    <button ng-class="{active: view === 'dashboard'}" ng-click="view = 'dashboard'">Dashboard</button>
                    <button ng-click="view = 'upload'">Upload</button>
                    <button ng-click="view = 'emergency'">Emergency Info</button>
                    <span>{{currentUser.name}}</span>
                    <button class="btn btn-danger" ng-click="logout()">Logout</button>
                </div>
            </div>
        </div>

        <div class="container">
            <div class="dashboard-header">
                <h2>My Medical Records</h2>
            </div>

            <div ng-if="myRecords.length > 0">
                <div class="record-card" ng-repeat="record in myRecords">
                    <div class="record-header">
                        <div class="record-title">
                            <h3>{{record.title}}</h3>
                            <p class="record-type">{{record.type.replace('_', ' ').toUpperCase()}}</p>
                        </div>
                        <div class="record-actions">
                            <button class="icon-btn view">👁</button>
                            <button class="icon-btn download">⬇</button>
                        </div>
                    </div>

                    <p class="record-description">{{record.description}}</p>
                    <p class="record-date">📅 {{record.date}}</p>

                    <div class="share-section">
                        <p>Share with Doctor:</p>
                        <div class="share-controls">
                            <input type="email" placeholder="doctor@example.com" ng-model="record.shareEmail">
                            <button ng-click="shareAccess(record.id, record.shareEmail)">Grant Access</button>
                        </div>

                        <div class="shared-list">
                            <div class="shared-item" ng-repeat="access in getSharedAccess(record.id)">
                                <span>✓ {{getDoctor(access.doctorId).name}}</span>
                                <button ng-click="revokeAccess(record.id, access.doctorId)">Revoke</button>
                            </div>
                        </div>
                    </div>
                </div>
            </div>

            <div ng-if="myRecords.length === 0" class="empty-state">
                <p>📄</p>
                <p>No records found. Upload your first medical record!</p>
                <button class="btn btn-primary" style="max-width: 200px; margin: 20px auto 0;" ng-click="view = 'upload'">Upload Record</button>
            </div>
        </div>
    </div>

    <!-- Upload View -->
    <div ng-if="view === 'upload'">
        <div class="navbar">
            <div class="navbar-content">
                <div class="logo">
                    <span>❤</span> HealthRecord
                </div>
                <div class="nav-links">
                    <button ng-click="view = 'dashboard'">Dashboard</button>
                    <button ng-class="{active: view === 'upload'}" ng-click="view = 'upload'">Upload</button>
                    <button ng-click="view = 'emergency'">Emergency Info</button>
                    <span>{{currentUser.name}}</span>
                    <button class="btn btn-danger" ng-click="logout()">Logout</button>
                </div>
            </div>
        </div>

        <div class="container" style="max-width: 800px;">
            <div class="dashboard-header">
                <h2>Upload Medical Record</h2>
            </div>

            <div class="record-card">
                <div class="form-group">
                    <label>Record Title</label>
                    <input type="text" ng-model="recordForm.title">
                </div>

                <div class="form-group">
                    <label>Record Type</label>
                    <select ng-model="recordForm.type">
                        <option value="lab_report">Lab Report</option>
                        <option value="prescription">Prescription</option>
                        <option value="imaging">Imaging (X-Ray/MRI/CT)</option>
                        <option value="consultation">Consultation Notes</option>
                        <option value="vaccination">Vaccination Record</option>
                        <option value="other">Other</option>
                    </select>
                </div>

                <div class="form-group">
                    <label>Description</label>
                    <textarea rows="4" ng-model="recordForm.description"></textarea>
                </div>

                <div class="form-group">
                    <label>Date</label>
                    <input type="date" ng-model="recordForm.date">
                </div>

                <div class="form-group">
                    <label>Upload File (PDF/Image)</label>
                    <div class="upload-area">
                        <p>📤</p>
                        <p>Click to upload or drag and drop</p>
                        <p class="note">PDF, JPG, PNG up to 10MB</p>
                    </div>
                </div>

                <button class="btn btn-primary" ng-click="uploadRecord()">➕ Upload Record</button>
            </div>
        </div>
    </div>

    <!-- Emergency Info View -->
    <div ng-if="view === 'emergency'">
        <div class="navbar">
            <div class="navbar-content">
                <div class="logo">
                    <span>❤</span> HealthRecord
                </div>
                <div class="nav-links">
                    <button ng-click="view = 'dashboard'">Dashboard</button>
                    <button ng-click="view = 'upload'">Upload</button>
                    <button ng-class="{active: view === 'emergency'}" ng-click="view = 'emergency'">Emergency Info</button>
                    <span>{{currentUser.name}}</span>
                    <button class="btn btn-danger" ng-click="logout()">Logout</button>
                </div>
            </div>
        </div>

        <div class="container" style="max-width: 800px;">
            <div class="alert-box">
                <h3>⚠ Emergency Medical Information</h3>
                <p>Critical information for first responders</p>
            </div>

            <div class="record-card">
                <div class="info-section">
                    <h3>Patient Information</h3>
                    <p><strong>Name:</strong> {{currentUser.name}}</p>
                </div>

                <div class="info-section">
                    <h3>🩸 Blood Group</h3>
                    <p class="blood-group">{{currentUser.bloodGroup || 'Not specified'}}</p>
                </div>

                <div class="info-section">
                    <h3>⚠ Known Allergies</h3>
                    <p>{{currentUser.allergies || 'None reported'}}</p>
                </div>

                <div class="info-section">
                    <h3>👤 Emergency Contact</h3>
                    <p>{{currentUser.emergencyContact || 'Not specified'}}</p>
                </div>

                <div class="tip-box">
                    <p>💡 <strong>Tip:</strong> Keep this information updated and accessible. In case of emergency, medical professionals can access this information quickly.</p>
                </div>
            </div>
        </div>
    </div>

    <!-- Doctor Dashboard -->
    <div ng-if="view === 'doctor-dashboard'">
        <div class="navbar">
            <div class="navbar-content">
                <div class="logo">
                    <span>❤</span> HealthRecord - Doctor Portal
                </div>
                <div class="nav-links">
                    <span>Dr. {{currentUser.name}}</span>
                    <button class="btn btn-danger" ng-click="logout()">Logout</button>
                </div>
            </div>
        </div>

        <div class="container">
            <div class="dashboard-header">
                <h2>Patient Records - Access Granted</h2>
            </div>

            <div ng-if="accessibleRecords.length > 0">
                <div class="record-card" ng-repeat="record in accessibleRecords">
                    <div class="record-header">
                        <div class="record-title">
                            <h3>{{record.title}}</h3>
                            <p class="record-type">Patient: {{getPatient(record.patientId).name}}</p>
                            <p class="record-type">{{record.type.replace('_', ' ').toUpperCase()}}</p>
                        </div>
                        <div class="record-actions">
                            <button class="icon-btn view">👁</button>
                            <button class="icon-btn download">⬇</button>
                        </div>
                    </div>

                    <p class="record-description">{{record.description}}</p>
                    <p class="record-date">📅 {{record.date}}</p>

                    <div class="share-section">
                        <p>Emergency Info:</p>
                        <div style="display: grid; grid-template-columns: 1fr 1fr; gap: 12px; font-size: 14px;">
                            <div><strong>Blood Group:</strong> {{getPatient(record.patientId).bloodGroup}}</div>
                            <div><strong>Allergies:</strong> {{getPatient(record.patientId).allergies}}</div>
                        </div>
                    </div>
                </div>
            </div>

            <div ng-if="accessibleRecords.length === 0" class="empty-state">
                <p>🔒</p>
                <p>No patient records accessible yet.</p>
                <p style="color: #9ca3af; font-size: 14px; margin-top: 8px;">Patients need to grant you access to their records.</p>
            </div>
        </div>
    </div>

    <script>
        angular.module('healthRecordApp', [])
            .controller('MainController', ['$scope', function($scope) {
                // Initial state
                $scope.view = 'login';
                $scope.currentUser = null;
                
                $scope.authForm = {
                    email: '',
                    password: '',
                    name: '',
                    role: 'patient',
                    bloodGroup: '',
                    allergies: '',
                    emergencyContact: ''
                };

                $scope.recordForm = {
                    title: '',
                    type: 'lab_report',
                    description: '',
                    date: new Date().toISOString().split('T')[0]
                };

                // Demo data
                $scope.users = [
                    {
                        id: 'u1',
                        email: 'patient@demo.com',
                        password: 'patient123',
                        name: 'John Doe',
                        role: 'patient',
                        bloodGroup: 'O+',
                        allergies: 'Penicillin',
                        emergencyContact: '+1234567890'
                    },
                    {
                        id: 'u2',
                        email: 'doctor@demo.com',
                        password: 'doctor123',
                        name: 'Dr. Sarah Smith',
                        role: 'doctor',
                        specialization: 'General Medicine',
                        licenseNo: 'MD12345'
                    }
                ];

                $scope.records = [
                    {
                        id: 'r1',
                        patientId: 'u1',
                        title: 'Blood Test Report',
                        type: 'lab_report',
                        description: 'Complete Blood Count - All values normal',
                        date: '2024-11-15',
                        uploadedBy: 'u1'
                    },
                    {
                        id: 'r2',
                        patientId: 'u1',
                        title: 'X-Ray Chest',
                        type: 'imaging',
                        description: 'Chest X-Ray - No abnormalities detected',
                        date: '2024-10-20',
                        uploadedBy: 'u2'
                    }
                ];

                $scope.sharedAccess = [];

                // Login
                $scope.login = function() {
                    var user = $scope.users.find(function(u) {
                        return u.email === $scope.authForm.email && u.password === $scope.authForm.password;
                    });

                    if (user) {
                        $scope.currentUser = user;
                        $scope.view = user.role === 'patient' ? 'dashboard' : 'doctor-dashboard';
                        $scope.authForm.email = '';
                        $scope.authForm.password = '';
                        $scope.updateRecords();
                    } else {
                        alert('Invalid credentials!\nTry:\nPatient: patient@demo.com / patient123\nDoctor: doctor@demo.com / doctor123');
                    }
                };

                // Signup
                $scope.signup = function() {
                    if (!$scope.authForm.email || !$scope.authForm.password || !$scope.authForm.name) {
                        alert('Please fill all required fields!');
                        return;
                    }

                    var newUser = {
                        id: 'u' + ($scope.users.length + 1),
                        email: $scope.authForm.email,
                        password: $scope.authForm.password,
                        name: $scope.authForm.name,
                        role: $scope.authForm.role,
                        bloodGroup: $scope.authForm.bloodGroup,
                        allergies: $scope.authForm.allergies,
                        emergencyContact: $scope.authForm.emergencyContact
                    };

                    $scope.users.push(newUser);
                    alert('Account created! Please login.');
                    $scope.view = 'login';
                    $scope.authForm = {
                        email: '',
                        password: '',
                        name: '',
                        role: 'patient',
                        bloodGroup: '',
                        allergies: '',
                        emergencyContact: ''
                    };
                };

                // Upload Record
                $scope.uploadRecord = function() {
                    if (!$scope.recordForm.title || !$scope.recordForm.description) {
                        alert('Please fill all fields!');
                        return;
                    }

                    var newRecord = {
                        id: 'r' + ($scope.records.length + 1),
                        patientId: $scope.currentUser.id,
                        title: $scope.recordForm.title,
                        type: $scope.recordForm.type,
                        description: $scope.recordForm.description,
                        date: $scope.recordForm.date,
                        uploadedBy: $scope.currentUser.id
                    };

                    $scope.records.push(newRecord);
                    alert('Record uploaded successfully!');
                    $scope.recordForm = {
                        title: '',
                        type: 'lab_report',
                        description: '',
                        date: new Date().toISOString().split('T')[0]
                    };
                    $scope.view = 'dashboard';
                    $scope.updateRecords();
                };

                // Share Access
                $scope.shareAccess = function(recordId, doctorEmail) {
                    var doctor = $scope.users.find(function(u) {
                        return u.email === doctorEmail && u.role === 'doctor';
                    });

                    if (doctor) {
                        $scope.sharedAccess.push({
                            recordId: recordId,
                            doctorId: doctor.id,
                            patientId: $scope.currentUser.id
                        });
                        alert('Access granted to ' + doctor.name);
                        $scope.updateRecords();
                    } else {
                        alert('Doctor not found!');
                    }
                };

                // Revoke Access
                $scope.revokeAccess = function(recordId, doctorId) {
                    $scope.sharedAccess = $scope.sharedAccess.filter(function(s) {
                        return !(s.recordId === recordId && s.doctorId === doctorId);
                    });
                    alert('Access revoked!');
                    $scope.updateRecords();
                };

                // Logout
                $scope.logout = function() {
                    $scope.currentUser = null;
                    $scope.view = 'login';
                };

                // Update Records
                $scope.updateRecords = function() {
                    if ($scope.currentUser) {
                        if ($scope.currentUser.role === 'patient') {
                            $scope.myRecords = $scope.records.filter(function(r) {
                                return r.patientId === $scope.currentUser.id;
                            });
                        } else {
                            $scope.accessibleRecords = $scope.records.filter(function(r) {
                                return $scope.sharedAccess.some(function(s) {
                                    return s.doctorId === $scope.currentUser.id && s.recordId === r.id;
                                });
                            });
                        }
                    }
                };

                // Helper functions
                $scope.getSharedAccess = function(recordId) {
                    return $scope.sharedAccess.filter(function(s) {
                        return s.recordId === recordId;
                    });
                };

                $scope.getDoctor = function(doctorId) {
                    return $scope.users.find(function(u) {
                        return u.id === doctorId;
                    }) || {};
                };

                $scope.getPatient = function(patientId) {
                    return $scope.users.find(function(u) {
                        return u.id === patientId;
                    }) || {};
                };

                // Initialize
                $scope.updateRecords();
            }]);
    </script>
</body>
</html>
