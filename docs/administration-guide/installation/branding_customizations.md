---
title: Branding Customizations
layout: default
summary: Configuring OntoPortal for your own project
status: In progress
nav_order: 7
parent: Installing OntoPortal
grand_parent: Administration Guide
permalink: /administration/steps/branding-customizations
---

# Branding Customizations

## Why brand your appliance?

If you're running a public version of the {{site.opva}}, 
you've probably already started to think about how to present your site.
Having a unique name, logo, and unifying colors lets users
recognize and associate good things with your site.
And it makes your site look good!

Even if you have a private ontology for your own research, 
just a few hours customizing its look and feel 
can help you distinguish it from BioPortal and other Appliances,
and can give your presented materials a distinctive presence.
Slides, web pages, and even papers can benefit from the colorful 
views of your OntoPortal Appliance content. 


## What gets customized? 

It's up to you. A reasonable first step would be to update the URL of the site,
header (the logo, and the color), and perhaps the footer. 

It's only slight more involved to add a favicon (for the browser bar), 
and a customized welcome and tagline on the home page.

AgroPortal (https://agroportal.lirmm.edu) provides an example 
where many elements adopt the parent color. 
(Note this screenshot reflects a pre-3.0-release interface technology.)

<figure>
  <img src="{{site.baseimgs}}/agroportal-color-scheme-2020.png" style="width:100%"/>
  <figcaption>An example of elements that can be colored for the theme</figcaption>
</figure>

## How do I do it?

First, review the instructions in the <a href="{{site.baseurl}}/administration/steps/advanced_configuration">Advanced Configuration</a> section. Our example is based on the Advanced Customization instructions at the end of that document.

### 1 set URL for appliance:
ssh to appliance and change user to ontoportal. 

```bash
[ubuntu@appliance ]$ sudo su - op-admin
``` 
edit `/opt/ontoportal/config/site_config.rb` and set:

```
$REST_HOSTNAME = 'appliance.ontoportal.org'
$REST_PORT = '8443'
$REST_URL_PREFIX = 'https://appliance.ontoportal.org'
$UI_HOSTNAME = 'appliance.ontoportal.org'
$SITE = 'Demo OntoPortal Appliance'

```

### 2. Add custom logo and change the color of the header.

1. Copy your custom logo file to `/opt/ontoportal/virtual_appliance/appliance_config/bioportal_web_ui/app/assets/images/logos/bioportal-logo.png`
2. the Copy original theme color variables scss file
```bash
cp /opt/ontoportal/virtual_appliance/deployment/bioportal_web_ui/app/assets/stylesheets/theme-variables.scss.erb
/opt/ontoportal/virtual_appliance/appliance_config/bioportal_web_ui/app/assets/assets/stylesheets`
```
then change change variables like `primary`, `secondary`, `light` variables in the ontoportal section:

 ```ruby
  "ontoportal"  => {
    primary: "#5499a4",
    hover: "#6B96B7",
    secondary: "#ffc107",
    light: "#F1F6FA",
    bg_chip_button_container: "#777777" ,
    text_chip_button_container: "#FFFFFF !important",
    login_btn: "#F1F6FA",
    login_btn_hover_bg: "#CCCCCC",
  },
```

### 3. Update tagline on the main page:
1. edit `/opt/ontoportal/virtual_appliance/appliance_config/bioportal_web_ui/config/locales/en/appliance-overrides.yml`
 and modify line containing
   `tagline: your ontology repository for your ontologies`

### 4. Update footer
1. Copy original footer from
`/opt/ontoportal/virtual_appliance/deployment/bioportal_web_ui/views/application/./views/_footer_appliance.html.haml` to
`/opt/ontoportal/virtual_appliance/appliance_config/bioportal_web_ui/views/application/./views/_footer_appliance.html.haml`
and make your modifications.

if `/opt/ontoportal/virtual_appliance/deployment/bioportal_web_ui/` is not present then you would need to set up deployment environment by running ./setup_deploy_env.sh

### 5. Run deployment

Once all configuration changes and file overwrites are set you would need to run deployment scripts. 
Deployment process described in <a href="{{site.baseurl}}/administration/steps/advanced_configuration">Advanced Configuration</a> 


## Do you have some artwork I can use?

You may use the following OntoPortal logo if it helps. 
(We will be adding some more logos, please contact us for details.)
<figure>
  <img src="{{site.baseimgs}}/OntoPortal-Logo-Circle.png"/>
  <figcaption>The OntoPortal logo</figcaption>
</figure>
