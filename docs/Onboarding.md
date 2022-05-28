# Onboarding

Welcome to RACTF Cloud! To get you up and running, please collect and return the below details.

* Event Name
* Domain
  * We support custom domains, but given the extra work involved, we recommend you select a subdomain of `ractf.cloud`. Our team will manage this for you.
* Event start and end times
* Logo (SVG)
* Estimated user numbers
  * Registered users
  * Simultaneous users
* Platform features requiring development
  * If you're not sure if we support something, please ask. We're happy to enhance the open source project, but would rather not ship features last minute.
* Challenge hosting requirements
  * Single-user challenge containers?
* Grafana access required?
  * We expose a limited subset of statistics directly through the platform, but we can provide access to a Grafana instance with additional details if required.
  * Please specify what email addresses we should invite to Grafana.
* Google Analytics token
  * If you do not provide a token, we will use a generic token on your deployment for our internal analytics.

Once you've supplied these details, we will deploy an instance of RACTF [Core](https://github.com/ractf/core) onto our infrastructure, RACTF [Shell](https://github.com/ractf/shell) onto AWS, and create a namespace on a shared instance of RACTF [Polaris](https://github.com/ractf/polaris). If you are interested in the automation we use here, please reach out to the infrastructure team for a walkthrough.

For guidance on publishing challenge containers, check out [this](/registry) page. Your RACTF team are available to provide whatever assitance you require.

Good luck with your event!
