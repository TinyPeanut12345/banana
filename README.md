graph TD
    subgraph Self-Checkout Process (Level 1)
        1.1(Process Purchase Items) --> 1.2(Update Inventory On Hand)
        1.1 -- Item UPC, Item Details --> D1[Items]
        Customer -- Item UPC --> 1.1
        1.1 -- Amount Due --> Customer
        1.1 -- Items Purchased --> D2[Inventory On Hand]
        1.2 -- Inventory Update --> D2

        Customer -- Payment --> 1.3(Process Payment)
        1.3 -- CC Payment --> CreditCardClearingHouse[Credit Card Clearing House]
        1.3 -- Debit Payment --> AutomatedClearingHouse[Automated Clearing House]
        CreditCardClearingHouse -- CCCH Response --> 1.3
        AutomatedClearingHouse -- ACH Response --> 1.3
        1.3 -- Payment Confirmation --> 1.4(Record Sales Transaction Details)

        1.4 -- Final Transaction Details --> D3[Sales Transactions]
        1.4 -- Receipt --> Customer
    end

    style D1 fill:#eee,stroke:#333,stroke-width:2px
    style D2 fill:#eee,stroke:#333,stroke-width:2px
    style D3 fill:#eee,stroke:#333,stroke-width:2px
    style CreditCardClearingHouse fill:#eee,stroke:#333,stroke-width:2px
    style AutomatedClearingHouse fill:#eee,stroke:#333,stroke-width:2px
    style Customer fill:#eee,stroke:#333,stroke-width:2px
