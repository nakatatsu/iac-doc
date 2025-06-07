# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

MCP IaC Doc is a documentation server that provides Infrastructure as Code (IaC) documentation to AI agents. It contains comprehensive guidelines, templates, and specifications for developing Terraform modules for AWS infrastructure.

## Key Development Commands

- 

## Architecture and Structure

- 

## Critical Project Standards

**Project Configuration:**
- Cloud Provider: AWS
- Project Name: mcp


## Development Workflow

When developing Terraform modules, follow the standard task process:

1. Create feature branch
2. Generate module skeleton (`make prepare handson`)
3. Update module README with purpose and requirements
4. Create specification.yaml based on requirements
5. Generate Terraform code following templates
6. Update terraform.tfvars.json with required variables
7. Run validation tools in order: fmt → init → validate → tflint → checkov → plan
8. Generate documentation with terraform-docs
9. Commit and create pull request

Always check `resouces_specification/` for resource-specific rules before implementing AWS services.