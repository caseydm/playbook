# Playbook

This is my guide for building and supporting python-backed web applications for small-to-medium sized businesses. It is recommended for businesses that have one to three developers and hosting costs of less than $1,000 per month.

## The Small Business Problem

Many small businesses can benefit from a custom web application. And it is normal to turn to a web development agency or expert to develop it. However, web agencies are building the application with more resources than the small business has access to. They may have access to server administrators, database experts, etc. This is useful for *building* the application. But what about maintenance and improvements? 

When an agency configures a server with custom scripts, you are locked into them for updates. It can be very difficult to move to another developer if anything changes in the relationship. Things that can change:
- Agency gets busy with bigger clients and response times slow
- Agency changes business model (often to a software company) and stops supporting clients
- Small business wants to reduce costs and find a lower cost developer

I've taken over applications from agencies and it is a scary process for the client. The code and performance is usually very good. But it often requires logging into the server as a root user to change anything. The server is often a single point of failure, hosting the staging and production versions of the site. The update process is custom and with unknown effects. The server packages are out of date. One bad move and the production site crashes. The new developer has to comb through every portion of the code to try and figure out what went wrong.

## Trusted Framework

 Through lessons learned, I have built what I call the 'Trusted Framework', which is intended to meet these three goals and solve the small business problem: 

- Reliable and secure application hosting, with server setup, security patches, and backups built-in
- Simple and repeatable development process that allows for testing and previewing changes in isolated enivoronments
- Documented continuity to easily hand off the application to another developer

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

My managed hosting provider of choice is Heroku. Heroku is built on top of Amazon Web Services. It is stable and reliable. THey make it incredibly easy to create and maintain a python application. Building on Heroku enforces best practices ([12 factor app](https://12factor.net/)) that will go with you if you decide to move to a different host.

Pros
- Security updates and backups provided, no need for system administrators
- Easy to deploy code and bring in new developers

Cons
- May cost more

### Why Django?

Django is a battle-tested, well-documented framework that 

### Why host code and track issues using GitHub?

### Why not Docker?






