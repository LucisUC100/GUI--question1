# GUI--question1
package com.example.question1;

import javafx.application.Application;
import javafx.fxml.FXMLLoader;
import javafx.scene.Scene;
import javafx.scene.control.Button;
import javafx.scene.control.Label;
import javafx.scene.control.TextField;
import javafx.scene.layout.Pane;
import javafx.stage.Stage;

import java.io.IOException;

public class HelloApplication extends Application {
    public void start(Stage stage) throws IOException {
        Pane aPane = new Pane();
        TextField item = new TextField();
        item.relocate(10,10);
        item.setPrefSize(150,25);
        
        Label label = new Label();
        Button verify = new Button("Verify");
        verify.relocate(175,10);
        verify.setPrefSize(120,25);
        verify.setOnAction(e->{
            try {
                int value = Integer.parseInt(item.getText());
                label.setText(value+" is an integer");
                label.relocate(10,50);
            } catch (NumberFormatException ex) {
                label.setText(item.getText() + " is not an integer.");
                label.relocate(10,50);
            }
        });

        Button close = new Button("Close the window");
        close.relocate(175,45);
        close.setPrefSize(120,25);
        close.setOnAction(e -> stage.close());

        aPane.getChildren().addAll(item,verify,close,label);
        stage.setScene(new Scene(aPane,300,300));
        stage.show();
    }

    public static void main(String[] args) {
        launch();
    }
}
