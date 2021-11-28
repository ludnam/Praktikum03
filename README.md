# Praktikum03

package org.hsd.inflab.se1c4;

import java.util.Arrays;
import javafx.application.Application;
import javafx.event.ActionEvent;
import javafx.event.EventHandler;
import javafx.geometry.Insets;
import javafx.scene.Scene;
import javafx.scene.control.Button;
import javafx.scene.control.TextField;
import javafx.scene.layout.BorderPane;
import javafx.scene.layout.HBox;
import javafx.stage.Stage;

/**
 * JavaFX App
 */
public class App extends Application {
	
	static int bereich = 49 - 1 + 1;

    @Override
    public void start(Stage stage) {

    	HBox hbox = new HBox();
    	BorderPane bp = new BorderPane();
    	Scene buehne =  new Scene(bp,400,100);
    	    	
    	hbox.setPadding(new Insets(10, 20, 20, 20));
    	hbox.setSpacing(20);
    	
    	TextField textFeld_1 = new TextField();
    	TextField textFeld_2 = new TextField();
    	TextField textFeld_3 = new TextField();
    	TextField textFeld_4 = new TextField();
    	TextField textFeld_5 = new TextField();
    	TextField textFeld_6 = new TextField();
    	
    	Button buttonZiehen = new Button();
    	buttonZiehen.setText("Ziehen");
    	
    	
    	hbox.getChildren().addAll(textFeld_1,textFeld_2,textFeld_3,textFeld_4,textFeld_5,textFeld_6);
    	bp.setTop(hbox);
    	bp.setCenter(buttonZiehen);
  

    	stage.setTitle("Lottoziehung");
        stage.setScene(buehne);
        stage.show();
        
        //Button Ziehen
        
        buttonZiehen.setOnAction(new EventHandler<ActionEvent>() {
			
			@Override
			public void handle(ActionEvent event) {
				
				int[] zahlen = new int[6];
				int zahl_Temp;
				
				for (int i = 0; i < zahlen.length; i++) {
					
					zahl_Temp = (int) (Math.random()*bereich) + 1;
					
					Arrays.sort(zahlen);

					if ((Arrays.binarySearch(zahlen, zahl_Temp)>=0)) {
						
						i--;
						
					}
					else {
						zahlen[0] = zahl_Temp;
					}
					
				}
				
				
				Arrays.sort(zahlen);
				
				textFeld_1.setText(String.valueOf(zahlen[0]));
				textFeld_2.setText(String.valueOf(zahlen[1]));
				textFeld_3.setText(String.valueOf(zahlen[2]));
				textFeld_4.setText(String.valueOf(zahlen[3]));
				textFeld_5.setText(String.valueOf(zahlen[4]));
				textFeld_6.setText(String.valueOf(zahlen[5]));

			}
		});
        
    }

    public static void main(String[] args) {
        launch();
    }

}
