

#include <iostream>
#include <string>

using namespace std;

int main() {
    int mainChoice;

   
    do {
        cout << "========================================\n";
        cout << "                SMARTPICK               \n";
        cout << "========================================\n\n";
        cout << "1. Smartphone Recommendation\n";
        cout << "2. Installment Calculator\n";
        cout << "3. Exit\n";
        cout << "Enter your choice (1-3): ";
        cin >> mainChoice;

        // Input validation loop
        while (mainChoice < 1 || mainChoice > 3) {
            cout << "Invalid choice. Please enter 1, 2, or 3: ";
            cin >> mainChoice;
        }

        // Variables to store the recommended models and their exact prices
        string phone1Name = "";
        string phone2Name = "";
        double phone1Price = 0.0;
        double phone2Price = 0.0;

        // ===========================================================
        // FEATURE 1: SMARTPHONE RECOMMENDATION
        // ===========================================================
        if (mainChoice == 1) {
            int purpose, budget, feature, gamingFreq, cameraImp;

            // Tracking scores for recommendation categories
            int performanceScore = 0;
            int cameraScore = 0;
            int batteryScore = 0;
            int budgetScore = 0;

            cout << "\n========================================\n";
            cout << "        SMARTPHONE RECOMMENDATION        \n";
            cout << "========================================\n\n";

            // --- QUESTION 1 ---
            cout << "Q1. What will you mainly use your smartphone for?\n";
            cout << "1. Gaming\n";
            cout << "2. Photography\n";
            cout << "3. Study / Education\n";
            cout << "4. General Use\n";
            cout << "Enter your choice (1-4): ";
            cin >> purpose;

            while (purpose < 1 || purpose > 4) {
                cout << "Invalid choice. Please enter 1-4: ";
                cin >> purpose;
            }

            if (purpose == 1) {
                performanceScore += 3;
            } else if (purpose == 2) {
                cameraScore += 3;
            } else if (purpose == 3) {
                batteryScore += 2;
            } else {
                budgetScore += 2;
            }

            // --- QUESTION 2 ---
            cout << "\nQ2. What is your budget?\n";
            cout << "1. Below RM1,000\n";
            cout << "2. RM1,000 - RM2,000\n";
            cout << "3. RM2,001 - RM3,000\n";
            cout << "4. Above RM3,000\n";
            cout << "Enter your choice (1-4): ";
            cin >> budget;

            while (budget < 1 || budget > 4) {
                cout << "Invalid choice. Please enter 1-4: ";
                cin >> budget;
            }

            if (budget == 1) {
                budgetScore += 3;
            } else if (budget == 2) {
                batteryScore += 2;
            } else if (budget == 3) {
                performanceScore += 1;
                cameraScore += 1;
            } else {
                performanceScore += 2;
                cameraScore += 2;
            }

            // --- QUESTION 3 ---
            cout << "\nQ3. What feature is most important to you?\n";
            cout << "1. Performance & Speed\n";
            cout << "2. Camera Quality\n";
            cout << "3. Long Battery Life\n";
            cout << "Enter your choice (1-3): ";
            cin >> feature;

            while (feature < 1 || feature > 3) {
                cout << "Invalid choice. Please enter 1-3: ";
                cin >> feature;
            }

            if (feature == 1) {
                performanceScore += 3;
            } else if (feature == 2) {
                cameraScore += 3;
            } else {
                batteryScore += 3;
            }

            // --- QUESTION 4 ---
            cout << "\nQ4. How often do you play mobile games?\n";
            cout << "1. Never\n";
            cout << "2. Occasionally\n";
            cout << "3. Frequently\n";
            cout << "4. Every day\n";
            cout << "Enter your choice (1-4): ";
            cin >> gamingFreq;

            while (gamingFreq < 1 || gamingFreq > 4) {
                cout << "Invalid choice. Please enter 1-4: ";
                cin >> gamingFreq;
            }

            if (gamingFreq == 4 || gamingFreq == 3) {
                performanceScore += 3;
                batteryScore += 1;
            } else if (gamingFreq == 2) {
                performanceScore += 1;
            } else {
                budgetScore += 1;
            }

            // --- QUESTION 5 ---
            cout << "\nQ5. How important is camera quality?\n";
            cout << "1. Not important\n";
            cout << "2. Basic camera is enough\n";
            cout << "3. Important\n";
            cout << "4. Very important\n";
            cout << "Enter your choice (1-4): ";
            cin >> cameraImp;

            while (cameraImp < 1 || cameraImp > 4) {
                cout << "Invalid choice. Please enter 1-4: ";
                cin >> cameraImp;
            }

            if (cameraImp == 1) {
                budgetScore += 2;
            } else if (cameraImp == 2) {
                budgetScore += 1;
            } else if (cameraImp == 3) {
                cameraScore += 2;
            } else {
                cameraScore += 4;
            }

            // --- CALCULATING RESULTS & PRICING ---
            string recommendedCategory;
            string reason;

            if (performanceScore >= cameraScore && performanceScore >= batteryScore && performanceScore >= budgetScore) {
                recommendedCategory = "PERFORMANCE & GAMING";
                reason = "Your answers indicate that high processing power and smooth multitasking are your priorities.";
                
                if (budget == 4) {
                    phone1Name = "ASUS ROG Phone 8 Pro";
                    phone1Price = 4799.00;
                    phone2Name = "Samsung Galaxy S24 Ultra";
                    phone2Price = 5499.00;
                } else if (budget == 3) {
                    phone1Name = "iQOO 12 5G";
                    phone1Price = 2799.00;
                    phone2Name = "POCO F6 Pro";
                    phone2Price = 2299.00;
                } else {
                    phone1Name = "POCO X6 Pro 5G";
                    phone1Price = 1499.00;
                    phone2Name = "Infinix GT 20 Pro";
                    phone2Price = 1299.00;
                }
            } else if (cameraScore >= performanceScore && cameraScore >= batteryScore && cameraScore >= budgetScore) {
                recommendedCategory = "CAMERA & PHOTOGRAPHY";
                reason = "Your answers indicate that photography and high-quality imaging are your priorities.";
                
                if (budget == 4) {
                    phone1Name = "iPhone 16 Pro Max";
                    phone1Price = 5999.00;
                    phone2Name = "Google Pixel 8 Pro";
                    phone2Price = 4499.00;
                } else if (budget == 3) {
                    phone1Name = "Samsung Galaxy S23 FE";
                    phone1Price = 2699.00;
                    phone2Name = "Xiaomi 13T Pro";
                    phone2Price = 2399.00;
                } else {
                    phone1Name = "Samsung Galaxy A55 5G";
                    phone1Price = 1899.00;
                    phone2Name = "Google Pixel 7a";
                    phone2Price = 1699.00;
                }
            } else if (batteryScore >= performanceScore && batteryScore >= cameraScore && batteryScore >= budgetScore) {
                recommendedCategory = "LONG BATTERY & PRODUCTIVITY";
                reason = "Your answers indicate that long screen-on time and productivity are your priorities.";

                if (budget >= 3) {
                    phone1Name = "OnePlus 12R";
                    phone1Price = 2999.00;
                    phone2Name = "Samsung Galaxy S24+";
                    phone2Price = 4299.00;
                } else {
                    phone1Name = "Samsung Galaxy M54";
                    phone1Price = 1599.00;
                    phone2Name = "HONOR Magic6 Lite";
                    phone2Price = 1299.00;
                }
            } else {
                recommendedCategory = "BUDGET & EVERYDAY VALUE";
                reason = "Your answers indicate that affordability and general everyday use are your priorities.";
                
                if (budget == 2) {
                    phone1Name = "Redmi Note 13 Pro 5G";
                    phone1Price = 1399.00;
                    phone2Name = "Samsung Galaxy A35";
                    phone2Price = 1699.00;
                } else {
                    phone1Name = "Redmi Note 13 (4G)";
                    phone1Price = 749.00;
                    phone2Name = "Infinix Note 40";
                    phone2Price = 899.00;
                }
            }

            // Formatting output for two decimal places
            cout.setf(ios::fixed);
            cout.setf(ios::showpoint);
            cout.precision(2);

            // --- DISPLAY RECOMMENDATION ---
            cout << "\n========================================\n";
            cout << "           YOUR RECOMMENDATION          \n";
            cout << "========================================\n";
            cout << "\nRecommended Category: \n" << recommendedCategory << "\n";
            cout << "\nRecommended Models: \n";
            cout << "1. " << phone1Name << " - RM" << phone1Price << "\n";
            cout << "2. " << phone2Name << " - RM" << phone2Price << "\n";
            cout << "\nReason:\n" << reason << "\n";
            cout << "========================================\n\n";

            int nextStep;
            cout << "Would you like to calculate an installment plan for one of these phones?\n";
            cout << "1. Yes, calculate installment\n";
            cout << "2. No, return to Main Menu\n";
            cout << "Enter your choice (1-2): ";
            cin >> nextStep;

            while (nextStep < 1 || nextStep > 2) {
                cout << "Invalid choice. Please enter 1 or 2: ";
                cin >> nextStep;
            }

            if (nextStep == 1) {
                // Show choice between the two recommended phones
                int phoneSelect;
                cout << "\nWhich phone would you like to calculate installment for?\n";
                cout << "1. " << phone1Name << " (RM" << phone1Price << ")\n";
                cout << "2. " << phone2Name << " (RM" << phone2Price << ")\n";
                cout << "Enter your choice (1-2): ";
                cin >> phoneSelect;

                while (phoneSelect < 1 || phoneSelect > 2) {
                    cout << "Invalid choice. Please enter 1 or 2: ";
                    cin >> phoneSelect;
                }

                // Automatically load selected phone details into Option 2 variables
                if (phoneSelect == 1) {
                    phone1Name = phone1Name;
                    phone1Price = phone1Price;
                } else {
                    phone1Name = phone2Name;
                    phone1Price = phone2Price;
                }

                mainChoice = 2; // Jump directly to installment calculator
            }
        }

        // ===========================================================
        // FEATURE 2: INSTALLMENT CALCULATOR
        // ===========================================================
        if (mainChoice == 2) {
            string selectedPhoneName;
            double budgetAmount;
            int tenureChoice;
            int months;
            double interestRate;
            double totalInterest;
            double finalValue;
            double monthlyPayment;

            cout << "\n========================================\n";
            cout << "         INSTALLMENT CALCULATOR         \n";
            cout << "========================================\n\n";

            // If user jumped from Option 1, auto-fill phone name & price
            if (phone1Name != "") {
                selectedPhoneName = phone1Name;
                budgetAmount = phone1Price;
                cout << "Selected Phone: " << selectedPhoneName << "\n";
                cout << "Phone Price   : RM" << budgetAmount << "\n";
            } else {
                // Direct access from Main Menu
                cout << "Enter custom phone price (RM): ";
                cin >> budgetAmount;

                while (budgetAmount <= 0) {
                    cout << "Invalid input. Please enter a positive amount: RM";
                    cin >> budgetAmount;
                }
                selectedPhoneName = "Custom Selected Phone";
            }

            cout << "\nChoose your installment plan:\n";
            cout << "1. 12 months (3% per year)\n";
            cout << "2. 24 months (5% per year)\n";
            cout << "3. 36 months (8% per year)\n";
            cout << "4. 48 months (10% per year)\n";
            cout << "Enter your choice (1-4): ";
            cin >> tenureChoice;

            while (tenureChoice < 1 || tenureChoice > 4) {
                cout << "Invalid choice. Please enter 1, 2, 3, or 4: ";
                cin >> tenureChoice;
            }

            if (tenureChoice == 1) {
                months = 12;
                interestRate = 0.03;
            } else if (tenureChoice == 2) {
                months = 24;
                interestRate = 0.05;
            } else if (tenureChoice == 3) {
                months = 36;
                interestRate = 0.08;
            } else {
                months = 48;
                interestRate = 0.10;
            }

            double years = months / 12.0;
            totalInterest = budgetAmount * interestRate * years;
            finalValue = budgetAmount + totalInterest;
            monthlyPayment = finalValue / months;

            cout.setf(ios::fixed);
            cout.setf(ios::showpoint);
            cout.precision(2);

            cout << "\n========================================\n";
            cout << "          INSTALLMENT SUMMARY           \n";
            cout << "========================================\n";
            cout << "Selected Device      : " << selectedPhoneName << "\n";
            cout << "Phone Price (Budget) : RM" << budgetAmount << "\n";
            cout << "Tenure               : " << months << " months\n";
            cout << "Interest Rate        : " << (interestRate * 100) << "% per year\n";
            cout << "Total Interest       : RM" << totalInterest << "\n";
            cout << "Final Value          : RM" << finalValue << "\n";
            cout << "Monthly Payment      : RM" << monthlyPayment << "\n";
            cout << "========================================\n\n";
        }

    } while (mainChoice != 3);

    cout << "\nThank you for using the Smartphone Assistant Program!\n";
    return 0;
}