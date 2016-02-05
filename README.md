# Chef-Provisioning

Steps to work on Chef-Provisioning on AWS-EC2

Creating credentials file and as per below format:
No quotes are needed for the key values.
1.  create ~/.aws/credentials 

<h4>[default]</h4>
<p>
   aws_access_key_id = XXXXXXXXXXXXXXXX</br>
   aws_secret_access_key = XXXXXXXXXXXXXXXXX</br> 
   region = us-west-2</br>
</p>
2. Create simple.rb file as below:

machine 'demo' do
  recipe 'apache'
end

with_machine_options({
  bootstrap_options: {
    image_id: "ami-5915e11d", # default for us-west-1
    instance_type: "t2.micro",
    key_name: "chef-analytic", # If not specified, this will be used and generated
    key_path: "/home/munusamy/Downloads/", # only necessary if storing keys some other location
  },
  use_private_ip_for_ssh: false, # DEPRECATED, use `transport_address_location`
  transport_address_location: :public_ip, # `:public_ip` (default), `:private_ip` or `:dns`.  Defines how SSH or WinRM should find an address to communicate with the instance.
})

3. Execute "chef-client -z simple.rb"

