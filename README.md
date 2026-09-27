# 01.-AEE.-RA1.-Introduccion a los lenguajes de marca.

Actividad Práctica: Gestión de Biblioteca Digital

Módulo: Lenguaje de Marcas y Sistemas de Gestión de Información
Profesor: Willman Acosta Lugo
Cualidad: AEE - 10 %
Modalidad: Trabajo en parejas
Fecha de entrega: 01/10/2026

FASE 1: Análisis y Diseño
1.1 Clasificación de Lenguajes de Marcas
Componente	Tipo de Lenguaje de Marca	Justificación
Catálogo de libros	XML + CSS	XML permite organizar, estructurar y compartir los datos de forma estandarizada, legible tanto por personas como por máquinas e independiente de la plataforma. CSS puede utilizarse para presentar visualmente la información.
Página web pública	HTML + CSS	HTML proporciona la estructura y el contenido de la página web, mientras que CSS se encarga del diseño visual, colores, tamaños, distribución y presentación.
Intercambio con editoriales	JSON / XML	JSON destaca por su simplicidad, reducido tamaño y facilidad de integración con aplicaciones web y JavaScript. XML es apropiado cuando se necesita una estructura más compleja, validación estricta y etiquetas personalizadas.
Configuración del sistema	YAML / XML / JSON	XML permite representar información mediante una estructura jerárquica de elementos y atributos. YAML facilita la configuración mediante listas y pares clave-valor. JSON también resulta adecuado para configuraciones sencillas y fácilmente procesables por aplicaciones.
Reportes de estadísticas	XML / CSV	XML resulta adecuado para datos complejos y jerárquicos. CSV es especialmente apropiado para datos tabulares y sencillos, facilitando su análisis mediante programas como Excel o LibreOffice Calc.
1.2 Diseño de Espacios de Nombres

La biblioteca utilizará diferentes espacios de nombres para separar los distintos tipos de información y evitar conflictos entre elementos.

http://biblioteca.campuscamarasevilla.es/
├── schemas/
│   ├── recursos/v1
│   │   ├── libros
│   │   ├── revistas
│   │   └── recursosDigitales
│   │
│   ├── usuarios/v1
│   │   ├── estudiantes
│   │   └── profesores
│   │
│   ├── prestamos/v1
│   │   ├── prestamos
│   │   └── devoluciones
│   │
│   └── configuracion/v1
│
└── apis/
    ├── publico/v1
    └── interno/v1
Documento XML de ejemplo con namespaces
<?xml version="1.0" encoding="UTF-8"?>

<biblioteca
    xmlns:rec="https://biblioteca.campuscamarasevilla.es/schema/recursos/v1"
    xmlns:usu="https://biblioteca.campuscamarasevilla.es/schema/usuarios/v1"
    xmlns:pre="https://biblioteca.campuscamarasevilla.es/schema/prestamos/v1"
    xmlns:conf="https://biblioteca.campuscamarasevilla.es/schema/configuracion/v1"
    xmlns:api="https://biblioteca.campuscamarasevilla.es/apis">

   <rec:recursos> 
        <rec:libros/>
        <rec:revistas/>
        <rec:recursosDigitales/>
    </rec:recursos>

   <usu:usuarios>
        <usu:estudiantes/>
        <usu:profesores/>
    </usu:usuarios>

   <pre:prestamos>
        <pre:prestamosActivos/>
        <pre:devoluciones/>
    </pre:prestamos>

   <conf:configuracion/>

   <api:publico>
        <api:catalogo/>
    </api:publico>

   <api:interno>
        <api:gestion/>
    </api:interno>

</biblioteca>

FASE 3: Wireframe de la Interfaz

La interfaz está diseñada para que una persona que trabaja en la recepción de la biblioteca pueda consultar rápidamente la existencia de un recurso y realizar un préstamo.

3.1 Estructura de la pantalla
┌────────────────────────────────────────────────────────────────────┐
│                                                                    │
│  📚 BIBLIOTECA DIGITAL DEL CAMPUS CÁMARA SEVILLA                   │
│                                                                    │
│  [ LOGO DE LA BIBLIOTECA ]                                        │
│                                                                    │
├────────────────────────────────────────────────────────────────────┤
│                                                                    │
│  BUSCADOR                                                          │
│                                                                    │
│  ┌──────────────────────────────────────────────┐  ┌────────────┐  │
│  │ Introducir título o autor                    │  │   BUSCAR   │  │
│  └──────────────────────────────────────────────┘  └────────────┘  │
│                                                                    │
├────────────────────────────────────────────────────────────────────┤
│                                                                    │
│  RESULTADOS                                                        │
│                                                                    │
│  ┌──────────────────────────────────────────────────────────────┐  │
│  │ Título: 1984                                                 │  │
│  │ Autor: George Orwell                                         │  │
│  │ Categoría: Ciencia ficción / Distopía                        │  │
│  │ Año de publicación: 1949                                     │  │
│  │                                                              │  │
│  │ Disponibilidad: ✓ DISPONIBLE                                 │  │
│  │                                                              │  │
│  │ [ REALIZAR PRÉSTAMO ]     [ VER INFORMACIÓN ]                │  │
│  │                                                              │  │
│  │ Ubicación: Ciencia ficción                                   │  │
│  │ Estantería: B-01                                             │  │
│  │ Signatura: CF-ORW-003                                        │  │
│  └──────────────────────────────────────────────────────────────┘  │
│                                                                    │
│  ┌──────────────────────────────────────────────────────────────┐  │
│  │ Título: Cien años de soledad                                 │  │
│  │ Autor: Gabriel García Márquez                                │  │
│  │ Categoría: Literatura / Realismo mágico                      │  │
│  │ Año de publicación: 1967                                     │  │
│  │                                                              │  │
│  │ Disponibilidad: ✕ NO DISPONIBLE                              │  │
│  │                                                              │  │
│  │ [ REALIZAR PRÉSTAMO ]     [ VER INFORMACIÓN ]                │  │
│  │                                                              │  │
│  │ Ubicación: Literatura                                       │  │
│  │ Estantería: A-02                                             │  │
│  │ Signatura: LI-GAR-002                                        │  │
│  └──────────────────────────────────────────────────────────────┘  │
│                                                                    │
└────────────────────────────────────────────────────────────────────┘


