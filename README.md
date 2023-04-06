# cloud-infra


A.  Basic Web Server:   BasicWebServerInVPC.template

    This CloudFormation (Infrastructure as Code) creates a VPC, Subnet and an EC2 instance in running that to serve a 
    basic web page. This is a reference implementation of:
    https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/working-with-templates-cfn-designer-walkthrough-createbasicwebserver.html

    You need to ensure that EC2 Key pair is created in the appropriate AWS region and referred for SSH access to the host.
    It is supporting HTTP at present.

    The URL to check is: http://3.90.108.39/

    Next steps to scale this setup, use Load Balancers as explained in:
    https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/working-with-templates-cfn-designer-walkthrough-updatebasicwebserver.html


B.  CloudFront based Static Web Page:   HttpsCfnWebServer.template

    This is an implementation where we leverage CloudFront CDN of AWS to scale as the load increases. There is no
    EC2 instance deployment, simple a static page on a S3 bucket from where it is picked and rendered. In addition to
    scaling, it also achieves HTTS (and redirection from HTTP to HTTPS). 

    THe URL is: https://d153iujs9e2gto.cloudfront.net/

    TODO:   mapping to a DNS with it's own certificate (resources are all created).

C.  TODO: 
        - Combined implementation of A with LoadBalancer + B
        - An integration test in Go lang to do HTTPS call to get Ok response.

    