## Recomendaciones de seguridad de bind9

```bash
1. Definición de Listas de Control de Acceso (ACL)
acl "clientes_internos" {
    127.0.0.1;
    192.168.1.0/24; // Reemplaza con tu rango de red interna
};

options {
    directory "/var/cache/bind";

    // 2. Mitigación de Resolutor Abierto
    recursion yes;
    allow-recursion { "clientes_internos"; };
    allow-query { "clientes_internos"; }; // Si es solo recursivo, limita todo
    allow-query-cache { "clientes_internos"; };

    // 3. Ocultar información del sistema
    version "No disponible";
    server-id none;

    // 4. Protección contra ataques de amplificación (RRL)
    rate-limit {
        responses-per-second 5;
        window 5;
    };

    // 5. Configuración de rendimiento y mitigación DoS (Crucial para 9.18/9.20)
    max-cache-size 2G; // Ajusta según la RAM de tu servidor
    clients-per-query 10;
    max-clients-per-query 20;

    // 6. Seguridad en el transporte (DoT) si aplica
    // listen-on port 853 ssl myssl { any; };
};
```
