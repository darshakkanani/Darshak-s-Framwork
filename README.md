<h1 align="center">
Darshak's Framework
</h1>

<p align="center"><b>The Framework Includes All These Tools And More!</b></p>

<p align="center">
    <a href="https://github.com/owasp-amass/amass">Amass</a> - Advanced attack surface mapping and asset discovery tool for security research<br>
    <a href="https://github.com/projectdiscovery/subfinder">Subfinder</a> - Fast and reliable subdomain enumeration tool with multiple data sources<br>
    <a href="https://github.com/aboul3la/Sublist3r">Sublist3r</a> - Fast subdomain enumeration tool using various search engines and data sources<br>
    <a href="https://github.com/tomnomnom/assetfinder">Assetfinder</a> - Find assets related to a domain using various data sources and APIs<br>
    <a href="https://github.com/projectdiscovery/httpx">Httpx</a> - Fast and multi-purpose HTTP toolkit for web reconnaissance and scanning<br>
    <a href="https://github.com/jaeles-project/gospider">GoSpider</a> - Fast web spider written in Go for crawling and extracting URLs<br>
    <a href="https://github.com/nsonaniya2010/SubDomainizer">Subdomainizer</a> - Advanced subdomain enumeration tool with multiple discovery methods<br>
    <a href="https://github.com/digininja/CeWL">CeWL</a> - Custom word list generator that spiders websites to create targeted wordlists<br>
    <a href="https://github.com/projectdiscovery/shuffledns">ShuffleDNS</a> - Mass DNS resolver with wildcard filtering and validation capabilities<br>
    <a href="https://github.com/projectdiscovery/nuclei">Nuclei</a> - Fast and customizable vulnerability scanner with extensive template library<br>
    <a href="https://github.com/projectdiscovery/katana">Katana</a> - Fast and powerful web crawler for discovering hidden endpoints and content<br>
    <a href="https://github.com/ffuf/ffuf">FFuf</a> - Fast web fuzzer with support for multiple protocols and advanced filtering<br>
    <a href="https://github.com/lc/gau">GAU</a> - Get All URLs tool that fetches known URLs from various historical data sources<br>
    <a href="https://github.com/pdiscoveryio/ctl">CTL</a> - Certificate Transparency Log tool for discovering subdomains from SSL certificates<br>
    <a href="https://github.com/projectdiscovery/dnsx">DNSx</a> - Fast and multi-purpose DNS toolkit for running multiple DNS queries<br>
    <a href="https://github.com/initstring/cloud_enum">Cloud Enum</a> - Multi-cloud OSINT tool for enumerating public resources in AWS, Azure, and Google Cloud<br>
    <a href="https://github.com/j3ssie/metabigor">Metabigor</a> - OSINT tool for network intelligence gathering including ASN and IP range discovery<br>
    <a href="https://github.com/gwen001/github-search">GitHub Recon</a> - GitHub reconnaissance tool for discovering organization mentions and domain patterns<br>
    <a href="https://github.com/projectdiscovery/naabu">Naabu</a> - Fast port scanner for discovering open ports and services<br>
    <a href="https://github.com/whoxy/whoxy">Reverse Whois</a> - Reverse WHOIS lookup using Whoxy to find domains registered by the same entity<br>
    <a href="https://securitytrails.com">SecurityTrails</a> - Comprehensive DNS, domain, and IP data provider for digital asset discovery<br>
    <a href="https://censys.io">Censys</a> - Internet-wide scanning platform for discovering and monitoring assets<br>
    <a href="https://shodan.io">Shodan</a> - Search engine for internet-connected devices and services<br>
</p>

## Workflows

The Ars0n Framework v2 supports three distinct workflows, each designed for different reconnaissance scenarios and objectives. Each workflow follows rs0n's proven bug bounty methodology and automatically guides users through the correct sequence of tools and techniques.

### Company Workflow

**Objective:** Discover and map all digital assets owned by an organization to build a comprehensive attack surface for security testing.

The Company workflow is designed to answer the question: "What does this organization's entire digital footprint look like?" This workflow takes a company name and systematically discovers all assets that organization owns or operates, both on-premises and in the cloud.

#### Key Steps:

1. **ASN (On-Prem) Network Ranges** - Discover network infrastructure owned by the organization
   - **Tools:** Amass Intel, Metabigor
   - **Purpose:** Intelligence gathering and ASN enumeration for comprehensive network range discovery
   - **How:** Uses company name to discover Autonomous System Numbers (ASNs) and associated IP network ranges through WHOIS data and BGP routing information

2. **Discover Live Web Servers (On-Prem)** - Find active web services in discovered network ranges
   - **Tools:** IP/Port scanning and Live Web Server detection
   - **Purpose:** Process discovered network ranges to identify live IP addresses and active web servers
   - **How:** Port scans network ranges and validates HTTP/HTTPS services within the organization's infrastructure

3. **Root Domain Discovery (No API Key)** - Find company domains using free/public sources
   - **Tools:** Google Dorking, CRT (Certificate Transparency), Reverse Whois
   - **Purpose:** Discover company domains and subdomains using publicly available information
   - **How:** Advanced Google search techniques, certificate transparency logs analysis, and reverse WHOIS lookups to find domains registered by the same entity

4. **Root Domain Discovery (API Key)** - Enhanced domain discovery using premium services
   - **Tools:** SecurityTrails, GitHub Recon Tools, Shodan CLI/API, Censys
   - **Purpose:** Comprehensive domain discovery using commercial APIs and databases
   - **How:** Leverages premium DNS/domain data providers, searches GitHub repositories for organization mentions, and queries internet scanning databases

5. **Consolidate Root Domains** - Organize discovered domains for systematic enumeration
   - **Tools:** Domain consolidation engine
   - **Purpose:** Create a unified list of unique root domains and prepare for subdomain enumeration
   - **How:** Deduplicates discovered domains and automatically creates Wildcard targets for comprehensive subdomain discovery

6. **Cloud Asset Enumeration (DNS)** - Discover cloud-hosted assets and services
   - **Tools:** Amass Enum, DNSx
   - **Purpose:** Advanced DNS enumeration and cloud asset discovery across all discovered domains
   - **How:** DNS brute-forcing, certificate transparency analysis, and comprehensive DNS record discovery to find cloud-hosted assets and subdomains

**Result:** Complete visibility into the company's attack surface, enabling security teams to explore all discovered targets and conduct comprehensive Nuclei scanning against live assets.

### Wildcard Workflow  

**Objective:** Comprehensively enumerate all subdomains under a root domain and prioritize the most valuable targets for manual testing.

The Wildcard workflow solves a critical problem faced by bug bounty hunters: after discovering hundreds or thousands of subdomains, how do you know which ones are worth your limited time? This workflow not only finds subdomains but intelligently ranks them based on their likelihood of containing vulnerabilities.

#### Key Steps:

1. **Amass Enum** - Advanced subdomain enumeration and OSINT reconnaissance
   - **Tools:** Amass Enum
   - **Purpose:** Powerful subdomain enumeration and OSINT tool for in-depth reconnaissance
   - **How:** Uses active and passive techniques including DNS brute-forcing, certificate transparency, and multiple data sources for comprehensive subdomain discovery

2. **Subdomain Scraping** - Gather subdomains from multiple OSINT sources
   - **Tools:** Sublist3r, Assetfinder, GAU, CTL, Subfinder
   - **Purpose:** Comprehensive subdomain discovery using various OSINT techniques and data sources
   - **How:** Queries search engines, certificate databases, web archives (Wayback Machine, Common Crawl), and multiple subdomain databases

3. **Consolidate Subdomains & Discover Live Web Servers - Round 1** - First consolidation and validation
   - **Tools:** Consolidation engine, Live Web Server detection
   - **Purpose:** Remove duplicates and identify which subdomains are serving live content
   - **How:** Deduplicates discovered subdomains and probes for HTTP/HTTPS responses to find active web servers

4. **Brute-Force** - Advanced DNS resolution and custom wordlist generation
   - **Tools:** ShuffleDNS, CeWL
   - **Purpose:** DNS brute-forcing with custom wordlists and mass DNS resolution
   - **How:** Generates target-specific wordlists from discovered content and performs high-speed DNS brute-forcing to find additional subdomains

5. **Consolidate Subdomains & Discover Live Web Servers - Round 2** - Second consolidation round
   - **Tools:** Consolidation engine, Live Web Server detection
   - **Purpose:** Process new brute-force discoveries and validate accessibility
   - **How:** Incorporates newly discovered subdomains and confirms they're serving live content

6. **JavaScript/Link Discovery** - Deep web application analysis
   - **Tools:** GoSpider, Subdomainizer
   - **Purpose:** Web scraping and crawling to discover hidden endpoints and JavaScript-embedded subdomains
   - **How:** Crawls live web applications and analyzes JavaScript files for embedded URLs, API endpoints, and additional subdomains

7. **Consolidate Subdomains & Discover Live Web Servers - Round 3** - Final consolidation
   - **Tools:** Consolidation engine, Live Web Server detection
   - **Purpose:** Final validation of all discovered assets from JavaScript/link analysis
   - **How:** Processes all newly discovered subdomains and ensures comprehensive live web server identification

8. **Decision Point - ROI Analysis** - Prioritize targets for manual testing
   - **Tools:** Screenshot capture, Metadata analysis
   - **Purpose:** Gather intelligence to identify targets with the greatest ROI for bug bounty hunting
   - **How:** Takes screenshots of web applications and analyzes metadata to identify signs of vulnerabilities, lack of maintenance, or large attack surfaces

**Key Value - MetaData Results:** The MetaData step provides detailed intelligence about each discovered URL, including:
- **Technologies Used:** Frameworks, CMS platforms, server software, and third-party services
- **Security Headers:** Analysis of security-related HTTP headers and their configurations
- **SSL/TLS Information:** Certificate details, encryption settings, and potential vulnerabilities  
- **DNS Records:** Complete DNS record analysis for each subdomain
- **HTTP Response Analysis:** Status codes, content types, and response characteristics
- **Architecture Insights:** Server configurations and application stack information

**Key Value - ROI Scoring Algorithm:** Based on rs0n's years of bug bounty hunting experience, each target receives an ROI (Return on Investment) score that predicts how likely it is to contain vulnerabilities. The algorithm considers:

- **SSL/TLS Issues:** Expired, self-signed, or misconfigured certificates (+25 points each)
- **Content Richness:** Number of discovered endpoints and functionality (+1-3 points per endpoint)
- **Technology Stack:** Presence of specific technologies known to have vulnerabilities (+3 points per technology)
- **Security Misconfigurations:** Missing security headers like CSP (+10 points)
- **Application Complexity:** Caching headers and dynamic content indicators (+10 points)
- **Error Pages:** 404 responses that might reveal information (+50 points)

This ROI scoring system directly addresses the biggest challenge beginners face in bug bounty hunting: **knowing where to start testing after subdomain enumeration**. Instead of randomly testing hundreds of targets, hunters can focus their efforts on the highest-scoring assets that are most likely to yield results.

### URL Workflow

**Objective:** Educational workflow that teaches manual bug bounty hunting techniques through dynamic, personalized lesson plans built specifically for your target.

The URL workflow represents the core educational mission of the Darshak Framework: **helping aspiring bug bounty hunters earn money while they learn**. This workflow takes a specific target URL and builds customized, hands-on lessons that teach real-world manual testing techniques using that actual target.

**Educational Philosophy:** While skilled bug bounty hunters can use this tool headless with complex scripts, the primary goal is education. The URL workflow bridges the gap between theoretical knowledge and practical application by providing guided, hands-on learning experiences with real targets.

**Status:** Currently under development. This represents the most ambitious educational component of the framework.

**Planned Educational Modules:**

1. **Client-Side Injection Testing**
   - **Discovery:** Automatically identifies locations where user input is reflected in the DOM
   - **Classification:** Guides users through determining if reflection is stored or reflected
   - **Manual Testing:** Step-by-step walkthrough of testing various XSS payloads
   - **Automation:** Provides automated tools to validate findings and complete the learning process

2. **Server-Side Vulnerability Assessment**
   - **SQL Injection:** Interactive lessons on identifying and exploiting database vulnerabilities
   - **Command Injection:** Hands-on training for OS command injection discovery and exploitation
   - **File Upload Vulnerabilities:** Guided exercises in bypass techniques and payload crafting

3. **Authentication and Authorization**
   - **Session Management:** Dynamic lessons on session token analysis and manipulation
   - **Access Control:** Interactive training on privilege escalation and authorization bypass
   - **Multi-Factor Authentication:** Hands-on exercises in MFA bypass techniques

4. **Business Logic Vulnerabilities**
   - **Workflow Manipulation:** Target-specific lessons on business process exploitation
   - **Parameter Tampering:** Interactive exercises in logical flaw discovery
   - **Race Conditions:** Hands-on training for timing-based vulnerabilities

5. **Advanced Techniques**
   - **CSRF and SSRF:** Personalized lessons based on target architecture
   - **XXE and Deserialization:** Target-specific payload development and testing
   - **API Security:** Interactive lessons on REST/GraphQL vulnerability discovery

**Learning Methodology:**
Each module follows the proven "Discover → Understand → Test → Validate" approach:
- **Discover:** Automated tools find potential vulnerability locations
- **Understand:** Educational content explains the vulnerability class and impact
- **Test:** Guided manual testing with target-specific examples and payloads
- **Validate:** Automated verification tools confirm findings and reinforce learning

**Real-World Application:** By using actual targets instead of synthetic labs, students learn to navigate real-world challenges like WAFs, rate limiting, and complex application logic - preparing them for successful bug bounty hunting careers.

**Current Alternative:** While the URL workflow is in development, students can use the Wildcard workflow to discover targets, then apply manual testing techniques learned through external resources.

## Troubleshooting

This section covers common issues you may encounter when setting up and running the Ars0n Framework v2. Most problems are related to Docker configuration or system requirements.

### Docker Not Installed

**Error:** `docker: command not found` or `docker-compose: command not found`

**Solution:**
- **Windows:** Download and install [Docker Desktop for Windows](https://docs.docker.com/desktop/install/windows-install/)
- **Mac:** Download and install [Docker Desktop for Mac](https://docs.docker.com/desktop/install/mac-install/)
- **Linux (Ubuntu/Debian):**
  ```bash
  sudo apt update
  sudo apt install docker.io docker-compose
  sudo systemctl start docker
  sudo systemctl enable docker
  sudo usermod -aG docker $USER
  ```

### Verify Docker Installation

Before running the Ars0n Framework, test your Docker installation with these simple examples:

**Test Docker:**
```bash
docker run hello-world
```

You should see output like:
```
Hello from Docker!
This message shows that your installation appears to be working correctly.
```

**Test Docker Compose:**

Create a file named `test-docker-compose.yml`:
```yaml
services:
  hello-world:
    image: hello-world
    container_name: test-hello-world
```

Then run:
```bash
docker-compose -f test-docker-compose.yml up
```

You should see the same hello-world message. If both tests pass, your Docker installation is working correctly and you can proceed with the Ars0n Framework.

### Docker Service Not Running

**Error:** `Cannot connect to the Docker daemon` or `docker daemon is not running`

**Solution:**
- **Windows:** Start Docker Desktop application
- **Mac:** Start Docker Desktop application
- **Linux:**
  ```bash
  sudo systemctl start docker
  sudo systemctl status docker
  ```

### Permission Denied Errors

**Error:** `permission denied while trying to connect to the Docker daemon socket`

**Solution:**
- **Linux:** Add your user to the docker group and restart your session:
  ```bash
  sudo usermod -aG docker $USER
  newgrp docker
  ```
- **Windows/Mac:** Ensure Docker Desktop is running with appropriate permissions

### Port Conflicts

**Error:** `port is already allocated` or `bind: address already in use`

**Solution:**
- Check if ports 3000, 8000, 8443, or 5432 are already in use:
  ```bash
  # Linux/Mac
  sudo netstat -tulpn | grep :3000
  sudo netstat -tulpn | grep :8443
  
  # Windows
  netstat -ano | findstr :3000
  netstat -ano | findstr :8443
  ```
- Stop conflicting services or modify the docker-compose.yml to use different ports

### Insufficient Resources

**Error:** `no space left on device` or `memory allocation failed`

**Solution:**
- **Windows/Mac:** Increase Docker Desktop memory allocation (8GB+ recommended)
- **Linux:** Check available disk space and memory:
  ```bash
  df -h
  free -h
  ```
- Clean up Docker resources:
  ```bash
  docker system prune -a
  docker volume prune
  ```

### Corporate/Enterprise Docker Restrictions

**Error:** `authentication required` or `registry access denied`

**Solution:**
- Configure Docker to use your organization's registry:
  ```bash
  docker login your-company-registry.com
  ```
- Update docker-compose.yml to use authenticated image sources
- Contact your IT department for Docker Enterprise configuration

### Docker-in-Docker (DinD) Issues

**Error:** `Cannot connect to the Docker daemon` when running inside containers

**Solution:**
- Ensure Docker socket is properly mounted in docker-compose.yml
- For enterprise environments, configure Docker BuildKit:
  ```bash
  export DOCKER_BUILDKIT=1
  docker-compose up --build
  ```

### Database Connection Issues

**Error:** `connection refused` or `database is starting up`

**Solution:**
- Wait for the database to fully initialize (health check may take 30+ seconds)
- Check database container logs:
  ```bash
  docker logs ars0n-framework-v2-db-1
  ```
- Restart the database service:
  ```bash
  docker-compose restart db
  ```

### Container Build Failures

**Error:** `failed to build` or `build context`

**Solution:**
- Ensure all required files are present in the project directory
- Check Dockerfile syntax and dependencies
- Clear Docker build cache:
  ```bash
  docker builder prune
  docker-compose build --no-cache
  ```

### Network Connectivity Issues

**Error:** `network unreachable` or `DNS resolution failed`

**Solution:**
- Check if your firewall is blocking Docker network traffic
- Configure DNS settings in docker-compose.yml if needed
- For corporate networks, configure proxy settings:
  ```bash
  export HTTP_PROXY=http://proxy.company.com:8080
  export HTTPS_PROXY=http://proxy.company.com:8080
  ```

### Windows-Specific Issues

**Error:** `WSL 2 installation is incomplete` or `Hyper-V not enabled`

**Solution:**
- Enable WSL 2: `wsl --install`
- Enable Hyper-V: `Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Hyper-V -All`
- Restart your computer after making these changes

### Mac-Specific Issues

**Error:** `Docker Desktop is not running` or `resource limits exceeded`

**Solution:**
- Increase Docker Desktop memory allocation (8GB+ recommended)
- Ensure Docker Desktop has necessary permissions
- Check macOS security settings for Docker

### Linux-Specific Issues

**Error:** `cgroup memory limit exceeded` or `seccomp not supported`

**Solution:**
- Update your kernel to a recent version
- Install required packages:
  ```bash
  sudo apt install linux-modules-extra-$(uname -r)
  ```
- Configure cgroup limits in /etc/docker/daemon.json

<p align="right">~ by darshak w/ ❤️</p>
<p align="center"><em>Copyright (C) 2025 Darshak Security, LLC</em></p>
