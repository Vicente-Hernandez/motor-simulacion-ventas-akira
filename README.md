

<img width="1024" height="1024" alt="unnamed" src="https://github.com/user-attachments/assets/b6543b14-c97e-4003-b5d0-8c1a154c2279" />

# ⚙️ Motor de Simulación de Ventas Automotrices

Este proyecto es un simulador avanzado del ciclo de venta automotriz, diseñado como una herramienta estratégica para analizar el impacto de distintas reglas de negocio, perfiles de cliente y escenarios macroeconómicos en la tasa de conversión de ventas.

El modelo genera perfiles de clientes dinámicos (personas y empresas), calcula la afinidad de estos con un catálogo de vehículos y los somete a un complejo proceso de evaluación financiera para determinar la probabilidad de compra.

---

### ✨ Características Principales

* **Generación Dinámica de Perfiles:** Creación de leads sintéticos para `Personas Naturales` (basado en datos socioeconómicos GSE) y `Personas Jurídicas` (basado en distribución de tamaño de empresas).
* **Contexto Macroeconómico:** Se conecta a la API del Banco Central de Chile para ajustar la simulación según el escenario económico (tasa de desempleo).
* **Motor de Afinidad:** Sistema de scoring que calcula la compatibilidad entre un cliente y un vehículo, considerando el perfil financiero, el precio del auto y el vehículo actual del cliente.
* **Simulador de Financiamiento Complejo:**
    * Evalúa múltiples tipos de crédito (`Tradicional` y `Renovación Inteligente`).
    * Implementa una lógica de cascada con varios intentos de aprobación.
    * Simula casos especiales como **complemento de renta** para personas casadas y **renegociación de pie** para empresas.
* **Lógica de Pago al Contado:** Modela un camino de compra alternativo para clientes que prefieren o pueden pagar al contado, basado en su perfil.
* **Alta Configurabilidad:** Todas las reglas de negocio (probabilidades, plazos, tasas, multiplicadores) están centralizadas en una única clase de configuración (`SimulationConfig`), permitiendo un ajuste fino y la prueba de distintos escenarios de forma sencilla.
* **Análisis y Visualización:** Genera un completo reporte de resultados, incluyendo un embudo de conversión, distribución de ventas por modelo, tasas de conversión por perfil y principales motivos de rechazo.

---

### 🔧 Estructura del Proyecto

El código está organizado de manera modular siguiendo un paradigma orientado a objetos, dividido en "Pilares" lógicos:

1.  **Configuración (`SimulationConfig`):** Parámetros centrales y reproducibilidad.
2.  **Generador de Perfiles (`ClientProfileGenerator`):** Creación de leads.
3.  **Motor de Afinidad (`VehicleAffinityEngine`):** Cálculo de compatibilidad.
4.  **Motor de Financiamiento (`FinancingEngine`):** Lógica de evaluación crediticia.
5.  **Orquestador (`SalesCycleOrchestrator`):** Ejecución del ciclo de venta completo.
6.  **Simulador Batch (`BatchSimulator`):** Procesamiento eficiente de grandes volúmenes de leads.

---

### 🚀 Instalación y Uso

#### 1. Prerrequisitos
* Python 3.8+
* Git

#### 2. Instalación

1.  **Clona el repositorio:**
    ```bash
    git clone [URL-DE-TU-REPOSITORIO]
    cd [NOMBRE-DEL-REPOSITORIO]
    ```

2.  **Crea un entorno virtual (recomendado):**
    ```bash
    python -m venv venv
    source venv/bin/activate  # En Windows: venv\Scripts\activate
    ```

3.  **Instala las dependencias:**
    ```bash
    pip install -r requirements.txt
    ```

#### 3. Configuración

1.  **Datos GSE:** Asegúrate de que el archivo `Perfiles-por-Regiones-y-Comunas-GSE-AIM-2023.xlsx` se encuentre en la ruta especificada en la `Celda 7` del notebook (`FILEPATH_GSE`), o modifica la variable con tu ruta local.

2.  **Credenciales API (Opcional):** Para usar el contexto macroeconómico, debes configurar las credenciales de la API del Banco Central como variables de entorno:
    ```bash
    export BCCH_USER="tu_usuario"
    export BCCH_PASS="tu_clave"
    ```
    Si no se configuran, el simulador funcionará en un modo manual con un escenario "Neutral".

#### 4. Ejecución

1.  Abre el notebook `motor-simulacion-ventas-akira.ipynb` en Jupyter Lab o Google Colab.
2.  Ejecuta todas las celdas en orden. Puedes usar la opción del menú `Entorno de ejecución > Ejecutar todo`.

---

### 📊 Resultados

Al finalizar la ejecución, el notebook generará:
* Un **output detallado** en la consola con el resumen de la simulación.
* Un **DataFrame de Pandas** llamado `df_resultados_final` disponible para análisis interactivo.
* Una serie de **gráficos de visualización** en la Celda 8.
* Un **archivo Excel** con los resultados detallados (generado al ejecutar la función `exportar_resultados_excel`).

---

### 📄 Licencia

Este proyecto se distribuye bajo la licencia MIT. Ver el archivo `LICENSE` para más detalles.
