<img width="800" alt="Banner del Simulador de Ventas" src="https://github.com/user-attachments/assets/b6543b14-c97e-4003-b5d0-8c1a154c2279">

# ⚙️ Motor de Simulación de Ventas Automotrices

![Python](https://img.shields.io/badge/python-3.8+-blue.svg)
![Pandas](https://img.shields.io/badge/pandas-brightgreen)
![Requests](https://img.shields.io/badge/requests-orange)
![License](https://img.shields.io/badge/license-MIT-green.svg)

Este proyecto es un simulador avanzado del ciclo de venta automotriz, diseñado como una herramienta estratégica para analizar el impacto de distintas reglas de negocio, perfiles de cliente y escenarios macroeconómicos en la tasa de conversión de ventas.

El modelo genera perfiles de clientes dinámicos (personas y empresas), calcula la afinidad de estos con un catálogo de vehículos y los somete a un complejo proceso de evaluación financiera para determinar la probabilidad de compra.

---

## 🚀 Características Principales

* **Generación Dinámica de Perfiles:** Crea leads sintéticos para **Personas Naturales** (basado en datos socioeconómicos GSE) y **Personas Jurídicas** (basado en el tamaño de la empresa).

* **Contexto Macroeconómico:** Se conecta a la **API del Banco Central de Chile** para obtener la tasa de desempleo y ajustar la simulación a un escenario económico realista.

* **Motor de Afinidad:** Implementa un sistema de scoring que calcula la compatibilidad entre un cliente y un vehículo, considerando el perfil financiero, el precio del auto y el vehículo actual del cliente.

* **Simulador de Financiamiento Complejo:** Evalúa múltiples tipos de crédito (`Tradicional` y `Renovación Inteligente`), aplica una lógica de **aprobación en cascada** y simula casos especiales como **complemento de renta** y **renegociación de pie**.

* **Alta Configurabilidad:** Todas las reglas de negocio (probabilidades, tasas, plazos, etc.) están centralizadas en una única clase (`SimulationConfig`), permitiendo experimentar con distintos escenarios de forma sencilla y reproducible.

* **Análisis y Visualización:** Genera un completo reporte de resultados, incluyendo un **embudo de conversión**, distribución de ventas, tasas de conversión por perfil y principales motivos de rechazo.

---

## 🛠️ Tecnologías Utilizadas

* **Python 3.8+**
* **Pandas** y **NumPy** para la manipulación y análisis de datos.
* **Requests** para el consumo de la API del Banco Central.
* **Openpyxl** para la interacción con archivos Excel.
* **Matplotlib** y **Seaborn** para la visualización de datos.
* **Jupyter Notebook** como entorno de análisis interactivo.

---

## 🏗️ Estructura del Proyecto

El código está organizado de manera modular siguiendo un paradigma orientado a objetos. Además de los archivos del repositorio, la lógica se divide en "Pilares" conceptuales para facilitar su comprensión.

### Archivos del Repositorio
```
motor-simulacion-ventas/
├── .gitignore
├── LICENSE
├── README.md
├── requirements.txt
├── motor_simulacion_ventas_akira.ipynb
└── Perfiles-por-Regiones-y-Comunas-GSE-AIM-2023.xlsx
```

### Pilares Lógicos del Código
1.  **Configuración (`SimulationConfig`):** Parámetros centrales y reproducibilidad.
2.  **Generador de Perfiles (`ClientProfileGenerator`):** Creación de leads.
3.  **Motor de Afinidad (`VehicleAffinityEngine`):** Cálculo de compatibilidad.
4.  **Motor de Financiamiento (`FinancingEngine`):** Lógica de evaluación crediticia.
5.  **Orquestador (`SalesCycleOrchestrator`):** Ejecución del ciclo de venta completo.
6.  **Simulador Batch (`BatchSimulator`):** Procesamiento eficiente de grandes volúmenes.

---

## ⚙️ Instalación y Uso

Sigue estos pasos para poner en marcha el simulador.

### 1. Clonar y Preparar el Entorno
```bash
# Clona el repositorio
git clone [https://github.com/tu-usuario/motor-simulacion-ventas.git](https://github.com/tu-usuario/motor-simulacion-ventas.git)
cd motor-simulacion-ventas

# Crea y activa un entorno virtual
python -m venv venv
source venv/bin/activate  # En Windows: venv\Scripts\activate
```

### 2. Instalar Dependencias
```bash
# Instala todas las librerías necesarias
pip install -r requirements.txt
```

### 3. Configurar Datos y Credenciales

⚠️ **Importante:** Antes de ejecutar, debes realizar la siguiente configuración:

* **Datos GSE:** Asegúrate de que el archivo `Perfiles-por-Regiones-y-Comunas-GSE-AIM-2023.xlsx` esté en la misma carpeta que el notebook, o modifica la ruta en la celda correspondiente del archivo `.ipynb`.

* **Credenciales API (Opcional):** Para usar el contexto macroeconómico, debes configurar tus credenciales de la API del Banco Central como variables de entorno. Si no lo haces, el simulador usará un escenario "Neutral" por defecto.
    ```bash
    # Ejemplo en Linux/macOS
    export BCCH_USER="tu_usuario"
    export BCCH_PASS="tu_clave"
    ```

### 4. Ejecutar la Simulación
1.  Inicia tu entorno de Jupyter:
    ```bash
    jupyter lab
    ```
2.  Abre el notebook **`motor_simulacion_ventas_akira.ipynb`**.
3.  Ejecuta todas las celdas en orden. La forma más sencilla es usar la opción del menú `Run > Run All Cells`.

---

## 📊 Resultados Esperados

Al finalizar la ejecución completa del notebook, obtendrás:

* Un **resumen de la simulación** impreso en la salida de la celda final.
* Un DataFrame de Pandas llamado **`df_resultados_final`**, listo para análisis interactivo.
* Una serie de **gráficos** que visualizan el embudo de conversión, las ventas por modelo y los motivos de rechazo.
* Un **archivo Excel** con los resultados detallados si ejecutas la función `exportar_resultados_excel()`.

---

## 📄 Licencia

Este proyecto se distribuye bajo la licencia MIT. Ver el archivo `LICENSE` para más detalles.
