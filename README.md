import java.awt.Color;
import java.awt.Robot;
import java.awt.AWTException;

public class TelaPiscante {
    public static void main(String[] args) {
        try {
            Robot robot = new Robot();
            Color corOriginal = robot.getPixelColor(0, 0); // Obtém a cor original da tela

            while (true) {
                robot.delay(500); // Aguarda 500 milissegundos (0,5 segundos)

                robot.keyPress(17); // Pressiona a tecla Ctrl
                robot.keyPress(18); // Pressiona a tecla Alt
                robot.keyPress(70); // Pressiona a tecla F

                robot.keyRelease(70); // Libera a tecla F
                robot.keyRelease(18); // Libera a tecla Alt
                robot.keyRelease(17); // Libera a tecla Ctrl

                Color corAtual = robot.getPixelColor(0, 0); // Obtém a cor atual da tela

                if (corAtual.equals(corOriginal)) {
                    robot.delay(500); // Aguarda 500 milissegundos (0,5 segundos)
                } else {
                    break; // Sai do loop se a cor da tela mudar
                }
            }
        } catch (AWTException e) {
            e.printStackTrace();
        }
    }
}
