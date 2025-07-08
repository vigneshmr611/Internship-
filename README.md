# Internship-
import javafx.application.Application;
import javafx.scene.Scene;
import javafx.scene.control.*;
import javafx.scene.layout.*;
import javafx.stage.Stage;
import java.util.ArrayList;

public class LibraryApp extends Application {

    private ArrayList<String> bookList = new ArrayList<>();
    private ListView<String> listView = new ListView<>();

    @Override
    public void start(Stage primaryStage) {
        TextField bookField = new TextField();
        bookField.setPromptText("Enter book title");

        Button addButton = new Button("Add Book");
        addButton.setOnAction(e -> {
            String title = bookField.getText().trim();
            if (!title.isEmpty()) {
                bookList.add(title);
                listView.getItems().add(title);
                bookField.clear();
            }
        });

        VBox layout = new VBox(10);
        layout.setStyle("-fx-padding: 20;");
        layout.getChildren().addAll(new Label("Library Management System"), bookField, addButton, listView);

        Scene scene = new Scene(layout, 300, 400);
        primaryStage.setTitle("Mini Library System");
        primaryStage.setScene(scene);
        primaryStage.show();
    }

    public static void main(String[] args) {
        launch(args);
    }
}
