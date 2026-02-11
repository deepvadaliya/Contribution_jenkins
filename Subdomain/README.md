## find out the subdomains of root domain(main domain)

##  1) use the sublist3r
- sudo apt install sublist3r
  run this  -  sublist3r -d example.com

##  2) use the amass
- sudo apt install amass
  run this - amass enum -passive -d example.com

##  3) install golang (using waybackurls)
- sudo apt install golang
- sudo go install github.com/tomnomnom/waybackurls@latest
- cd ~/go/bin  =>  you can see one file are created at this location
  
ubuntu@subdomain:~/go/bin$ ls
waybackurls

ubuntu@subdomain:~/go/bin$ ./waybackurls -h

- nano domain.txt
- write your root url in this field => example.com

run this command after all this setup
- cat optimizerx.txt | ./waybackurls > example.urls

##  4) using subfinder

🔹 Step 1: Check if Go is installed
- go version

If not installed:

- sudo apt update
- sudo apt install golang -y

🔹 Step 2: Install subfinder
- go install -v github.com/projectdiscovery/subfinder/v2/cmd/subfinder@latest

This downloads and builds the tool.

🔹 Step 3: Add Go bin to PATH (IMPORTANT)
- export PATH=$PATH:$HOME/go/bi

Make it permanent:

- echo 'export PATH=$PATH:$HOME/go/bin' >> ~/.bashrc
- source ~/.bashrc

🔹 Step 4: Verify installation
- subfinder -version

✅ Method 2: Install using APT (if available)

- sudo apt update
- sudo apt install subfinder -y

Verify:
subfinder -version

Final step Run this command
- subfinder -dL example.txt -all -recursive -o subdomain.txt

##  5) Check the alive Domain
the last step is we are findout the domains but how to check this domain's are working or not 
to solve this we are use the HTTPX command this command are check which domain are working or not

Install HTTPX
Method 1: 

1) you required the go version before run this command
   (Install httpx using Go)
   - go install -v github.com/projectdiscovery/httpx/cmd/httpx@latest

2) Add Go bin to PATH (IMPORTANT)
   - export PATH=$PATH:$HOME/go/bin

    to make it permanent
   - echo 'export PATH=$PATH:$HOME/go/bin' >> ~/.bashrc
   - source ~/.bashrc
     
3) Verify installation
   - httpx -version


  ####  test the httpx is working 
  
🧪 Test httpx (Simple & Safe)
Check a single domain:
- echo example.com | httpx

Check multiple subdomains (your use case):
- httpx -l subdomain.txt

  🛠️ Useful httpx options (Beginner-friendly)
- httpx -l subdomain.txt -title -status-code -tech-detect
Shows:
HTTP status code (200, 301, 403…)
Page title
Technologies used

## Save alive domains only:
httpx -l subdomain.txt -o alive.txt
