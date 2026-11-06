# TryHackMe SOC Level 1

I completed the TryHackMe SOC Level 1 learning path and practised investigating alerts in a simulated SOC. I used the SIEM to search for related events and decide which alerts needed escalation.

## Example investigation: Suspected DNS exfiltration

I reviewed a high-severity alert where PowerShell launched `nslookup.exe` with an encoded-looking subdomain. In the SIEM, I found another lookup to the same domain with a different encoded-looking prefix. Both commands came from the same PowerShell process on the same host.

I also connected two earlier events to that process: a command to map a financial records share and another to disconnect the mapped drive. I used the hostname, parent process ID and event timestamps to put the activity in order.

I classified the DNS alert as a true positive and escalated it as suspected DNS exfiltration. The logs showed the commands being launched. Whether files were accessed or data was successfully transferred remained unconfirmed.

## What I learned

I learned how to connect alerts using the host, process and event time. I also learned to separate what the logs show from what I suspect happened.
