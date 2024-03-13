import javax.swing.*;
import java.awt.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;

public class LoginForm extends JFrame implements ActionListener {
    private JTextField campoLogin;
    private JPasswordField campoSenha;
    private JLabel labelResultado;

    public LoginForm() {
        super("Programa de Login");

        // Configurações da janela
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        setSize(400, 200);
        setLocationRelativeTo(null);

        // Painel principal
        JPanel painel = new JPanel(new GridLayout(3, 2));

        // Componentes
        JLabel labelLogin = new JLabel("Login:");
        campoLogin = new JTextField();
        JLabel labelSenha = new JLabel("Senha:");
        campoSenha = new JPasswordField();
        JButton botaoOK = new JButton("OK");
        botaoOK.addActionListener(this);
        labelResultado = new JLabel();

        // Adiciona a logomarca do IFMT
        ImageIcon logoIcon = new ImageIcon("ifmt_logo.png");
        JLabel labelLogo = new JLabel(logoIcon);

        // Adiciona componentes ao painel
        painel.add(labelLogo);  // Logomarca do IFMT
        painel.add(new JLabel()); // Espaço vazio para manter a grade
        painel.add(labelLogin);
        painel.add(campoLogin);
        painel.add(labelSenha);
        painel.add(campoSenha);
        painel.add(botaoOK);
        painel.add(labelResultado);

        // Adiciona painel à janela
        add(painel);

        // Exibir janela
        setVisible(true);
    }

    @Override
    public void actionPerformed(ActionEvent e) {
        if (e.getActionCommand().equals("OK")) {
            String login = campoLogin.getText();
            String senha = new String(campoSenha.getPassword());
            labelResultado.setText("Login: " + login + "\nSenha: " + senha);
        }
    }

    public static void main(String[] args) {
        SwingUtilities.invokeLater(new Runnable() {
            public void run() {
                new LoginForm();
            }
        });
    }
}
