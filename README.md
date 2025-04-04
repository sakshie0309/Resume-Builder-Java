# Resume-Builder-Java
import java.awt.*;
import java.awt.event.*;
import java.io.File;
import java.io.FileWriter;
import java.io.IOException;

public class ResumeBuilder extends Frame {
    private TextField nameField, phoneField, emailField, educationField, skillsField, languagesField, experienceField;

    public ResumeBuilder() {
        setTitle("Resume Builder");
        setSize(400, 400);
        setLayout(new GridLayout(8, 2));

        add(new Label("Name: "));
        nameField = new TextField();
        add(nameField);

        add(new Label("Phone: "));
        phoneField = new TextField();
        add(phoneField);

        add(new Label("Email: "));
        emailField = new TextField();
        add(emailField);

        add(new Label("Education: "));
        educationField = new TextField();
        add(educationField);

        add(new Label("Skills: "));
        skillsField = new TextField();
        add(skillsField);

        add(new Label("Languages Known: "));
        languagesField = new TextField();
        add(languagesField);

        add(new Label("Experience: "));
        experienceField = new TextField();
        add(experienceField);

        Button generateButton = new Button("Generate Resume");
        generateButton.addActionListener(new ActionListener() {
            public void actionPerformed(ActionEvent e) {
                generateResume();
            }
        });
        add(generateButton);

        addWindowListener(new WindowAdapter() {
            public void windowClosing(WindowEvent windowEvent) {
                System.exit(0);
            }
        });

        setVisible(true);
    }

    private void generateResume() {
        String name = nameField.getText();
        String phone = phoneField.getText();
        String email = emailField.getText();
        String education = educationField.getText();
        String skills = skillsField.getText();
        String languages = languagesField.getText();
        String experience = experienceField.getText();

        String htmlContent = "<html>\n" +
                "<head>\n" +
                "<meta charset=\"UTF-8\">\n" +
                "<meta name=\"viewport\" content=\"width=device-width, initial-scale=1.0\">\n" +
                "<title>" + name + "'s Resume</title>\n" +
                "<style>\n" +
                "body {\n" +
                "  margin: 0;\n" +
                "  padding: 0;\n" +
                "  font-family: 'Arial', sans-serif;\n" +
                "  display: flex;\n" +
                "  height: 100vh;\n" +
                "  background-color: #f2f2f2;\n" +
                "  margin-left: 100px;\n" +
                "}\n" +
                "\n" +
                ".a4-sheet {\n" +
                "  display: flex;\n" +
                "  margin: 20px;\n" +
                "  border: 1px solid #ccc;\n" +
                "  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);\n" +
                "}\n" +
                "\n" +
                ".left-section,\n" +
                ".right-section {\n" +
                "  padding: 20px;\n" +
                "  display: flex;\n" +
                "  flex-direction: column;\n" +
                "  justify-content: center;\n" +
                "  align-items: center;\n" +
                "  font-size: 18px;\n" +
                "}\n" +
                "\n" +
                ".left-section {\n" +
                "    flex: 2;\n" +
                "  background-color: #92d036;\n" +
                "  color: #171616;\n" +
                "  border: 3px solid #000000;\n" +
                "}\n" +
                "\n" +
                ".right-section {\n" +
                "    flex: 2.9;\n" +
                "  background-color: #000000;\n" +
                "  text-align: center;\n" +
                "  color: #c2c1c1;\n" +
                "  border: 3px solid #000000;\n" +
                "}\n" +
                "</style>\n" +
                "</head>\n" +
                "<body>\n" +
                "<div class=\"a4-sheet\">\n" +
                "  <div class=\"left-section\">\n" +
                "      <img src=\"https://upload.wikimedia.org/wikipedia/commons/thumb/f/f5/Circle-icons-flower.svg/768px-Circle-icons-flower.svg.png\" width=\"200px\" alt=\"\">\n" +
                "    <h2>" + name + "</h2>\n" +
                "    <p>Phone: " + phone + "</p>\n" +
                "    <p>Email: " + email + "</p>\n" +
                "  </div>\n" +
                "  <div class=\"right-section\">\n" +
                "    <h2>Skills</h2>\n" +
                "    <p>" + skills + "</p>\n" +
                "\n" +
                "    <h2>Education</h2>\n" +
                "    <p>" + education + "</p>\n" +
                "\n" +
                "    <h2>Languages Known</h2>\n" +
                "    <p>" + languages + "</p>\n" +
                "\n" +
                "    <h2>Experience</h2>\n" +
                "    <p>" + experience + "</p>\n" +
                "  </div>\n" +
                "</div>\n" +
                "</body>\n" +
                "</html>";

        try {
            File htmlFile = new File("resume.html");
            FileWriter writer = new FileWriter(htmlFile);
            writer.write(htmlContent);
            writer.close();
            System.out.println("Resume generated successfully. Opening 'resume.html'...");

            // Open the HTML file using the default web browser
            Desktop.getDesktop().browse(htmlFile.toURI());
        } catch (IOException e) {
            e.printStackTrace();
        }
    }

    public static void main(String[] args) {
        new ResumeBuilder();
    }
}
