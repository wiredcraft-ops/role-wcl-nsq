# encoding: UTF-8

Vagrant.configure('2') do |config|
  config.vm.box = 'centos/7'
  config.vm.synced_folder ".", "/vagrant", disabled: true
  config.vm.provision 'ansible' do |ansible|
    ansible.playbook = 'vagrant/site.yml'
    ansible.limit = 'all'
    ansible.become = true
    ansible.host_key_checking = false
    # ansible.verbose = "vvv"
    ansible.groups = {
      'nsq' => ['nsqd-1', 'nsqd-2', 'nsqd-3'],
      'nsqadmin' => ['nsqd-1', 'nsqd-2', 'nsqd-3'],
      'nsqd' => ['nsqd-1', 'nsqd-2', 'nsqd-3'],
      'nsqlookupd' => ['nsqd-1', 'nsqd-2', 'nsqd-3']
    }
    ansible.extra_vars = {
      nsq_nsqd_interface: 'eth1',
      nsq_nsqadmin_interface: 'eth1',
      nsq_nsqlookupd_interface: 'eth1'
    }
  end

  (1..3).each do |i|
    vm_name = "nsqd-#{i}"
    config.vm.define vm_name do |c|
      c.vm.host_name = vm_name
      c.vm.network 'private_network', ip: "192.168.30.#{11 + i}" # eth1
    end
  end
end
