# Appravoal System - Mikroservis Projesi

Bu proje, Appravoal System adında bir mikroservis mimarisi kullanılarak geliştirilmiştir. Kullanıcıların yönetimi, rol ve izinlerin atanması, grupların yönetilmesi ve organizasyonel yapının oluşturulması gibi özellikler sağlar.

---

## Genel Bilgiler

Proje aşağıdaki mikroservislerden oluşmaktadır:

1. **User**: Kullanıcı bilgilerinin ve ilişkili rollerin yönetimi.
2. **Role**: Sistem içerisindeki rolleri yönetir.
3. **Group**: Kullanıcıları gruplar halinde organize eder.
4. **Permission**: Farklı işlem izinlerini yönetir.
5. **Organization**: Organizasyon yapısını ve hiyerarşisini yönetir.

Tüm mikroservisler **Gateway** ile birleştirilmiştir ve REST API ile haberleşir.

---

## Kullanılan Teknolojiler

- **Programlama Dili**: Java, Spring Boot
- **Veritabanı**: PostgreSQL
- **API Test**: Postman
- **API Gateway**: Spring Cloud Gateway

---

## Mikroservislerin Detayları

### User Servisi
- Kullanıcı bilgileri ve rollerin yönetimi.
- Kullanıcılar ile rolleri arasında **1:N** ilişkisi bulunur.

### Role Servisi
- Rollerin yönetimi.
- Kullanıcılar ile **1:N**, izinlerle **N:N** ilişkisi vardır.

### Group Servisi
- Grupların oluşturulması ve yönetimi.
- Rollere **1:N**, izinlere **N:N** ilişkisi bulunur.

### Permission Servisi
- Farklı işlem izinlerinin yönetimi.
- Rollere ve gruplara **N:N** ilişkisi bulunur.

### Organization Servisi
- Organizasyon yapısı oluşturulur.
- Organizasyonlar ağaç yapısı ile modellenmiştir.

### Gateway
- Tüm mikroservisler için tek bir giriş noktısı sağlar.
- Gelen istekleri uygun servislere yönlendirir.

---

## Veritabanı Yapısı

- **User** ve **Role**: 1:N
- **Role** ve **Permission**: N:N
- **Group** ve **Role**: 1:N
- **Group** ve **Permission**: N:N
- **Organization**: Kendine referans veren ağaç yapısı

---

## Postman Testleri

Proje API’ları Postman kullanılarak test edilmiştir. Aşağıdaki işlemler için örnek istekler oluşturulmuştur:

- Kullanıcı oluşturma ve yönetim
- Roller ve izinler ekleme
- Grupları ilişkilerle yönetme
- Organizasyon yapısı işlemleri
