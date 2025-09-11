Perfect 👍 Here’s the same **README.md** in English, formatted for GitHub:

````markdown
# Ansible + Windows VM (VMware Workstation)

This project demonstrates how to manage a **Windows virtual machine** running on **VMware Workstation** using **Ansible**.  

---

## Setup Steps

### 1. Install prerequisites on the control machine (Linux)

```bash
sudo apt update
sudo apt install ansible python3-pip -y
pip install pywinrm
````

### 2. Prepare the Windows VM

Run the following commands in **PowerShell as Administrator**:

```powershell
# Enable WinRM
winrm quickconfig

# Allow Basic Auth and unencrypted connections
Set-Item WSMan:\localhost\Service\Auth\Basic -Value $true
Set-Item WSMan:\localhost\Service\AllowUnencrypted -Value $true

# Open firewall for WinRM
netsh advfirewall firewall add rule name="WinRM" dir=in action=allow protocol=TCP localport=5985
```

### 3. Define the inventory file

Create `inventory.yml`:

```yaml
all:
  hosts:
    windows_host:
      ansible_host: 192.168.56.101   # Windows VM IP
      ansible_user: Administrator
      ansible_password: YourPasswordHere
      ansible_connection: winrm
      ansible_winrm_transport: basic
```

### 4. Test the connection

```bash
ansible windows_host -i inventory.yml -m win_ping
```

Expected output:

```json
windows_host | SUCCESS => {
    "changed": false,
    "ping": "pong"
}
```

---

## Notes

* This setup only demonstrates the connection between **Ansible** and the **Windows VM**.
* Automatically adding the VM into the **VMware Workstation library** is not included. To achieve that, you may use tools like `vmrun` or VMware APIs.

---

## References

* [Ansible Documentation: Windows](https://docs.ansible.com/ansible/latest/os_guide/windows_guide/index.html)
* [VMware Workstation Automation (`vmrun`)](https://www.vmware.com/support/developer/vix-api/)

```

---

Do you also want me to add the **playbook example (copying Vagrantfile & running vagrant up)** to this README as a section? That way your repo shows the full workflow.
```
