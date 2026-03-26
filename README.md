<div align="center">
  <br />
  <img src="https://api.iconify.design/lucide/scan-line.svg?color=%230ea5e9" width="56" alt="radar" />
  <h1>E A S Y R E C O N</h1>
  <p><strong>The recon command you run before anything else.</strong></p>

  <p>
    <img src="https://img.shields.io/badge/version-1.0.0-0ea5e9?style=for-the-badge&labelColor=f8fafc&color=0ea5e9" alt="Version" />
    <img src="https://img.shields.io/badge/build-passing-10b981?style=for-the-badge&labelColor=f8fafc&color=10b981" alt="Build" />
    <img src="https://img.shields.io/badge/license-MIT-64748b?style=for-the-badge&labelColor=f8fafc&color=64748b" alt="License" />
  </p>


</div>


> **Stop wasting the first hour of every engagement setting up your tools.**  
> `easyrecon` strips away the friction. Run one command, get a perfectly categorized attack surface, and jump straight into hunting. 

<br />

## <img src="https://api.iconify.design/lucide/target.svg?color=%230ea5e9" width="24" align="top" /> Why You Must Have EasyRecon

If you do bug bounty or pentesting, you already know the pain: every new target starts with the exact same repetitive setup work. Chaining `subfinder`, piping to `httpx`, digging through text files for API endpoints. 

**EasyRecon handles the heavy lifting for you automatically.**

<table width="100%">
  <tr>
    <td width="33%" align="center" valign="top">
      <br />
      <img src="https://api.iconify.design/lucide/zap.svg?color=%230ea5e9" width="32" /><br />
      <br />
      <strong>Save 60 Minutes</strong><br />
      <span style="color:#64748b;">No manual configurations or chaining scripts. Just run the command and get to work.</span>
      <br /><br />
    </td>
    <td width="33%" align="center" valign="top">
      <br />
      <img src="https://api.iconify.design/lucide/maximize.svg?color=%2314b8a6" width="32" /><br />
      <br />
      <strong>Miss Nothing</strong><br />
      <span style="color:#64748b;">It runs 7 trusted industry tools in parallel, then cleanly merges the results.</span>
      <br /><br />
    </td>
    <td width="33%" align="center" valign="top">
      <br />
      <img src="https://api.iconify.design/lucide/search-code.svg?color=%23f59e0b" width="32" /><br />
      <br />
      <strong>Hunt Faster</strong><br />
      <span style="color:#64748b;">It automatically parses exactly where admin panels, APIs, and sensitive files live.</span>
      <br /><br />
    </td>
  </tr>
</table>

<br />

## <img src="https://api.iconify.design/lucide/workflow.svg?color=%230ea5e9" width="24" align="top" /> The Orchestration Pipeline

What exactly happens when you run `easyrecon target.com`:

```mermaid
flowchart LR
    %% Styling
    classDef primary fill:#f0f9ff,stroke:#0ea5e9,stroke-width:2px,color:#0369a1
    classDef secondary fill:#ffffff,stroke:#cbd5e1,stroke-width:1px,stroke-dasharray: 4 4

    A[Target Domain]:::primary --> B[Subdomains]:::primary
    B --> C[URLs]:::primary
    C --> D[Live Hosts]:::primary
    D --> E[Categorize]:::primary
    E --> F[Report]:::primary

    B -.- B1[subfinder]:::secondary
    B -.- B2[amass]:::secondary
    B -.- B3[assetfinder]:::secondary

    C -.- C1[gau]:::secondary
    C -.- C2[waybackurls]:::secondary
    C -.- C3[katana]:::secondary

    D -.- D1[httpx]:::secondary
```

<br />

## <img src="https://api.iconify.design/lucide/folder-kanban.svg?color=%230ea5e9" width="24" align="top" /> Smart Attack Surface Sorting

Instead of combing through monolithic, messy text files, `easyrecon` acts like an analyst and automatically buckets your targets. **You know exactly where to strike first.**

| Priority | Category | Match Signatures |
| :--- | :--- | :--- |
| <img src="https://api.iconify.design/lucide/alert-octagon.svg?color=%23f43f5e" width="18" align="top" /> **High** | `sensitive` | `.git`, `.env`, backup directories, `/config`, `/actuator` |
| <img src="https://api.iconify.design/lucide/shield-alert.svg?color=%23f43f5e" width="18" align="top" /> **High** | `admin` | `/admin`, `/panel`, `/dashboard`, control interfaces |
| <img src="https://api.iconify.design/lucide/key-round.svg?color=%23f43f5e" width="18" align="top" /> **High** | `login` | `/login`, `/auth`, `/sso`, `/wp-admin` |
| <img src="https://api.iconify.design/lucide/unplug.svg?color=%23f59e0b" width="18" align="top" /> **Med** | `api` | `/api`, `/v1`, `/graphql`, `/swagger` |
| <img src="https://api.iconify.design/lucide/variable.svg?color=%23f59e0b" width="18" align="top" /> **Med** | `params` | URLs exposing testable parameters (`?id=`, `?url=`) |
| <img src="https://api.iconify.design/lucide/upload-cloud.svg?color=%23f59e0b" width="18" align="top" /> **Med** | `upload` | File endpoints, `/import`, `/media` |
| <img src="https://api.iconify.design/lucide/info.svg?color=%2364748b" width="18" align="top" /> **Info** | `js` `json` `php` | Technology-specific endpoint groups |

<br />

## <img src="https://api.iconify.design/lucide/terminal-square.svg?color=%230ea5e9" width="24" align="top" /> Quick Start

### 1. Requirements
* Python 3.8+
* Go *(required for automated tool installation)*

### 2. Install
```bash
git clone https://github.com/unrealsrabon/easyrecon
cd easyrecon
chmod +x install.sh
./install.sh
```

### 3. Usage
```bash
# Kick off a full orchestration
easyrecon target.com

# Focus on a specific phase
easyrecon target.com --phase subdomain

# Customize the execution
easyrecon target.com --timeout 60 --output ~/recon-results
```

<br />

## <img src="https://api.iconify.design/lucide/settings.svg?color=%230ea5e9" width="24" align="top" /> Configuration

Tailor `easyrecon` perfectly to your environment by mapping out a `~/.easyrecon.yaml`:

```yaml
tools:
  amass:
    enabled: false             # Skip heavy execution
  subfinder:
    timeout: 60                # Cap runtime limit
    extra_args: "-recursive"   # Feed custom flags

settings:
  output_dir: "~/results"
  threads: 50
  auto_install: true
```

<br />

## <img src="https://api.iconify.design/lucide/book-open-check.svg?color=%230ea5e9" width="24" align="top" /> Legal & License

**Disclaimer:** Only point `easyrecon` at assets you own or possess explicit, written permission to test. Unauthorized scanning is actionable and illegal.

Released under the **MIT License**.  
Crafted by [@unrealsrabon](https://github.com/unrealsrabon) — part of the *ai-will-replace-developers* initiative.
