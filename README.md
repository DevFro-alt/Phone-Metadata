cat << 'EOF' > README.md
# 📞 Scam Call Investigation & Phone OSINT Guide

Recently, we received **unknown calls** from numbers not saved in our contacts that exhibited a *suspicious pattern*—several numbers appeared nearly identical, differing by only ~20% of their digits. We identified these as **call scammers**.

---

## 🛠️ OSINT Tools Used

* **[PhoneInfoga](https://sundowndev.github.io/phoneinfoga)** – Advanced tool for phone number OSINT recon.
* **[Numverify API](https://marketplace.apilayer.com/number_verification-api)** – Global phone number verification & carrier lookup service.
* **`venv`** – Python virtual environment for isolated tool execution.

---

## 🎯 Purpose

The objective of this reconnaissance is to expose target number **metadata**, specifically:
* **Country** origin
* **Validity** status
* **Number Carrier** *(Most critical identifier)*

> **System Requirement:** This tutorial targets **UNIX Terminals** (Linux/macOS). If you are using Windows, run this within **WSL (Windows Subsystem for Linux)**.

---

## 🚀 Step-by-Step Tutorial

1. **Open Documentation:** Go to the [PhoneInfoga Official Site](https://sundowndev.github.io/phoneinfoga).
2. **Navigate:** Scroll down to the **Installation** section.
3. **Binary Setup:** Under *Binary Installation*, follow steps 1 to 3 (or copy straight from our repository file).
4. **Verify Version:** Confirm that PhoneInfoga is updated to the latest version.
5. **Check Commands:** Open your CLI terminal and execute:
   ```bash
   phoneinfoga --help
   ```
6. **Basic Local Scan:** Run a preliminary scan on your target:
   ```bash
   phoneinfoga scan -n <target_number>
   ```
   > ⚠️ **Note:** A standard `phoneinfoga scan` performs an offline *local scan* (faster, but relies solely on Google's offline `libphonenumber`). For real-time infrastructure data, **Numverify** integration is required.

7. **Access Numverify:** Head over to the [Numverify API Portal](https://marketplace.apilayer.com/number_verification-api).
8. **Create Account:** Sign up for an APILayer account to claim a free subscription tier.
9. **OpSec Privacy Tip:** When creating accounts for OSINT research, use a *burner email* or *alias address* (e.g., Proton Mail SimpleLogin aliases).
10. **Retrieve Credentials:** Copy your assigned **API Key** from the dashboard.
11. **Return to CLI:** Reopen your active terminal window.
12. **Initialize Environment:** We advise running inside a virtual environment (`venv`) to keep dependencies isolated and avoid corrupting system-level modules:
    ```bash
    python3 -m venv osint_env
    source osint_env/bin/activate
    ```
    *(Note: While PhoneInfoga v2 is a compiled Go binary that operates independently of Python, using `venv` remains essential for managing general OSINT tool suites on environments like Kali Linux).*
13. **Execute Deep Scan:** Run the infrastructure-level scan using your Numverify credentials (refer to our script repository for exact flag formatting).
14. **Scan Duration:** Allow the scan to process, which usually takes between **30 seconds to 2 minutes**.
15. **Analyze Results:** Once finished, inspect the target output detailing *validity, local format, international format, country, and carrier details*.

---

## 🏁 Conclusion

By combining **local offline parsing** (`libphonenumber`) with **infrastructure API integration** (`Numverify`), you can quickly extract actionable intelligence from unknown numbers. Pinpointing line validity and carrier provenance allows you to map out scam pattern clusters, report fraudulent blocks, and protect your communications before interacting with unknown callers.

---

> ⚖️ **Disclaimer:** *This project aims strictly to expose scammers and spam callers, NOT for illegal stalking. If you intend to investigate an individual's phone number, ensure you have explicit authorization before conducting research. All programs, services, and tools belong to their respective creators.*
EOF
