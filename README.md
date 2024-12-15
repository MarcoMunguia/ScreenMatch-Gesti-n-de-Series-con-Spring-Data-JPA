# ScreenMatch-Gesti-n-de-Series-con-Spring-Data-JPA
Organización y almacenamiento de series en una base de datos.
# 🎬 ScreenMatch - Gestión de Series con Spring Data JPA  

Esta aplicación amplía las funcionalidades de **ScreenMatch** para gestionar series, incluyendo organización, clasificación por categorías y la identificación de los 5 capítulos más importantes de cada serie. Utilizamos **Spring Data JPA** para la persistencia de datos en una base de datos **MySQL**, implementando consultas avanzadas, modelado de entidades, y un enfoque dinámico para manejar y buscar datos.  

## 🚀 Funcionalidades Clave  

1. **Gestión de Series**:  
   - Organización y almacenamiento de series en una base de datos.  
   - Modelado de series como entidades reconocidas por JPA.  

2. **Clasificación por Categorías**:  
   - Clasificación de series según diferentes géneros o categorías (e.g., drama, comedia, acción).  

3. **Top 5 Capítulos por Serie**:  
   - Identificación de los 5 capítulos más importantes de cada serie.  

4. **Consultas Dinámicas**:  
   - **Derived Queries**: Consultas generadas automáticamente por Spring Data JPA basadas en el nombre de los métodos.  
   - **JPQL y Native Queries**: Consultas personalizadas para obtener datos más específicos.  

5. **Persistencia de Datos**:  
   - Integración con una base de datos **MySQL** para almacenar series, categorías y capítulos.  

6. **Reestructuración y Modelado**:  
   - Uso de **enums** para representar categorías.  
   - Modelado eficiente de datos para mejorar la organización y consultas.  

## 📂 Estructura del Proyecto  

```plaintext  
.  
├── src  
│   ├── main  
│   │   ├── java  
│   │   │   ├── com.example.screenmatch  
│   │   │   │   ├── ScreenMatchApplication.java     # Clase principal  
│   │   │   │   ├── model  
│   │   │   │   │   ├── Serie.java                 # Entidad para representar series  
│   │   │   │   │   ├── Categoria.java             # Enum para categorías  
│   │   │   │   │   ├── Capitulo.java              # Entidad para capítulos  
│   │   │   │   ├── repository  
│   │   │   │   │   ├── SerieRepository.java       # Repositorio para manejo de series  
│   │   │   │   │   ├── CapituloRepository.java    # Repositorio para manejo de capítulos  
│   │   │   │   ├── service  
│   │   │   │   │   ├── SerieService.java          # Lógica de negocio para series  
│   │   │   │   │   ├── CapituloService.java       # Lógica de negocio para capítulos  
│   │   │   │   ├── controller  
│   │   │   │   │   ├── SerieController.java       # Controlador REST para series  
│   │   │   │   │   ├── CapituloController.java    # Controlador REST para capítulos  
│   │   ├── resources  
│   │   │   ├── application.properties             # Configuración de Spring y MySQL  
│   │   │   └── data.sql                           # Archivo inicial de carga de datos  
├── README.md                                       # Documentación del proyecto  
```  

## 🛠️ Tecnologías Utilizadas  

- **Lenguaje**: Java  
- **Framework**: Spring Boot y Spring Data JPA  
- **Base de Datos**: MySQL  
- **Herramientas de Modelado**: JPA para la persistencia de datos  
- **Consultas**: Derived Queries, JPQL y Native Queries  

## 🔧 Configuración y Ejecución  

1. **Clonar el Repositorio**:  
   ```bash  
   git clone https://github.com/tuusuario/screenmatch-series.git  
   cd screenmatch-series  
   ```  

2. **Configurar la Base de Datos**:  
   - Asegúrate de tener un servidor MySQL en funcionamiento.  
   - Configura las credenciales en `application.properties`:  
     ```properties  
     spring.datasource.url=jdbc:mysql://localhost:3306/screenmatch  
     spring.datasource.username=tu_usuario  
     spring.datasource.password=tu_contraseña  
     spring.jpa.hibernate.ddl-auto=update  
     ```  

3. **Ejecutar la Aplicación**:  
   - Con **Maven**, ejecuta:  
     ```bash  
     mvn spring-boot:run  
     ```  
   - Accede a la aplicación en `http://localhost:8080`.  

4. **Endpoints Disponibles**:  
   - `GET /series` - Lista todas las series.  
   - `GET /series/{id}` - Obtiene los detalles de una serie específica.  
   - `POST /series` - Agrega una nueva serie.  
   - `GET /series/top-capitulos` - Lista los 5 capítulos más importantes por serie.  

## 📝 Ejemplo de Entidad (Serie)  

```java  
@Entity  
public class Serie {  
    @Id  
    @GeneratedValue(strategy = GenerationType.IDENTITY)  
    private Long id;  

    private String nombre;  

    @Enumerated(EnumType.STRING)  
    private Categoria categoria;  

    @OneToMany(mappedBy = "serie")  
    private List<Capitulo> capitulos;  
}  
```  

## 🎯 Aprendizajes  

### 💡 Persistencia de Datos con JPA  
- Modelado de datos con entidades y relaciones (e.g., OneToMany).  
- Uso de enums para representar categorías en la base de datos.  

### 🔍 Consultas Avanzadas  
- Implementación de consultas personalizadas con JPQL y Native Queries.  
- Uso de Derived Queries para simplificar consultas comunes.  

### 🛠️ Reestructuración y Mejora  
- Dinamismo en la lógica de negocio.  
- Persistencia de datos en una base de datos MySQL, asegurando integridad y escalabilidad.  

---

## 🌟 Funcionalidades Futuras  

- Implementar una interfaz web para gestionar series y capítulos.  
- Agregar filtros avanzados por categoría, fecha de lanzamiento, o calificación.  
- Integrar autenticación y autorización para gestionar el acceso a la aplicación.  

---

## 🏷️ Etiquetas  

`#Java` `#SpringBoot` `#JPA` `#MySQL` `#PersistenciaDeDatos`  

---

¡Espero que este `README.md` sea útil para documentar tu proyecto de ScreenMatch con Spring Data JPA! 🚀 Si necesitas personalizarlo más, ¡avísame! 😊
