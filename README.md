# Spring Boot Eureka Service Discovery Demo

Bu proje, **Spring Cloud Netflix Eureka** teknolojisini kullanarak mikroservis mimarilerinde **Service Discovery (Hizmet Keşfi)** mekanizmasının nasıl çalıştığını göstermek amacıyla geliştirilmiştir.

Proje iki ana modülden oluşmaktadır:
1.  **Eureka Server:** Servislerin kayıt olduğu merkezi sunucu (Discovery Server).
2.  **Eureka Client:** Kendini sunucuya kaydeden mikroservis örneği.

## 🚀 Proje Yapısı

```bash
.
├── eureka-server  # Service Registry (Port: 8761)
└── eureka-client  # Microservice (Port: Dinamik veya 8888)
🛠️ Kurulum ve Çalıştırma
Projeyi lokalinizde çalıştırmak için aşağıdaki adımları izleyebilirsiniz.

1. Eureka Server'ı Ayağa Kaldırma
Öncelikle kayıt sunucusunu başlatmamız gerekiyor. eureka-server dizinine gidip uygulamayı çalıştırın.

Bash
cd eureka-server
mvn spring-boot:run
Sunucu http://localhost:8761 adresinde çalışmaya başlayacaktır.

<img width="2936" height="1767" alt="image" src="https://github.com/user-attachments/assets/cecd3cea-1854-4760-8c6f-637fcd0b602c" />


2. Eureka Client'ları Başlatma (Multi-Instance)
Load Balancing (Yük Dengeleme) senaryosunu simüle etmek için aynı client uygulamasından iki farklı portta ayağa kaldırıyoruz.

Birinci Instance (Varsayılan Port): eureka-client projesini standart şekilde başlatın.

<img width="2770" height="896" alt="image" src="https://github.com/user-attachments/assets/5d839433-6719-4dbd-a490-8c6c80a84cb5" />


İkinci Instance (Farklı Port): Terminalden veya IDE konfigürasyonundan portu değiştirerek ikinci bir örneği başlatın:

Bash
# Örnek terminal komutu
mvn clean install
java -jar -Dserver.port=8081 target/eureka-client-0.0.1-SNAPSHOT.jar

<img width="2668" height="425" alt="image" src="https://github.com/user-attachments/assets/5aa2a6ed-5232-406b-8f43-04f21840af09" />

✅ Sonuç: Service Registry Durumu
Her iki client uygulaması da başarıyla ayağa kalktığında, Eureka Server bu instance'ları otomatik olarak algılar ve "Instances currently registered with Eureka" tablosuna ekler.

Aşağıdaki görselde, tek bir uygulama isimi altında (EUREKA-CLIENT) çalışan 2 farklı instance olduğu görülmektedir.

<img width="2937" height="1454" alt="image" src="https://github.com/user-attachments/assets/2c9ee9e3-1181-48ea-9a96-81d51ab828dc" />


💻 Kullanılan Teknolojiler
Java 21

Spring Boot 3.x

Spring Cloud Netflix Eureka

Maven
