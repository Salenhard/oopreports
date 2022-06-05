# UI Language

## JAVA FXML

### Загрузка FXML файла
```JAVA
public class BotApplication extends Application {
    @Override
    public void start(Stage stage) throws IOException {
        FXMLLoader fxmlLoader = new FXMLLoader(BotApplication.class.getResource("login-view.fxml"));
        Scene scene = new Scene(fxmlLoader.load(), 352.0, 434.0);
        stage.getIcons().add(new Image("file:bot_icon.png"));
        stage.setTitle("Login");
        stage.setScene(scene);
        stage.setResizable(false);
        stage.show();
    }
```
### Добавление компонентов

Теперь пришло время добавить некоторые компоненты. метку (label):

```xml
<?xml version="1.0" encoding="UTF-8"?>

<?import javafx.scene.control.Label?>

<!--Допускается только один компонент на корневом уровне-->
<Label>Hello World!</Label>
```

VBox, который размещает свои дочерние элементы вертикально друг над другом.

```xml
<?xml version="1.0" encoding="UTF-8"?>

<?import javafx.scene.control.Label?>
<?import javafx.scene.layout.VBox?>
<?import javafx.scene.control.Button?>

<VBox>
    <Label text="Hello world!"/>
    <Label text="This is a simple demo application."/>
    <Button text="Click me!"/>
</VBox>
```
### FX Namespace

Существует пара элементов и атрибутов FXML, которые по умолчанию недоступны. Для досупа нужно добавить пространство имён (Namespace) FXML, чтобы сделать их доступными. Его необходимо добавить к корневому компоненту:

```xml
<?xml version="1.0" encoding="UTF-8"?>
    ...

<VBox xmlns="http://javafx.com/javafx"
      xmlns:fx="http://javafx.com/fxml">
    ...
</VBox>
````

Теперь можно использовать новые элементы из пространства имен ```fx```.

```xml
<Label fx:id="mainTitle" text="Hello world!"/>
```
Атрибут ```fx:id``` является уникальным идентификатором компонента, который можно использовать для ссылки на компонент из других частей нашего FXML и даже из нашего контроллера.

### style
```xml
style = "-fx-background-color - устанавливает цвет фона
-fx-text-fill - устанавливает цвет текста
-fx-border-radius - устанавливает закругление у обьекта в пикселях
-fx-border-color - устанавливает цвет border
-fx-background-image - устанавливает фоновую картинку
-fx-font-size - устанавливает размер шрифта
-fx-font-name - устанавливает шрифт"
```

### Скрипты

Первое, что нужно сделать, это добавить обработчик события onAction для кнопки.
```xml
<Button fx:id="mainButton" text="Click me!" onAction="buttonClicked()"/>
```
Обратите внимание на fx:id, это идентификатор, который будет использоваться позже для ссылки на кнопку.

Теперь нужно предоставить функцию, которая будет вызвана для обработки события. Ее можно определить внутри тега ```fx:script```. Можно использовать различные языки для написания скрипта, JavaScript, Groovy или Clojure

### Пример
Пример окна с чатом из приложения чатбот
```xml
<?xml version="1.0" encoding="UTF-8"?>

<?import javafx.geometry.Insets?>
<?import javafx.scene.control.Button?>
<?import javafx.scene.control.Label?>
<?import javafx.scene.control.TextArea?>
<?import javafx.scene.control.TextField?>
<?import javafx.scene.layout.HBox?>
<?import javafx.scene.layout.VBox?>
<?import javafx.scene.text.Font?>

<VBox prefHeight="352.0" prefWidth="494.0" spacing="5.0" style="-fx-background-color: #c5ecfc;" xmlns="http://javafx.com/javafx/17" xmlns:fx="http://javafx.com/fxml/1" fx:controller="com.example.chat_bot.ChatController">
    <padding>
        <Insets bottom="10.0" left="10.0" right="10.0" top="5.0" />
    </padding>
   <Label text="Чат:" textFill="#0e2da8">
      <font>
         <Font name="Calibri" size="16.0" />
      </font></Label>
   <TextArea fx:id="chatTextArea" editable="false" prefHeight="492.0" prefWidth="394.0" style="-fx-control-inner-background: white; -fx-text-fill: #0c2aa8; -fx-border-color: white; -fx-background-radius: 5; -fx-border-radius: 5;">
      <font>
         <Font name="Calibri" size="16.0" />
      </font></TextArea>
   <HBox prefHeight="25.0" prefWidth="167.0" spacing="5.0">
      <children> <!-- устнановка другого цвета фона рамки и закругления у рамки, также цвет текста  style="-fx-background-color: white; -fx-border-color: white; -fx-background-radius: 10; -fx-border-radius: 10; -fx-text-fill: #0c2aa8;" -->
         <TextField fx:id="inputTextField" minWidth="360.0" onKeyPressed="#onSendKeyPressed" prefHeight="37.0" prefWidth="360.0" style="-fx-background-color: white; -fx-border-color: white; -fx-background-radius: 10; -fx-border-radius: 10; -fx-text-fill: #0c2aa8;" HBox.hgrow="ALWAYS">
            <font>
               <Font name="Calibri" size="16.0" />
            </font></TextField>                 <!-- установка другого цвета и закругления style="-fx-background-color: #fffdb8; -fx-background-radius: 10;" -->
          <Button fx:id="sendButton" minWidth="107.0" onAction="#onSendButtonClick" prefHeight="37.0" prefWidth="107.0" style="-fx-background-color: #fffdb8; -fx-background-radius: 10;" text="Отправить" textFill="#0c2aa8" HBox.hgrow="NEVER">
            <font>
               <Font name="Calibri" size="16.0" />
            </font></Button>
      </children>
      <VBox.margin>
         <Insets />
      </VBox.margin>
   </HBox>
</VBox>
```
