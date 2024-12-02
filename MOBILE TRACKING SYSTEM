import java.awt.*;
import java.awt.event.*;
import java.util.Random;

public class MobileTrackingSystemAWT extends Frame {

    private TextField tfMobileNumber, tfMobileId, tfImeiNumber;
    private TextArea taOutput;
    private Choice choiceMenu;
    private Button btnSubmit, btnReset;
    private String mobileNumber = null;
    private String mobileId = null;
    private String imeiNumber = null;

    public MobileTrackingSystemAWT() {
        // Frame Setup
        setTitle("Mobile Tracking System");
        setSize(500, 500);
        setLayout(new BorderLayout());

        // Panel for Input Fields
        Panel inputPanel = new Panel(new GridLayout(4, 2, 10, 10));
        inputPanel.setBackground(Color.LIGHT_GRAY);

        inputPanel.add(new Label("Mobile Number:"));
        tfMobileNumber = new TextField(30);
        inputPanel.add(tfMobileNumber);

        inputPanel.add(new Label("Mobile ID:"));
        tfMobileId = new TextField(30);
        inputPanel.add(tfMobileId);

        inputPanel.add(new Label("IMEI Number:"));
        tfImeiNumber = new TextField(30);
        inputPanel.add(tfImeiNumber);

        // Menu for Choices
        inputPanel.add(new Label("Select Action:"));
        choiceMenu = new Choice();
        choiceMenu.add("Enter User Details");
        choiceMenu.add("Track Mobile");
        choiceMenu.add("Lock Device");
        choiceMenu.add("Exit");
        inputPanel.add(choiceMenu);

        add(inputPanel, BorderLayout.NORTH);

        // Output Area
        taOutput = new TextArea("", 10, 50, TextArea.SCROLLBARS_VERTICAL_ONLY);
        taOutput.setEditable(false);
        add(taOutput, BorderLayout.CENTER);

        // Panel for Buttons
        Panel buttonPanel = new Panel();
        buttonPanel.setLayout(new FlowLayout());

        btnSubmit = new Button("Submit");
        btnReset = new Button("Reset");
        buttonPanel.add(btnSubmit);
        buttonPanel.add(btnReset);

        add(buttonPanel, BorderLayout.SOUTH);

        // Event Handlers
        btnSubmit.addActionListener(e -> handleChoice());
        btnReset.addActionListener(e -> resetFields());
        addWindowListener(new WindowAdapter() {
            public void windowClosing(WindowEvent we) {
                System.exit(0);
            }
        });

        setVisible(true);
    }

    private void handleChoice() {
        String selectedAction = choiceMenu.getSelectedItem();
        switch (selectedAction) {
            case "Enter User Details":
                enterUserDetails();
                break;
            case "Track Mobile":
                trackMobile();
                break;
            case "Lock Device":
                lockDevice();
                break;
            case "Exit":
                System.exit(0);
                break;
        }
    }

    private void enterUserDetails() {
        mobileNumber = tfMobileNumber.getText().trim();
        mobileId = tfMobileId.getText().trim();
        imeiNumber = tfImeiNumber.getText().trim();

        if (!mobileNumber.isEmpty() && !mobileId.isEmpty() && !imeiNumber.isEmpty()) {
            taOutput.setText("User details saved successfully.\n");
            showDialog("Success", "User details have been saved.");
        } else {
            taOutput.setText("Invalid input. All fields must be filled.\n");
            showDialog("Error", "All fields must be filled to proceed.");
            mobileNumber = null;
            mobileId = null;
            imeiNumber = null;
        }
    }

    private void trackMobile() {
        if (isValidUser()) {
            Random random = new Random();
            String[] districts = {"Chennai", "Coimbatore", "Trichy", "Madurai", "Salem", "Thanjavur", "Tirunelveli", "Vellore", "Erode", "Dindigul"};
            String[] areas = {"North", "South", "East", "West"};

            String district = districts[random.nextInt(districts.length)];
            String area = areas[random.nextInt(areas.length)];

            double latitude = 8.0 + (12.0 - 8.0) * random.nextDouble();
            double longitude = 76.0 + (80.0 - 76.0) * random.nextDouble();

            taOutput.setText(String.format("Tracking mobile...\nLocation: %s (%s Area)\nLatitude: %.4f, Longitude: %.4f\n",
                    district, area, latitude, longitude));
            showDialog("Tracking Info", "Mobile tracked successfully!");
        } else {
            taOutput.setText("Please provide valid user details.\n");
            showDialog("Error", "Please enter valid user details before tracking.");
        }
    }

    private void lockDevice() {
        if (isValidUser()) {
            taOutput.setText("The mobile device has been locked.\n");
            showDialog("Success", "The mobile has been locked successfully.");
        } else {
            taOutput.setText("Please provide valid user details.\n");
            showDialog("Error", "Please enter valid user details before locking the device.");
        }
    }

    private boolean isValidUser() {
        return mobileNumber != null && mobileId != null && imeiNumber != null &&
               !mobileNumber.isEmpty() && !mobileId.isEmpty() && !imeiNumber.isEmpty();
    }

    private void resetFields() {
        tfMobileNumber.setText("");
        tfMobileId.setText("");
        tfImeiNumber.setText("");
        taOutput.setText("");
        choiceMenu.select(0);
        mobileNumber = null;
        mobileId = null;
        imeiNumber = null;
        showDialog("Reset", "All fields have been reset.");
    }

    private void showDialog(String title, String message) {
        Dialog dialog = new Dialog(this, title, true);
        dialog.setLayout(new FlowLayout());
        dialog.setSize(300, 150);
        dialog.add(new Label(message));
        Button okButton = new Button("OK");
        okButton.addActionListener(e -> dialog.setVisible(false));
        dialog.add(okButton);
        dialog.setVisible(true);
    }

    public static void main(String[] args) {
        new MobileTrackingSystemAWT();
    }
}
