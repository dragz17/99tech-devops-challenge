Provide your solution here:

# 🚨 **Troubleshooting High Memory Usage on NGINX Load Balancer**

## **Scenario**  
A VM running Ubuntu 24.04 with 64GB of storage is consistently running at 99% memory usage. The VM is responsible for running only one service: **NGINX** as a load balancer for upstream services.

---

## 🔍 **Troubleshooting Steps**

### **1. Initial Check**  
- Check memory and CPU usage:  
  ```bash
  free -h
  top
  htop
  ```

---

### **2. Check the NGINX Configuration That Might Cause Memory Leaks**  
- **Could it be from `worker_processes`?**  
- **Could it be from `worker_connections`?**  
- **Is the buffer size too large?**  

---

### **3. Check for Bugs or Memory Leaks**  
- Check the community for known issues; there might be problems with a certain module.

---

### **4. Evaluate Traffic Patterns (Maybe Due to DDoS?)**  
- Analyze the `access.log`:
  ```bash
  tail -f /var/log/nginx/access.log
  ```  
- Could it be a DDoS attack?

---

### **5. System Tuning**  
- Tune the `worker_processes` and `worker_connections`.  
- Update modules or NGINX if required.  
- Implement rate limiting, WAF (Web Application Firewall), and add memory limits.

---

## ⚡ **Possible Causes and Impacts**

### **1. Misconfigured NGINX Settings**
- **Cause:** Incorrect `worker_processes`, `worker_connections`, or buffer sizes.
- **Impact:** Memory exhaustion, slow response times.
- **Recovery:** Adjust settings to match traffic patterns and server capacity.

### **2. Memory Leaks in NGINX or Modules**
- **Cause:** Bugs in the NGINX core or third-party modules.
- **Impact:** Gradual increase in memory usage leading to service degradation.
- **Recovery:** Update NGINX, disable unnecessary modules, or apply patches.

### **3. High Traffic or DDoS Attack**
- **Cause:** Abnormal traffic patterns or malicious requests.
- **Impact:** Overwhelmed server resources and possible downtime.
- **Recovery:** Implement rate limiting, use a WAF, and analyze traffic patterns for mitigation.

---

## 🛡️ **Best Practices**

- Regularly monitor NGINX performance metrics.
- Set appropriate resource limits and use a robust firewall.
- Perform routine log analysis for early detection of unusual traffic.

---

## ✅ **Conclusion**

By systematically checking NGINX configurations, evaluating for memory leaks, analyzing traffic patterns, and tuning system settings, the high memory usage issue can be diagnosed and resolved effectively. Proactive monitoring and configuration management are key to ensuring stable and efficient performance.