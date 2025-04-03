# public void editarDispositivo() {
    Dispositivo dispositivo = seleccionarDispositivo("Seleccione el dispositivo a editar:");
    if (dispositivo != null) {
        boolean editar = true;
        while (editar) {
            String opcion = JOptionPane.showInputDialog(
                "¿Qué desea editar?\n1. Marca\n2. Precio\n" + 
                (dispositivo instanceof PC ? "3. Memoria RAM\n4. Disco Duro\n" : "3. Tamaño\n") +
                "5. Salir"
            );

            if (opcion == null || opcion.equals("5")) {
                editar = false;
            } else {
                switch (opcion) {
                    case "1":
                        dispositivo.marca = JOptionPane.showInputDialog("Nueva marca:", dispositivo.marca);
                        break;
                    case "2":
                        dispositivo.precio = solicitarPrecio();
                        break;
                    case "3":
                        if (dispositivo instanceof PC) {
                            ((PC) dispositivo).setMemoriaRAM(JOptionPane.showInputDialog("Nueva RAM:", ((PC) dispositivo).getMemoriaRAM()));
                        } else {
                            ((Tablet) dispositivo).setTamaño(JOptionPane.showInputDialog("Nuevo tamaño:", ((Tablet) dispositivo).getTamaño()));
                        }
                        break;
                    case "4":
                        if (dispositivo instanceof PC) {
                            ((PC) dispositivo).setDiscoDuro(JOptionPane.showInputDialog("Nuevo Disco Duro:", ((PC) dispositivo).getDiscoDuro()));
                        } else {
                            JOptionPane.showMessageDialog(null, "Opción no válida.");
                        }
                        break;
                    default:
                        JOptionPane.showMessageDialog(null, "Opción no válida.");
                        break;
                }
            }
        }
        guardarInventario(); // Guardar cambios
        JOptionPane.showMessageDialog(null, "Dispositivo actualizado.");
    }
}
