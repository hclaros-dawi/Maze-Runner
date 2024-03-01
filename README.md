#JUEGO MAZE RUNNER 

public class MazeRunner {
    public static String walk(int[][] maze, String[] directions) {
        int row = -1, col = -1; //Indica posición no encontrada o no válida, ya que matriz empieza en 0

       //Encontrar la posición inicial 
        for (int i = 0; i < maze.length; i++) { //Itera sobre filas matriz
            for (int j = 0; j < maze[i].length; j++) { //Itera sobre columnas matriz
                if (maze[i][j] == 2) { //Si celda actual tiene valor igual a 2, es el start point
                    row = i; //Actualiza row
                    col = j; //Actualiza col
                    break; //Sale del bucle, ya que ya se ha encontrado el punto de inicio
                }
            }
        }

        if (row == -1 || col == -1) { //Indica posición no encontrada o no válida, ya que matriz empieza en 0
            return "Maze inválido. No se encontró posición inicial";
        }

        //Iterar sobre array de direcciones
        for (String dir : directions) {
            //Moverse en la dirección especificada
            switch (dir) { //Actualiza la posición del laberinto según la dirección indicada
                case "N":
                    row--; //Decrementa el valor de row para moverse hacia arriba en el laberinto
                    break;
                case "S":
                    row++; //Incrementa el valor de row para moverse hacia abajo en el laberinto
                    break;
                case "E":
                    col++; //Incrementa el valor de col para moverse hacia la derecha en el laberinto
                    break;
                case "W":
                    col--; //Decrementa el valor de col para moverse hacia la izquierda en el laberinto
                    break;
                default:
                    return "Dirección inválida";
            }

            //Verificar que se ha salido del laberinto
            if (row < 0 || row >= maze.length || col < 0 || col >= maze[0].length) {
                return "Dead";
            }

            if (maze[row][col] == 3) { //Si celda actual tiene valor igual a 3, es el finish point
                return "Finish";
            }

            if (maze[row][col] == 1) { //Si celda actual tiene valor igual a 1, choca con una pared y muere
                return "Dead";
            }
        }

        //Si se ha completado el recorrido de todas las direcciones sin llegar al punto final, jugador está perdido
        return "Lost";
    }
}
