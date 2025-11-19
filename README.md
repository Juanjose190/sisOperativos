
````markdown
# AWS FINAL - SISTEMAS OPERATIVOS

Integrante: Juan José Burbano Bolaños
            Danilo Andrés Montezuma

## Conectar con el cliente

```bash
ssh -i ~/Downloads/dfs-key-v2.pem ubuntu@3.151.85.34
sudo -u app-user bash
cd /opt/client-app
````

## PRUEBAS

### PRUEBA 1: Usuario READONLY puede LISTAR

```bash
node dist/client.js 10.0.0.10 token_guest_789 LIST
```

### PRUEBA 2: Usuario READONLY NO puede ESCRIBIR

```bash
node dist/client.js 10.0.0.10 token_guest_789 WRITE demo.txt "Hola desde mi puta choza"
```

### PRUEBA 3: Usuario ADMIN puede ESCRIBIR

```bash
node dist/client.js 10.0.0.10 token_admin_123 WRITE demo.txt "Archivo creado en demo"
```

### PRUEBA 4: Usuario USER puede LEER

```bash
node dist/client.js 10.0.0.10 token_user_456 READ demo.txt
```

### PRUEBA 5: Usuario USER NO puede ELIMINAR

```bash
node dist/client.js 10.0.0.10 token_user_456 DELETE demo.txt
```

### PRUEBA 6: Solo ADMIN puede ELIMINAR

```bash
node dist/client.js 10.0.0.10 token_admin_123 DELETE demo.txt
```

### PRUEBA 7: Token INVÁLIDO

```bash
node dist/client.js 10.0.0.10 token_falso_999 LIST
```

### PRUEBA 8: Crear archivos y listar

```bash
node dist/client.js 10.0.0.10 token_admin_123 WRITE test1.txt "Primer archivo"
node dist/client.js 10.0.0.10 token_admin_123 WRITE test2.txt "Segundo archivo"
node dist/client.js 10.0.0.10 token_guest_789 LIST
```

## Ver el servidor

### Conectar al servidor

```bash
ssh -i /Users/juanjose/Downloads/dfs-key-v2.pem ubuntu@18.119.206.80
```

### Comandos útiles

```bash
sudo systemctl status file-server
sudo journalctl -u file-server -n 30
sudo ls -la /srv/dfs_storage/
sudo cat /srv/dfs_storage/metadata.json
sudo cat /srv/dfs_storage/test1.txt
```

```

```
