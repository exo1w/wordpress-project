# WordPress on Kubernetes with AWS EFS & MySQL (Demo Project)

This is a demo project showing how to deploy a **WordPress website** on **Kubernetes** with **AWS EFS** for persistent storage and **MySQL** as the database.

---

## Project Highlights

- WordPress running in Kubernetes Pod(s) with **persistent storage**.
- MySQL database backend with separate Pod.
- AWS EFS used to store WordPress files (**themes, plugins, uploads**) reliably.
- LoadBalancer service exposes WordPress externally.
- Fully automated deployment with PVC & PV for EFS.

---

## Architecture
   +-----------------+
   |   LoadBalancer  |
   +--------+--------+
            |
     +------v------+
     | WordPress   |
     | Pod(s)      |
     +------+------+
            |
       +----v----+
       | EFS PV  |
       +----+----+
            |
     +------v------+
     |   MySQL Pod |
     +-------------+

     
---

## Quick Start

1. **Create EFS Access Point**  
   - Set POSIX UID/GID to `33:33` (matches WordPress container).  

2. **Deploy PersistentVolume & PersistentVolumeClaim**  
   - Connect WordPress Pod to EFS.  

3. **Deploy MySQL**  
   - Set database, user, and password (`wordpress`, `wpuser`, `myrootpassword`).  

4. **Deploy WordPress**  
   - Connect to MySQL service.
   - Mount EFS volume.  

5. **Expose via LoadBalancer**  
   - Access WordPress externally.

---

## Verification

- Open the LoadBalancer URL to complete WordPress setup.
- Upload files, themes, or plugins to check persistence on EFS.
- Ensure database connectivity and WordPress works as expected.

---

## Notes

- Always ensure **UID/GID matches between EFS and container**.
- For production: enable `WP_DEBUG`, configure backups, and scale WordPress pods.
- Use LoadBalancer with multiple pods for high availability.

---

## Author

**Mohammed Ahmed Abdelbar** – Full Stack / DevOps Enthusiast  
[GitHub](https://github.com/exo1w) | [LinkedIn](https://www.linkedin.com/in/mohammed-abdelbar)