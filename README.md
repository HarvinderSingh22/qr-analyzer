# qr-analyzer

PART 1: UNDERSTANDING THE TOOL
What This Tool Does
This is a client-side QR security analyzer that:

    Scans QR codes via image upload or camera
    Decodes the hidden content (URL or text)
    Performs 15+ security checks on the content
    Shows a risk score (0-100% safe) with color-coded results
    Identifies phishing, malware, and suspicious patterns
    Provides detailed security analysis for each finding

Example Scenarios:

    ✅ SAFE: QR code for a legitimate website like https://google.com
    ⚠️ MEDIUM: QR code with HTTP URL or URL shortener like bit.ly
    🚨 HIGH RISK: QR code pointing to an IP address or fake bank site

How It Works (Basic Logic/Flow)
JavaScript
Copy

1. USER INPUT → Upload QR image or use camera
2. IMAGE PROCESSING → Read pixels using JavaScript FileReader API
3. QR DECODING → jsQR library extracts hidden content (URL/text)
4. CONTENT ANALYSIS → 
   - IF URL → Check HTTPS, domain, redirects, patterns (10 tests)
   - IF TEXT → Check for sensitive data, encoding (5 tests)
5. SCORING → Each test adds points (Safe=0, Warning=3, Danger=5)
6. RISK LEVEL → Calculate final score and show Green/Yellow/Red
7. DISPLAY → Show risk factors, icons, and action buttons

Key Functions You'll Build:

    processImage() - Handles file/camera input
    decodeQRCode() - Extracts content using jsQR
    analyzeUrl() - Runs security tests on URLs
    displayResults() - Shows final report

How to Use It - Simple User Guide
Method 1: Upload QR Code Image

    Click on the dashed upload area or drag-and-drop your QR image
    Supports JPG, PNG, GIF, BMP (max 10MB)
    Tool automatically scans and shows results

Method 2: Camera Scan

    Click "📹 Use Camera" button
    Allow camera permission when browser asks
    Hold camera steady over the QR code
    Auto-scans in 1-2 seconds and shows results

Understanding Results

    Risk Score (0-100%): Higher is safer
        80-100% ✅ SAFE (Green)
        50-79% ⚠️ MEDIUM (Yellow) - Verify source
        0-49% 🚨 HIGH RISK (Red) - Do NOT open
    Risk Factors: Each factor shows:
        ✅ = Safe
        ⚠️ = Warning
        🚨 = Danger
    Action Buttons:
        "🔄 New Scan" - Scan another QR code
        "📋 Copy Content" - Copy decoded text/URL
        "🔗 Open Link" - Open URL in new tab (only for URLs)

Safety Guide

    Never scan QR codes from unknown posters or emails
    Always verify URLs manually before entering sensitive data
    Check for HTTPS - Look for padlock icon in browser
    Be careful with URL shorteners (bit.ly, tinyurl)
    Payment QR codes - Verify amount before scanning
