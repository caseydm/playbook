# Playbook

This is a guide for building and supporting python-backed web applications for small-to-medium sized businesses. It is recommended for businesses that have one to three developers and hosting costs of less than $1,000 per month.

## Small business requirements

Many small businesses benefit from a custom web application. 

## Trusted Framework

I have worked with many small businesses, and have seen many ways to host a web application. Through lessons learned, I have built what I call the 'Trusted Framework', which is intended to meet these three goals: 

- Reliable and secure application hosting, with server setup, security patches, and backups built-in
- Simple and repeatable development process that allows for testing and previewing changes in isolated enivoronments
- Documented continuity to easily hand off application to another developer

To meet those goals I use the following tools and processes:

- Application is built using the [Django](https://www.djangoproject.com/) python framework
- Code is hosted on [GitHub](https://github.com/) using a private repository that is owned by the client
- Hosting is provided by [Heroku](https://www.heroku.com/)
- New features and bug fixes are tracked in [GitHub Issues](https://help.github.com/articles/about-issues/)
- Changes are pushed to a staging environment for review, then to production using [Heroku Flow](https://www.heroku.com/flow)
- Client and developer continuity is maintained in a README file in the root of the main GitHub repository

Let's walk through the reasonsing for these choices, starting with the one that provides the biggest impact.

### Why Heroku?

There are two ways to host a web site: managed and unmanaged. 

***Unmanaged Hosting***
An unmanaged web site is hosted using a raw server. This server is provided by Amazon Web Services (AWS), Digital Ocean, or Rackspace (to name a few) and typically comes with the Ubuntu linux operating system installed. The server must be carefully configured to ensure the security and performance of the web site. System administrators perform this function manually, or with scripts using server management tools such as Fabric and Ansible. 

For example, this is a Fabric script of mine that sets up a web server on Amazon Web Services. It secures the server, installs python, a web server (NGINX), and creates directories for the app.

Pros
- May be cheaper than managed hosting
- More flexibility to modify server with packages and services

Cons
- Complex setup
- Backups, staging environment, etc must be implemented by developer
- If not updated regularly with security patches and operating system updates, the server will become 'stale' and become vulnerable to attacks or downtime

***Managed Hosting***
Managed hosting utilizes linux servers to host your site. However, the hosting provider configures the servers for you and installs security patches as needed. Server setup scripts are not necessary with a managed hosting provider.

If you do not have an in-house team of system administrators, I highly recommend you use managed hosting for your application.

### Why Django?

Django is a battle-tested, well-documented framework that 

### Why host code and track issues using GitHub?




