# Proyecto-intermodular-Fundamentos-de-Computaci-n-en-la-Nube

##  Descripción del proyecto

**NexoHR** es un sistema de gestión de Recursos Humanos orientado a pequeñas y medianas empresas.  
Permite gestionar empleados, contratos, nóminas, ausencias y permisos desde cualquier navegador web.

Este repositorio recoge el análisis y diseño de la **arquitectura cloud** necesaria para desplegar el sistema en la nube, como parte del módulo de Fundamentos de Computación en la Nube del proyecto intermodular de SMR 1.

---

##  Proveedor Cloud elegido

| | |
|---|---|
| **Proveedor** | Amazon Web Services (AWS) |
| **Región** | Europe (Ireland) — `eu-west-1` |
| **Motivo** | Mayor cuota de mercado, Free Tier generoso, centros de datos en Europa (cumplimiento RGPD) y documentación extensa |

---

##  Arquitectura propuesta
> Todo el entorno corre dentro de una **VPC privada**.  
> Los **Security Groups** restringen el acceso: solo HTTPS al EC2 y solo conexiones internas al RDS.

---

##  Servicios AWS utilizados

| Servicio | Uso en el proyecto | Free Tier |
|---|---|---|
| **Amazon EC2** (t2.micro) | Servidor web + aplicación RRHH | ✅ 750 h/mes · 12 meses |
| **Amazon RDS for MySQL** (db.t4g.micro) | Base de datos gestionada | ✅ 750 h/mes + 20 GB · 12 meses |
| **Amazon S3** | Almacenamiento de documentos y PDFs | ✅ 5 GB siempre gratis |
| **Amazon VPC** | Red privada virtual, aislamiento de recursos | ✅ Gratuito |
| **Security Groups** | Cortafuegos a nivel de instancia | ✅ Gratuito |
| **Elastic IP** | IP pública estática para el servidor | ✅ Gratis si está asociada |

---

##  Estimación de costes mensuales

> Calculado con [AWS Pricing Calculator](https://calculator.aws) · Región: Europe (Ireland)

| Servicio | Instancia / Plan | Coste mensual | Free Tier |
|---|---|---|---|
| Amazon EC2 | t2.micro (1 vCPU, 1 GB RAM) | ~8,50 $/mes | ✅ Sí (12 meses) |
| Amazon RDS MySQL | db.t4g.micro + 20 GB SSD | ~14,50 $/mes | ✅ Sí (12 meses) |
| Amazon S3 | 5 GB Standard | ~0,12 $/mes | ✅ Sí (5 GB siempre) |
| Elastic IP | 1 IP estática asociada | 0,00 $/mes | ✅ Sí |
| Transferencia datos | Saliente < 1 GB/mes | 0,00 $/mes | ✅ Sí |
| **TOTAL sin Free Tier** | | **~23–25 $/mes** | |
| **TOTAL con Free Tier** | Primer año cuenta nueva | **0,00 $/mes** | ✅ |

---

## 📚 Referencias

- [AWS Pricing Calculator](https://calculator.aws)
- [Amazon EC2 — Free Tier](https://aws.amazon.com/free/)
- [Amazon RDS for MySQL — Precios](https://aws.amazon.com/rds/mysql/pricing/)
- [Amazon S3 — Precios](https://aws.amazon.com/s3/pricing/)
- [Documentación oficial de AWS](https://docs.aws.amazon.com/)

---

*Proyecto desarrollado por Nicky Cetro Fernandez*
