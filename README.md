# segundo-proyecto
package proyecto2progra;

import java.io.*;

import java.util.*;


public class FabricaMueblesApp {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int opcion;
        boolean salir = false;
        StringBuilder registro = new StringBuilder(); 

        do {
            System.out.println("Menú:");
            System.out.println("1. Crear archivo de texto");
            System.out.println("2. Crear mesa o silla");
            System.out.println("3. Inventario de materiales");
            System.out.println("4. Materiales para fabricación");
            System.out.println("5. Facturación");
            System.out.println("6. Ventas por empleado");
            System.out.println("7. Información del producto");
            System.out.println("8. Información de la orden");
            System.out.println("9. Salir");
            System.out.print("Seleccione una opción: ");

            opcion = scanner.nextInt();
            scanner.nextLine();  // Consumir la nueva línea

            switch (opcion) {
                case 1:
                    crearArchivoTexto(registro);
                    break;
                case 2:
                    crearMesaOSilla(registro);
                    break;
                case 3:
                    inventarioMateriales(registro);
                    break;
                case 4:
                    materialesFabricacion(registro);
                    break;
                case 5:
                    facturacion(registro);
                    break;
                case 6:
                    ventasPorEmpleado(registro);
                    break;
                case 7:
                    informacionProducto(registro);
                    break;
                case 8:
                    informacionOrden(registro);
                    break;
                case 9:
                    salir = true;
                    guardarEnArchivo(registro);
                    System.out.println("Saliendo del programa. ¡Hasta luego!");
                    break;
                default:
                    System.out.println("Opción no válida. Intente nuevamente.");
            }
        } while (!salir);
    }

    public static void crearArchivoTexto(StringBuilder registro) {
        try {
            PrintWriter writer = new PrintWriter("registro.txt");
            writer.println(registro.toString());
            writer.close();
            System.out.println("Archivo de texto creado con éxito.");
        } catch (IOException e) {
            System.out.println("Error al crear el archivo de texto: " + e.getMessage());
        }
    }

    public static void crearMesaOSilla(StringBuilder registro) {
        Scanner scanner = new Scanner(System.in);
        System.out.println("Ingrese los datos para crear una mesa o silla:");
        System.out.println("se va fabricar silla o mesa:");
        String mesaosilla = scanner.nextLine();
        System.out.print("Estilo: ");
        String estilo = scanner.nextLine();
        System.out.print("Color: ");
        String color = scanner.nextLine();
        System.out.print("Material: ");
        String material = scanner.nextLine();

        registro.append("Mesa/Silla - Estilo: ").append(estilo).append(", Color: ").append(color).append(", Material: ").append(material).append("\n");
    }

    public static void inventarioMateriales(StringBuilder registro) {
        Scanner scanner = new Scanner(System.in);
        System.out.println("Ingrese los datos del material en inventario:");
        System.out.print("Cantidad: ");
        int cantidad = scanner.nextInt();
        scanner.nextLine();  // Consumir la nueva línea
        System.out.print("Nombre: ");
        String nombre = scanner.nextLine();
        System.out.print("Medidas: ");
        String medidas = scanner.nextLine();

        registro.append("Inventario de Materiales - Cantidad: ").append(cantidad).append(", Nombre: ").append(nombre).append(", Medidas: ").append(medidas).append("\n");
    }

    public static void materialesFabricacion(StringBuilder registro) {
        Scanner scanner = new Scanner(System.in);
        System.out.println("Ingrese los datos de los materiales para fabricación:");
        System.out.print("Nombre: ");
        String nombre = scanner.nextLine();
        System.out.print("Cantidad: ");
        int cantidad = scanner.nextInt();
        scanner.nextLine();  // Consumir la nueva línea
        System.out.print("Medidas: ");
        String medidas = scanner.nextLine();

        registro.append("Materiales de Fabricación - Nombre: ").append(nombre).append(", Cantidad: ").append(cantidad).append(", Medidas: ").append(medidas).append("\n");
    }

    public static void facturacion(StringBuilder registro) {
        Scanner scanner = new Scanner(System.in);
        System.out.println("Ingrese los datos de facturación:");
        System.out.print("NIT: ");
        String nit = scanner.nextLine();
        System.out.print("Nombre: ");
        String nombre = scanner.nextLine();
        System.out.print("Descripción: ");
        String descripcion = scanner.nextLine();

        registro.append("Facturación - NIT: ").append(nit).append(", Nombre: ").append(nombre).append(", Descripción: ").append(descripcion).append("\n");
    }

    public static void ventasPorEmpleado(StringBuilder registro) {
       Scanner scanner = new Scanner(System.in);
        System.out.println("Ingrese los datos de empleado:");
        System.out.print("Nombre: ");
        String nombre = scanner.nextLine();
        System.out.print("numero de empleado: ");
        String empleado = scanner.nextLine();
        System.out.print("comision por venta: ");
        String comision = scanner.nextLine();
       
       registro.append("Empleado - nombre: ").append(nombre).append(", Empleado: ").append(empleado).append(", comision: ").append(comision).append("\n");
    }

    public static void informacionProducto(StringBuilder registro) {
       Scanner scanner = new Scanner(System.in);
        System.out.println("Ingrese los datos del producto:");
        System.out.print("codigo: ");
        String codigo = scanner.nextLine();
        System.out.print("descripcion: ");
        String informacion = scanner.nextLine();
        System.out.print("precio del producto: ");
        String producto = scanner.nextLine();
       
       registro.append("Producto - codigo: ").append(codigo).append(", Descripcion: ").append(informacion).append(", precio: ").append(producto).append("\n");
    }

    public static void informacionOrden(StringBuilder registro) {
      Scanner scanner = new Scanner(System.in);
        System.out.println("Ingrese los datos de la orden:");
        System.out.print("numero de orden: ");
        String orden = scanner.nextLine();
        System.out.print("fecha: ");
        String fecha = scanner.nextLine();
        System.out.print("vendedor: ");
        String vendedor = scanner.nextLine();
       
       registro.append("Orden - numero de orden: ").append(orden).append(", fecha: ").append(fecha).append(", vendedor: ").append(vendedor).append("\n");  
    }

    public static void guardarEnArchivo(StringBuilder registro) {
        try {
            PrintWriter writer = new PrintWriter("registro.txt");
            writer.println(registro.toString());
            writer.close();
        } catch (IOException e) {
            System.out.println("Error al guardar el registro en el archivo de texto: " + e.getMessage());
        }
    }
}

//conexion 
package proyecto2progra;

import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.SQLException;

public class ConexionMySQL {

    public static void main(String[] args) {
        // Parámetros de conexión
        String url = "jdbc:mariadb://localhost:127.0.0.1:3306/fabrica";
        String usuario = "root";
        String contraseña = "2004";

        try {
            // Cargar el controlador JDBC
            Class.forName("org.mariadb.jdbc.Driver");

            // Establecer la conexión
            Connection conexion = DriverManager.getConnection("jdbc:mariadb://127.0.0.1:3306/fabrica");

            if (conexion != null) {
                System.out.println("Conexión exitosa a la base de datos MySQL.");
                
                conexion.close();
            } else {
                System.out.println("No se pudo establecer la conexión.");
            }
        } catch (ClassNotFoundException e) {
            System.err.println("Error al cargar el controlador JDBC: " + e.getMessage());
        } catch (SQLException e) {
            System.err.println("Error de SQL: " + e.getMessage());
        }
    }
}

//ingreso de tablas 

import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.PreparedStatement;
import java.sql.SQLException;

public class fabrica {

    public static void main(String[] args) {
        String url = "jdbc:mariadb://localhost:127.0.0.1:3306/fabrica";
        String usuario = "root"; // 
        String contraseña = "2004"; 

        try {
            Connection connection = DriverManager.getConnection("jdbc:mariadb://localhost:127.0.0.1:3306/fabrica");

          
            insertarMesaOSilla(connection, "silla", "estilo", "color", "material");
            

            connection.close();
        } catch (SQLException e) {
            e.printStackTrace();
        }
    }

    public static void insertarMesaOSilla(Connection connection, String mesaosilla, String estilo, String color, String material) throws SQLException {
        String insertSQL = "INSERT INTO mesasosilla (tipo, estilo, color, material) VALUES (?, ?, ?, ?)";
        PreparedStatement preparedStatement = connection.prepareStatement(insertSQL);
        preparedStatement.setString(1, mesaosilla);
        preparedStatement.setString(2, estilo);
        preparedStatement.setString(3, color);
        preparedStatement.setString(4, material);
        preparedStatement.executeUpdate();
        preparedStatement.close();
    }

}
 public static void insertarinventario(Connection connection, String mesaosilla, String estilo, String color, String material) throws SQLException {
    String insertSQL = "INSERT INTO inventario material  ( nombre, cantidad, medida) VALUES (?, ?, ?, ?)";
    PreparedStatement preparedStatement = connection.prepareStatement(insertSQL);
    preparedStatement.setString(1, nombre);
    preparedStatement.setString(2, cantidad);
    preparedStatement.setString(3, medida);
    preparedStatement.executeUpdate();
    preparedStatement.close();
}

}

public static void insertarmaterial(Connection connection, String mesaosilla, String estilo, String color, String material) throws SQLException {
    String insertSQL = "INSERT INTO tu_materiales inventario material  ( nombre, cantidad, medida) VALUES (?, ?, ?, ?)";
    PreparedStatement preparedStatement = connection.prepareStatement(insertSQL);
    preparedStatement.setString(1, nombre);
    preparedStatement.setString(2, cantidad);
    preparedStatement.setString(3, medida);
    preparedStatement.executeUpdate();
    preparedStatement.close();
}

}

public static void insertarfacturacion(Connection connection, String mesaosilla, String estilo, String color, String material) throws SQLException {
    String insertSQL = "INSERT INTO facturacion  ( nit, nombre , descripcion) VALUES (?, ?, ?, ?)";
    PreparedStatement preparedStatement = connection.prepareStatement(insertSQL);
    preparedStatement.setString(1, nit);
    preparedStatement.setString(2, nombre);
    preparedStatement.setString(3, descripcion);
    preparedStatement.executeUpdate();
    preparedStatement.close();
}

}

public static void insertarempleados(Connection connection, String mesaosilla, String estilo, String color, String material) throws SQLException {
    String insertSQL = "INSERT INTO facturacion  ( nombre, numero , comision) VALUES (?, ?, ?, ?)";
    PreparedStatement preparedStatement = connection.prepareStatement(insertSQL);
    preparedStatement.setString(1, nombre);
    preparedStatement.setString(2, numero);
    preparedStatement.setString(3, comision);
    preparedStatement.executeUpdate();
    preparedStatement.close();
}

}
public static void insertarproducto(Connection connection, String mesaosilla, String estilo, String color, String material) throws SQLException {
    String insertSQL = "INSERT INTO facturacion  ( codigo, descripcion , precio) VALUES (?, ?, ?, ?)";
    PreparedStatement preparedStatement = connection.prepareStatement(insertSQL);
    preparedStatement.setString(1, codigo);
    preparedStatement.setString(2, descripcion);
    preparedStatement.setString(3, precio);
    preparedStatement.executeUpdate();
    preparedStatement.close();
}

}

public static void insertarorden(Connection connection, String mesaosilla, String estilo, String color, String material) throws SQLException {
    String insertSQL = "INSERT INTO facturacion  ( numero, fecha , proveedor) VALUES (?, ?, ?, ?)";
    PreparedStatement preparedStatement = connection.prepareStatement(insertSQL);
    preparedStatement.setString(1, numero);
    preparedStatement.setString(2, fecha);
    preparedStatement.setString(3, proveedor);
    preparedStatement.executeUpdate();
    preparedStatement.close();
}

}

//codigo que use en heidisql para crear las tablas
Crear la tabla MesaSilla
CREATE TABLE MesaSilla (
    id INT AUTO_INCREMENT PRIMARY KEY,
    estilo VARCHAR(255),
    color VARCHAR(255),
    material VARCHAR(255)
);

-- Crear la tabla InventarioMateriales
CREATE TABLE InventarioMateriales (
    id INT AUTO_INCREMENT PRIMARY KEY,
    cantidad INT,
    nombre VARCHAR(255),
    medidas VARCHAR(255)
);

-- Crear la tabla MaterialesFabricacion
CREATE TABLE MaterialesFabricacion (
    id INT AUTO_INCREMENT PRIMARY KEY,
    nombre VARCHAR(255),
    cantidad INT,
    medidas VARCHAR(255)
);

-- Crear la tabla Facturacion
CREATE TABLE Facturacion (
    id INT AUTO_INCREMENT PRIMARY KEY,
    nit VARCHAR(255),
    nombre VARCHAR(255),
    descripcion VARCHAR(255)
);

-- Crear la tabla VentasEmpleado
CREATE TABLE VentasEmpleado (
    id INT AUTO_INCREMENT PRIMARY KEY,
    nombre VARCHAR(255),
    empleado VARCHAR(255),
    comision VARCHAR(255)
);facturacion

-- Crear la tabla Producto
CREATE TABLE Producto (
    id INT AUTO_INCREMENT PRIMARY KEY,
    codigo VARCHAR(255),
    descripcion VARCHAR(255),
    precio VARCHAR(255)
);

-- Crear la tabla Orden
CREATE TABLE Orden (
    id INT AUTO_INCREMENT PRIMARY KEY,
    numeroOrden VARCHAR(255),
    fecha VARCHAR(255),
    vendedor VARCHAR(255)
);fabricafabricafabrica
