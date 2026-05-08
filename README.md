import sys

def mtn_momo_balance():
    # Configuration
    SECRET_PIN = "2345"
    ACCOUNT_BALANCE = 5450.00
    CURRENCY = "UGX"  # Can be GHS, RWF, etc. depending on region

    print("--- MTN Mobile Money Simulation ---")
    
    # Step 1: Dial Code
    ussd_input = input("Dial USSD Code (e.g., *165# or *170#): ")
    
    if ussd_input not in ["*165#", "*170#"]:
        print("Connection problem or invalid MMI code.")
        return

    # Step 2: Main Menu
    print("\nMTN MoMo")
    print("1) Send Money")
    print("2) Airtime & Bundles")
    print("3) Withdraw Cash")
    print("4) Payments")
    print("5) My Wallet")
    
    choice = input("Select option: ")

    # Step 3: Wallet Menu
    if choice == "5":
        print("\nMy Wallet")
        print("1) Check Balance")
        print("2) Mini Statement")
        print("3) Change PIN")
        
        wallet_choice = input("Select option: ")
        
        if wallet_choice == "1":
            # Step 4: PIN Entry
            attempts = 3
            while attempts > 0:
                entered_pin = input("\nEnter 4-digit PIN: ")
                
                if entered_pin == SECRET_PIN:
                    print("\n-------------------------------")
                    print(f"Y'ello! Your available balance is {CURRENCY} {ACCOUNT_BALANCE:,.2f}.")
                    print("-------------------------------")
                    break
                else:
                    attempts -= 1
                    if attempts > 0:
                        print(f"Incorrect PIN. You have {attempts} attempts left.")
                    else:
                        print("Too many incorrect attempts. Your session has timed out.")
        else:
            print("Feature not implemented in this simulation.")
    else:
        print("Service temporarily unavailable.")

if __name__ == "__main__":
    mtn_momo_balance()