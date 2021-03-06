Written By: Thu Le, Michael R, Joairia C, Duc T. Doan

![image](https://images.prismic.io/www-static/e7798719-3af9-42bf-8273-04f02108383f_digitalocean-vpc-blog-1.jpg?auto=compress,format)
[[1] Image Source ](https://www.digitalocean.com/blog/vpc-trust-platform/)

# Brief History 

DigitalOcean is an American cloud company which provides cloud hosting server provisioning, with a focus on software developers. DigitalOcean was founded by Ben and Moisey Uretsky in June 24th, 2011. The Uretskys had already established a company back in 2003 called Server Stack, which was a managed hosting business. Most companies at the time were only targeting corporate clients who required a cloud infrastructure to manage their servers on a larger scale. They were ambitious to fulfill that gap and create a profitable future for themselves. None of the companies among the competitors were targeting individual software developers and small-scale companies as their potential customers. Due to this Ben and Moisey were ambitious and wanted to get rid of that gap, and wanted to create a new product which would combine the web hosting and virtual servers for the untapped market. After extensive research, Ben and Moisey Uretsky founded DigitalOcean; a company that provides cloud hosting services and server provisioning for individual users and small-scale start-ups making it easy for them to host their websites with one-click solutions.

In 2012 the Uretskys met co-founder Mitch Wainer, following Wainer's response to a Craigslist job listing. The company launched their beta product in January 2012 and became a part of a start-up accelerator program by none other than TechStars. By the end of this start-up accelerator program, the company was able to sign up nearly 400 customers and provided more than 10,000 instances of cloud servers. At the beginning of 2013, it’s among the first few companies to offer SSD-based virtual machines for a seamless experience. On January 16th, 2018, new droplet (virtual machines) plans were introduced on their blog. In May 2018, the company announced the launch of its Kubernetes-based container service.



# What is DigitalOcean?


DigitalOcean is a scalable cloud service provider, that offers cloud services comparable to Azure and AWS. It's main focus since the beginning has been a cloud infrastructure solution built towards software developers since it has a focus on application support and you're able to run your applications parallel across the multiple cloud servers. Anyone looking into cloud solutions would find DigitalOcean as a great contender to other cloud services due to its easy to navigate GUI, incredible prices and the community that surrounds it offering support, tutorials and much more. DigitalOcean has 12 datacenters around the globe which with reduce latency due to ability to scale out to the different regions depending where you are.


DigitalOcean is a provider of VPS or "Droplets" using KVM as the hypervisor, it offers high quality server hosting, diverse VPS configurations suitable for all hosting needs. DigitalOcean provides a service called One-Click Apps which is great for growing businesses due to scalability. These One-Click apps allow you to start a Droplet with many features pre-configured, which allows the user to start quickly when working with pre-existing VPS so they don’t have to waste time on configuration or starting fresh. There is a vast amount of VPS offered, installed with features like WordPress, LAMP Stack, LEMP Stack, MEAN, Docker and many more options which allows for quick access to these pre-built applications on the VPS. Recently DigitalOcean has setup a way for users to upload custom operating system files to install to other users and their company. 


DigitalOcean has many features, all their servers are run on SSD disks, their control panel is easy to navigate, all of DigitalOceans servers are built with the latest and best optimized hardware making it a contender against other popular cloud services. These VPS that are accessible from DigitalOcean and offer many options which will be discussed in the example portion of this page.




# Who owns DigitalOcean?

In 2011, Uretskys founded DigitalOcean a private American Cloud infrastructure company, which aims to "provide cloud hosting services and server provisioning for individual software developers and small-scale start-ups" [2], to help them get closer to the big technologies and bring a Excellent management tool. The company was under the leadership of the former CEO of Citrix, Mark Templeton who took over from Ben Uretsky in April 2016 till 2019. However, at this moment, the company is under the leadership of Yancey Spruill, former CFO and COO of SendGrid (a fellow Techstars company)" [3]. Any user around the world has the ability to purchase and use the services provided by DigitalOcean which has a great support community and different rates that each customer may choose whatever the best option for them is. 

# How to use DigitalOcean

DigitalOcean has 12 Datacentre’s around the world which all work together on running the DigitalOcean cloud infrastructure. By meeting the requirements set by the server, the user can create a Virtual Private Server (container). A VPS is a virtual machine, which uses part of the server's resources (CPU, RAM, HDD) and runs a copy of its own operating system and provides user (root) access to the clients of DigitalOcean. This means that each customer has the right to create what they want, which can have a separate container, running the chosen operating system. Customers have administrator access to the VPS, so they can change without fear of conflicts with other users who have the same containers on the same Digital Ocean server. 

If a user is unsure on how to use DigitalOcean, you want to start with purchasing whatever type of services you need online from DigitalOceans website. Once you have bought your service with DigitalOcean you're able to start creating VPS through their services, from there it is up to the user to do what they want. You can run fresh VPS or install preconfigured VPS on your server and use tutorials and lots of other support offered to start building your company with DigitalOcean, which is totally scalable if the user wants to add anything to it in the future. With DigitalOcean, you will have your own server, you have full control, you're able to set parameters, select applications and most importantly you can customize the services accordingly. Find below an image showing how one company used DigitalOcean to build their infrastructure. 

![Image](https://images.prismic.io/www-static/9528bc0c-1196-42dc-9d01-92968d0dbeba_content-ignite-digitalocean-infrastructure.png?auto=compress,format)
[[5] Image Source](https://www.digitalocean.com/customers/content-ignite/)


# Examples of use

DigitalOcean started as a simple cloud infrastructure, however since then has grown to be so much more. As of now DigitalOcean offers a variety of services all based off their cloud infrastructure and datacenters, these options include Droplets, Kubernetes, Databases and Spaces. To get more in depth of their services that they offer you have the, Droplets and Kubernetes that you would use for computing. Space Object Storage and Volumes Block Storage for your Spaces. MySQL, PostgreSQL and Redis™ for your Managed Databases. VPC, Cloud Firewalls, Load Balancers, Floating IP’s and DNS for all of your networking needs. 

With all of these ways you could use DigitalOcean there are so many things that you can do with this product, in fact due to its many uses and great pricing it is a very popular alternative and actually is a strong competitor to Amazon Web Services.

On DigitalOceans website they have many forums discussing tutorials, overviews, featured articles of what is new and what other people are building and a vast amount of other resources to view how to use DigitalOcean and what to use it for. 

Some examples of usage of DigitalOcean that can be viewed straight from their website includes:

Using DigitalOcean API:
(This process is using the API to manage your Droplets. As well make sure to replace the TOKEN variable with your own token)

**Example: List all Droplets**

```
curl -X GET "https://api.digitalocean.com/v2/actions" \
	-H "Authorization: Bearer $TOKEN"
```

**Example: Create a New Droplet**

```
curl -X POST "https://api.digitalocean.com/v2/droplets" \
	-d'{"name":"My-Droplet","region":"nyc3","size":"s-1vcpu-1gb","image":"ubuntu-20-04-x64"}' \
	-H "Authorization: Bearer $TOKEN" \
	-H "Content-Type: application/json"
```

A great part of DigitalOcean is that it has so many tools that you're able to do so much with so many options available to the user. Additionally with the API, there are a large amount of various wrappers for the API, these wrappers for example can be used to integrate the API into a script or application. Find below an example of installing a wrapper for the API then creating a new Droplet with it.

**Install the wrapper (make sure to have RubyGems installed):**

`gem install droplet_kit`

**Create a new ruby script:**

`vi create_droplet.rb`

**Creating a new Droplet, with DropletKit (Make sure to your personal access token with write access):**

```
#!/usr/bin/ruby

require 'droplet_kit'
token='token'
client = DropletKit::Client.new(access_token: token)

droplet = DropletKit::Droplet.new(name: 'example.com', region: 'nyc3', size: 's-1vcpu-1gb', image: 'ubuntu-20-04-x64')
client.droplets.create(droplet)
```

This API Droplet example does not even scratch the surface of the possibilities of what a user can do or achieve with DigitalOcean. Users can create their entire servers, websites with all the MySQL database/storage needed, many software developers use it for building applications and so much more. DigitalOcean is a great place for small businesses to start because you can use DigitalOcean to scale and run parallel across multiple cloud servers, as the company grows.

**Here is a final example of how with DigitalOceans you can create floating IP's for your server:**

![Image](https://www.digitalocean.com/docs/images/floating-ips/ha-diagram-animated.76f7de975b2ca13263d081bbcd1b01b5915b400b40cb2c5348289701daf59fdb.gif)
[[6] Image Source](https://www.digitalocean.com/docs/networking/floating-ips/)

# _Sources_

[1] <https://www.digitalocean.com/blog/vpc-trust-platform/>

[1] <https://www.cloudways.com/blog/what-is-digital-ocean/#what-is-digitalocean>

[2] <https://en.wikipedia.org/wiki/DigitalOcean>

[3] <https://www.digitalocean.com/community/tags/one-click-install-apps>

[4] <https://www.whoishostingthis.com/hosting-reviews/digitalocean/>

[5] <https://www.digitalocean.com/customers/content-ignite/>

[6] <https://www.digitalocean.com/docs/apis-clis/api/example-usage/>

