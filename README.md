# ansible-nfs-gcp
# 🚀 Ansible GCP Instance Creation

This project uses **Ansible** to automate the creation of a **Google Cloud Platform (GCP)** virtual machine instance.

---

## 📌 Prerequisites

-  Ansible installed
-  Google Cloud SDK configured
-  GCP service account key in JSON format
-  SSH key pair (`id_rsa`, `id_rsa.pub`) generated
-  Python packages installed:
  ```bash
  pip install google-auth requests google-api-python-client
  ```

---

## ⚙️ What It Does

1. Loads your local public SSH key
2. Installs required Python packages via pip
3. Creates a GCP instance using the provided configuration
4. Writes instance details to `gcp_instance.json`
5. Generates a dynamic Ansible inventory file

---

## 🛠 How to Use

### 1. Modify Your Variables

Update variables inside `playbooks/create-gcp-instance.yaml`:

```yaml
vars:
  machine_name: master1
  google_project_id: your-project-id
  service_account_path: /path/to/service_account.json
  ssh_public_key_path: /path/to/id_rsa.pub
```

---

### 2. Run the Playbook

```bash
ansible-playbook playbooks/create-gcp-instance.yaml
```

---

## 🔑 SSH into the Instance

After the playbook runs successfully, connect via:

```bash
ssh your-username@instance-public-ip
```

Replace `your-username` and `instance-public-ip` with actual values.

---

## 📁 Project Structure

```
.
├── playbooks/
│   └── create-gcp-instance.yaml
├── tasks/
│   └── create-gcp-task.yaml
├── dynamic_inventory.json
├── gcp_instance.json
```

---

## ✅ Output Example

```bash
PLAY RECAP
localhost : ok=6 changed=3 unreachable=0 failed=0
```

---

## 📬 Notes

- Ensure your service account has necessary IAM roles (e.g., Compute Admin).
- Make sure the firewall rules allow SSH (port 22) access.
## by sivthingthing
