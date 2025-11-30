# pySigma Community Pipelines

<a href="https://sigmahq.io/">
<p align="center">
<br />
<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/SigmaHQ/sigma/master/images/sigma_logo_dark.png">
  <img width="454" alt="Sigma Logo" src="https://raw.githubusercontent.com/SigmaHQ/sigma/master/images/sigma_logo_light.png">
</picture>
</p>
</a>
<br />

<p align="center">
<a href="https://sigmahq.io/"><img src="https://cdn.jsdelivr.net/gh/SigmaHQ/sigmahq.github.io@master/images/Sigma%20Official%20Badge.svg" alt="Sigma Official Badge"></a>
<img alt="GitHub Repo stars" src="https://img.shields.io/github/stars/SigmaHQ/pySigma-community-pipelines">
</p>

Welcome to the pySigma Community Pipelines repository, the central hub for community-shared processing pipelines.

## What are Processing Pipelines?

Processing pipelines provide granular control over how Sigma rules are converted into SIEM-specific formats. They enable among other things:

* **Field Mappings** - Convert generic field names to platform-specific equivalents (e.g., `CommandLine` → `process.command_line` for ECS, or `process` for Splunk)
* **Log Source Mappings** - Map Sigma log sources to data source identifiers (e.g., `category: process_creation` → `winlog.channel: Microsoft-Windows-Sysmon/Operational`)
* **Value Transformations** - Adjust field values for platform requirements (e.g., converting boolean values, handling data types)
* **Conditional Logic** - Add platform-specific search conditions (e.g., index names, source types)

## 🗂️ Repository Structure

The repository is organized by platform type:

* **[elastic_pipelines/](./elastic_pipelines/)** - Pipelines for Elastic Stack / ECS (Elasticsearch, Kibana, ElastAlert).
* **[splunk_pipelines/](./splunk_pipelines/)** - Pipelines for Splunk SIEM and Splunk Enterprise Security.
* **[pipeline_examples/](./pipeline_examples/)** - Comprehensive examples demonstrating all transformation types currently supported by pySigma.

## 🚀 Usage

### Using Sigma CLI

Convert Sigma rules using pipelines with [sigma-cli](https://github.com/SigmaHQ/sigma-cli):

```bash
sigma convert -t splunk -p splunk_pipelines/splunk_sysmon.yml rules/windows/process_creation/
```

## 🔎 Contributing

We welcome contributions of new pipelines and improvements to existing ones!

This repository thrives on community involvement to expand the collection of processing pipelines for various security platforms.

### How to Contribute

1. **Fork the repository** and create a feature branch
2. **Create or modify pipelines** in the appropriate directory
3. **Test your pipeline** with example Sigma rules
4. **Document your changes**
5. **Submit a pull request** with a clear description

### Related Projects

* [Sigma Rules](https://github.com/SigmaHQ/sigma) - Main Sigma detection rule repository
* [pySigma](https://github.com/SigmaHQ/pySigma) - Core Python library for Sigma rule processing
* [sigma-cli](https://github.com/SigmaHQ/sigma-cli) - Command-line tool for Sigma rule conversion

## 📜 Maintainers

* [Nasreddine Bencherchali (@nas_bench)](https://twitter.com/nas_bench)
