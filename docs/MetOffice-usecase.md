# UK Met office#
provided by Luke Abraham

My particular use case is around the Met Office virtual machine, which I have ported to AWS
 
https://github.com/metomi/metomi-vms
 
(this is from the Met Office GitHub, which includes my AWS additions). I also have an Ansible version for AWS with the additional playbook and scripts to create instances and also make the VPC and bash scripts to spin-up instances based on a pre-saved image
 
https://github.com/theabro/aws-ukca
 
I’m sure that these could be improved – they are rather complex in places.
 
I recently did a blog for the SSI on this
 
https://www.software.ac.uk/blog/2022-07-12-using-virtual-machines-training
 
and the details of the use case were published in Geoscientific Model Development a few years ago (although this was pre-cloud, just using VirtualBox, but this essentially covers the workflow)
 
https://gmd.copernicus.org/articles/11/3647/2018/
 
I also presented at SeptembRSE last year on my use of the JASMIN Unmanaged Cloud for this
 
https://www.youtube.com/watch?v=X5mqO1dgc2c&t=108s
