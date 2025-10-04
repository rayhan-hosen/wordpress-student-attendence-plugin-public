# Guardian Attendance - WordPress Plugin

A comprehensive WordPress plugin designed for educational institutions to manage student attendance with separate interfaces for administrators and guardians.

## 📋 Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Installation](#installation)
- [Configuration](#configuration)
- [Usage](#usage)
- [Shortcodes](#shortcodes)
- [File Structure](#file-structure)
- [Customization](#customization)
- [Security](#security)
- [Troubleshooting](#troubleshooting)


## 🎯 Overview

Guardian Attendance is a WordPress plugin that provides a complete attendance management system for schools and educational institutions. It offers a dual-interface approach where administrators can mark attendance while guardians can view their child's attendance records through an intuitive calendar interface. **A Extended plugin associated with TutotLMS**

### Key Benefits

- **Dual Interface**: Separate admin and guardian views
- **Privacy-Focused**: Uses last 4 digits of student ID for privacy
- **Calendar Visualization**: Easy-to-read monthly attendance calendar
- **Responsive Design**: Works seamlessly on desktop and mobile devices
- **Secure**: Built with WordPress security best practices

## ✨ Features

### For Administrators

- **Easy Attendance Marking**: Simple form to mark student attendance
- **Student ID Validation**: 8-digit student ID input with pattern validation
- **Date Selection**: Flexible date picker for marking attendance
- **Status Management**: Present/Absent status tracking
- **Today's Overview**: Quick view of today's attendance records
- **Admin Dashboard**: Dedicated WordPress admin menu

### For Guardians
- **Calendar View**: Monthly calendar showing attendance status
- **Month/Year Navigation**: Easy navigation between different months
- **Visual Indicators**: Color-coded attendance status (Green for Present, Red for Absent)
- **Student Linking**: Automatic student-guardian account linking
- **Responsive Interface**: Mobile-friendly calendar display

### Technical Features
- **Database Management**: Automatic table creation and cleanup
- **Data Validation**: Comprehensive input validation and sanitization
- **Nonce Security**: CSRF protection for all forms
- **Translation Ready**: Full internationalization support
- **Clean Uninstall**: Complete data removal on plugin deletion

## 🚀 Installation

### Method 1: WordPress Admin Dashboard

1. Log in to your WordPress admin dashboard
2. Navigate to **Plugins** → **Add New**
3. Click **Upload Plugin**
4. Choose the `student-attendance.zip` file
5. Click **Install Now**
6. Activate the plugin

### Method 2: Manual Installation

1. Download the plugin files
2. Extract the contents to `/wp-content/plugins/guardian-attendance/`
3. Log in to WordPress admin dashboard
4. Navigate to **Plugins** → **Installed Plugins**
5. Find "Guardian Attendance" and click **Activate**

### Requirements

- WordPress 5.0 or higher
- PHP 7.4 or higher
- MySQL 5.6 or higher
- User roles: `edit_pages` capability for admin access

## ⚙️ Configuration

### Admin Setup

1. **Access Admin Panel**: Navigate to **Attendance** in your WordPress admin menu
2. **Permissions**: Ensure users have `edit_pages` capability to access attendance features
3. **Database**: The plugin automatically creates required database tables on activation

### Guardian Setup

1. **User Accounts**: Create WordPress user accounts for guardians
2. **Student Linking**: Link guardian accounts to student accounts
3. **Shortcode Placement**: Add the attendance shortcode to pages where guardians should view attendance

## 📖 Usage

### Admin Usage

#### Marking Attendance

1. Go to **Attendance** in your WordPress admin menu
2. Enter the student's 8-digit ID
3. Select the attendance date (defaults to today)
4. Choose status: Present or Absent
5. Click **Submit Attendance**

#### Viewing Today's Records

- The admin page automatically displays all attendance records for the current day
- Records show the last 4 digits of student ID and their status
- Updates are reflected immediately after submission

### Guardian Usage

#### Viewing Attendance

1. Log in to your WordPress account
2. Navigate to the page containing the attendance shortcode
3. Use the month/year dropdowns to navigate between different months
4. View attendance status on the calendar:
   - **Green circle with "P"**: Present
   - **Red circle with "A"**: Absent
   - **No indicator**: No attendance recorded

## 🔧 Shortcodes

### Primary Shortcode

```
[guardian_attendance]
```

**Description**: Displays the attendance calendar for the logged-in guardian's linked student.

**Parameters**: None required

**Usage Example**:
```php
// In a page or post
[guardian_attendance]

// In PHP template
echo do_shortcode('[guardian_attendance]');
```


## 📁 File Structure

```
guardian-attendance/
├── admin/
│   ├── attendance-page.php      # Admin interface
│   ├── css/
│   │   └── admin-style.css      # Admin styling
│   └── js/
│       └── admin-script.js      # Admin JavaScript
├── frontend/
│   └── css/
│       └── frontend-style.css   # Frontend styling
├── includes/
│   ├── attendance-functions.php # Core functions
│   ├── class-attendance-db.php  # Database operations
│   └── class-attendance-shortcode.php # Shortcode handler
├── student-attendance.php       # Main plugin file
├── uninstall.php               # Cleanup script
└── README.md                   # This file
```

## 🎨 Customization

### Styling Customization

#### Admin Styling
Edit `admin/css/admin-style.css` to customize:
- Form layouts and colors
- Button styles
- Table appearance
- Responsive breakpoints

#### Frontend Styling
Edit `frontend/css/frontend-style.css` to customize:
- Calendar appearance
- Color schemes for attendance status
- Form styling
- Mobile responsiveness

### Functional Customization

#### Adding Custom Status Types
To add new attendance statuses (e.g., "Late", "Excused"):

1. Update the database schema in `class-attendance-db.php`
2. Modify the status validation in `attendance-functions.php`
3. Update the admin form in `attendance-page.php`
4. Add corresponding CSS classes

#### Custom Student ID Format
To change from 8-digit to different ID format:

1. Update the pattern validation in `attendance-page.php`
2. Modify the sanitization logic in `attendance-functions.php`
3. Adjust the last-4-digit extraction logic

## 🔒 Security

### Security Features

- **Nonce Protection**: All forms use WordPress nonces for CSRF protection
- **Input Sanitization**: All user inputs are sanitized and validated
- **Capability Checks**: Admin functions require proper WordPress capabilities
- **SQL Injection Prevention**: All database queries use prepared statements
- **XSS Protection**: All outputs are properly escaped

### Security Best Practices

1. **Regular Updates**: Keep the plugin updated
2. **User Permissions**: Regularly audit user capabilities
3. **Database Access**: Monitor database access logs
4. **Input Validation**: Never bypass input validation

## 🐛 Troubleshooting

### Common Issues

#### "You do not have sufficient permissions"
- **Cause**: User lacks `edit_pages` capability
- **Solution**: Assign proper WordPress role or add capability

#### "No student linked to your account"
- **Cause**: Guardian account not linked to student
- **Solution**: Link Guardian account with student accunt in TutorLMS

#### Calendar not displaying
- **Cause**: Missing CSS or JavaScript files
- **Solution**: Check file permissions and WordPress file structure

#### Database errors
- **Cause**: Table creation failed or corrupted
- **Solution**: Deactivate and reactivate plugin to recreate tables

### Debug Mode

Enable WordPress debug mode to see detailed error messages:

```php
// In wp-config.php
define('WP_DEBUG', true);
define('WP_DEBUG_LOG', true);
define('WP_DEBUG_DISPLAY', false);
```

### Log Files

Check WordPress debug log at `/wp-content/debug.log` for detailed error information.




### Coding Standards

- Follow WordPress Coding Standards
- Use proper PHP documentation
- Include security considerations
- Test on multiple WordPress versions



## 📞 Support

For support, feature requests, or bug reports:

- **Author**: Rayhan Hosen
- **Version**: 1.0
- **Text Domain**: guardian-attendance
- **WordPress Compatibility**: 5.0+
- **PHP Compatibility**: 7.4+

---

**Note**: This plugin is designed for educational institutions and requires proper WordPress user management setup for optimal functionality. Ensure your WordPress installation has appropriate user roles and capabilities configured before use. For the plugin contact https://www.linkedin.com/in/rayhan-hosen/
