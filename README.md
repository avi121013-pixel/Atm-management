#include <stdio.h>

int main()
{
    int pin = 1234;
    int enteredPin;
    int choice;
    int newPin;
    float balance = 5000;
    float amount;

    printf("================================\n");
    printf("       ATM MANAGEMENT SYSTEM\n");
    printf("================================\n");

    printf("\nEnter Your ATM PIN: ");
    scanf("%d", &enteredPin);

    if (enteredPin != pin)
    {
        printf("\nIncorrect PIN! Access Denied.\n");
        return 0;
    }

    printf("\nLogin Successful!\n");

    while (1)
    {
        printf("\n========== ATM MENU ==========\n");
        printf("1. Check Balance\n");
        printf("2. Deposit Money\n");
        printf("3. Withdraw Money\n");
        printf("4. Change PIN\n");
        printf("5. Exit\n");
        printf("==============================\n");

        printf("Enter Your Choice: ");
        scanf("%d", &choice);

        switch (choice)
        {
            case 1:
                printf("\nYour Current Balance: Rs. %.2f\n",
                       balance);
                break;

            case 2:
                printf("\nEnter Amount to Deposit: ");
                scanf("%f", &amount);

                if (amount > 0)
                {
                    balance = balance + amount;
                    printf("\nMoney Deposited Successfully!\n");
                    printf("Updated Balance: Rs. %.2f\n",
                           balance);
                }
                else
                {
                    printf("\nInvalid Amount!\n");
                }
                break;

            case 3:
                printf("\nEnter Amount to Withdraw: ");
                scanf("%f", &amount);

                if (amount <= 0)
                {
                    printf("\nInvalid Amount!\n");
                }
                else if (amount > balance)
                {
                    printf("\nInsufficient Balance!\n");
                }
                else
                {
                    balance = balance - amount;
                    printf("\nPlease Collect Your Cash.\n");
                    printf("Remaining Balance: Rs. %.2f\n",
                           balance);
                }
                break;

            case 4:
                printf("\nEnter New 4-Digit PIN: ");
                scanf("%d", &newPin);

                if (newPin >= 1000 && newPin <= 9999)
                {
                    pin = newPin;
                    printf("\nPIN Changed Successfully!\n");
                }
                else
                {
                    printf("\nPlease Enter a Valid 4-Digit PIN.\n");
                }
                break;

            case 5:
                printf("\nThank You for Using Our ATM!\n");
                printf("Have a Nice Day!\n");
                return 0;

            default:
                printf("\nInvalid Choice! Try Again.\n");
        }
    }

    return 0;
}
