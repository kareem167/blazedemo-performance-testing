# BlazeDemo Performance Testing

A JMeter project for exercising BlazeDemo’s flight-booking journey and measuring the behavior of its web requests. The repository contains the test plan, test data, and requirements document.

> **Test environment:** BlazeDemo is a shared public demo. Keep checks against the public site low-volume. Run load, stress, soak, and repeated-purchase testing only in an environment you own or are authorized to test. Use payment values approved for a sandbox.

## Requirements Coverage

The test plan is intended to cover the four-step booking journey:

1. **Home page** — load the application.
2. **Flight search** — submit departure and destination cities and check the results.
3. **Flight selection** — submit the selected flight details.
4. **Purchase and confirmation** — submit fictional passenger and approved sandbox payment data, then check the confirmation response.

The plan includes these test profiles:

- **Smoke** — checks that the booking flow runs with minimal traffic.
- **Single Purchase Check** — validates one end-to-end purchase.
- **Baseline** — records reference response times.
- **Load** — measures the configured steady workload.
- **Stress** — increases users in stages.
- **Soak** — runs the configured workload over time.

The JMeter plan includes request assertions and response-time limits for the booking steps, timers to model pauses, and extractors for values used by later requests. The requirements document defines the expected behavior, workload profiles, acceptance criteria, reporting metrics, and stop conditions.

## Repository Contents

| Path | Description |
|---|---|
| `BlazeDemo Performance Test Plan.jmx` | JMeter test plan and Thread Groups |
| `testData/cities_data.csv` | Route data for flight searches |
| `testData/passenger_payment_data.csv` | Fictional passenger and sandbox payment test data |
| `testRequirement/BlazeDemo_Performance_Test_Requirements.docx` | Detailed requirements and test guidance |
| `result/` | Local JTL results and HTML reports, when included |

## Requirements

- Apache JMeter 5.6.3
- JMeter Plugins Ultimate Thread Group plugin for the Stress profile
- The CSV data files listed above
- An authorized environment for performance testing
- Sandbox-approved payment values for purchase scenarios

## Running the Test Plan

From the repository root, run:

```powershell
jmeter -n -t "BlazeDemo Performance Test Plan.jmx" -l "result/run.jtl" -e -o "result/run-report"
```

This runs the enabled Thread Groups, writes sample results to a JTL file, and generates an HTML dashboard. Review the enabled groups before running: multiple enabled groups may run together unless the Test Plan is configured to run them consecutively. Use a new or empty report folder for each run.

## Test Data and Results

Use fictional passenger details and payment values approved by the selected sandbox. Do not commit real payment data, credentials, cookies, or tokens.

Review JTL files and HTML reports before sharing them. Generated results may contain request or response details, and are excluded from version control by the repository’s `.gitignore` unless intentionally added.

## Detailed Requirements

See [BlazeDemo Performance Test Requirements](testRequirement/BlazeDemo_Performance_Test_Requirements.docx) for the full application scope, workload settings, acceptance criteria, execution schedule, reporting expectations, and risk controls.
