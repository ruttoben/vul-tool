import subprocess
import re
from reportlab.pdfgen import canvas

# Get user input for the target URL and scan type
url = input("Enter the target URL: ")
scan_type = input("Enter the scan type (SQL or XSS): ")

# Execute SQLMap or XSSer with the appropriate command-line options
if scan_type.lower() == "sql":
    output = subprocess.check_output(["sqlmap", "-u", url], cwd="/path/to/sqlmap/directory")
else:
    output = subprocess.check_output(["xsstrike", "-u", url], cwd="/path/to/xsser/directory")

# Parse the output of the vulnerability scan
vulnerabilities = re.findall("Vulnerability: (.+)\n", output.decode())

# Generate a PDF report of the vulnerabilities
report = canvas.Canvas("vulnerability_report.pdf")
y = 720
for vuln in vulnerabilities:
    report.drawString(100, y, vuln)
    y -= 20
report.save()
print("Report generated successfully.")
