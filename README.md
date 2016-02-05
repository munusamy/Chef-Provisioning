# Chef-Provisioning

<h3>Steps to work on Chef-Provisioning on AWS-EC2</h3>

<p>Creating credentials file and as per below format:
No quotes are needed for the key values.</p>
<h4>1.  create ~/.aws/credentials</h4> 

<h4>[default]</h4>
<p>
   aws_access_key_id = XXXXXXXXXXXXXXXX</br>
   aws_secret_access_key = XXXXXXXXXXXXXXXXX</br> 
   region = us-west-2</br>
</p>
<h4>2. Create simple.rb file as below:</h4>
<p>machine 'demo' do</br>
&nbsp;&nbsp;&nbsp;&nbsp;recipe 'apache'</br>
end</p></br>

<p>with_machine_options({</br>
  bootstrap_options: {</br>
  &nbsp;&nbsp;&nbsp;&nbsp; image_id: "ami-5915e11d", # default for us-west-1</br>
  &nbsp;&nbsp;&nbsp;&nbsp; instance_type: "t2.micro",</br>
  &nbsp;&nbsp;&nbsp;&nbsp; key_name: "chef-analytic", # If not specified, this will be used and generated</br>
  &nbsp;&nbsp;&nbsp;&nbsp; key_path: "/home/munusamy/Downloads/", # only necessary if storing keys some other location</br>
  &nbsp;&nbsp;&nbsp;&nbsp;},</br>
  &nbsp;&nbsp;&nbsp;&nbsp; use_private_ip_for_ssh: false, # DEPRECATED, use `transport_address_location`</br>
  &nbsp;&nbsp;&nbsp;&nbsp; transport_address_location: :public_ip, # `:public_ip` (default), `:private_ip` or `:dns`.  Defines how SSH or WinRM should find an address to communicate with the instance.</br>
})</p>

<h4>3. Execute</h4></br><p> "chef-client -z simple.rb"</p>
