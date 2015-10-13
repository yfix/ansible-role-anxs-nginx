nginx_install_method = ENV.key?('NGINX_INSTALL_METHOD') ? ENV['NGINX_INSTALL_METHOD'] : 'package'

Vagrant.configure('2') do |config|
  config.vm.define 'anxs' do |c|
    c.vm.box = 'ubuntu/trusty64'
    c.vm.network :private_network, ip: '192.168.88.16'
    c.vm.hostname = 'anxs.local'
    c.vm.provision 'ansible' do |ansible|
      ansible.playbook = 'test.yml'
      ansible.sudo = true
      ansible.host_key_checking = false
      ansible.extra_vars = {
        nginx_install_method: nginx_install_method
      }
    end
  end
end
