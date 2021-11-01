# Goof - Snyk's vulnerable demo app, prepared for RHPDS! 
Welcome! This repo contains Snyk's [Goof](https://github.com/snyk/goof) app with some changes to run it on OpenShift. Goof is a vulnerable Node.js demo application, based on the [Dreamers Lab tutorial](http://dreamerslab.com/blog/en/write-a-todo-list-with-express-and-mongodb/).

[![Known Vulnerabilities](https://snyk.io/test/github/snyk/goof/badge.svg?style=flat-square)](https://snyk.io/test/github/snyk/goof)

This is the code for the Snyk workshop on Red Hat's Product Demo System (RHPDS)! The workshop guide can be found in the [snyk-rhpds](https://github.com/snyk-partners/snyk-rhpds) repo.

## Exploiting Vulnerabilities

This vulnerable app includes exploitable packages with known vulnerabilities. 

- [Mongoose - Buffer Memory Exposure](https://snyk.io/vuln/npm:mongoose:20160116)
- [st - Directory Traversal](https://snyk.io/vuln/npm:st:20140206)
- [ms - ReDoS](https://snyk.io/vuln/npm:ms:20151024)
- [marked - XSS](https://snyk.io/vuln/npm:marked:20150520)

The `exploits/` directory includes a series of steps to demonstrate each one.
