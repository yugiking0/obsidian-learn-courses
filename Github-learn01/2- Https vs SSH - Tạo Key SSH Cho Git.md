# Tạo Key SSH Cho Git
```bash
ssh-keygen -t ed25519 -C "your_email@example.com" 
```

*Note: If you are using a legacy system that doesn't support the Ed25519 algorithm, use:*
```bash
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```

![[Pasted image 20230829172254.png]]






