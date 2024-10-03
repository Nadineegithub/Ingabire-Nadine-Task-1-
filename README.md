```SQL

CREATE TABLE Users (
    UserID INT PRIMARY KEY,
    UserName VARCHAR(50) NOT NULL
);
CREATE TABLE Profiles (
    ProfileID INT PRIMARY KEY,
    UserID INT,
    Bio VARCHAR(255),
    FOREIGN KEY (UserID) REFERENCES Users(UserID)
);
CREATE TABLE Customers (
    CustomerID INT PRIMARY KEY,
    CustomerName VARCHAR(100)
);
CREATE TABLE Orders (
    OrderID INT PRIMARY KEY,
    CustomerID INT,
    OrderDate DATE,
    FOREIGN KEY (CustomerID) REFERENCES Customers(CustomerID)
);
INSERT INTO Users (UserID, UserName) VALUES (2, 'JaneSmith');
INSERT INTO Users (UserID, UserName) VALUES (3, 'AliceJohnson');
INSERT INTO Profiles (ProfileID, UserID, Bio) VALUES (2, 2, 'Data Scientist and AI enthusiast.');
INSERT INTO Profiles (ProfileID, UserID, Bio) VALUES (1, 1, 'Software Developer from NY.');
INSERT INTO Customers (CustomerID, CustomerName) VALUES (1, 'Acme Corporation');
INSERT INTO Customers (CustomerID, CustomerName) VALUES (2, 'Globex Inc.');
INSERT INTO Orders (OrderID, CustomerID, OrderDate) VALUES (1, 1, TO_DATE('2024-10-01', 'YYYY-MM-DD'));
INSERT INTO Orders (OrderID, CustomerID, OrderDate) VALUES (2, 2, TO_DATE('2024-10-02', 'YYYY-MM-DD'));

SELECT Users.UserName, Profiles.Bio
FROM Users
LEFT JOIN Profiles ON Users.UserID = Profiles.UserID;

SELECT Profiles.Bio, Users.UserName
FROM Profiles
RIGHT JOIN Users ON Users.UserID = Profiles.UserID;

commit;

rollback;


```

###CONCEPTUAL MODELS
![table 1](https://github.com/user-attachments/assets/6ac61850-02a6-4cac-857b-69d7bb287b38)
![table 2](https://github.com/user-attachments/assets/c3c066c9-7ac3-482b-9ea6-f1e39330456b)
![table 3](https://github.com/user-attachments/assets/462de7a7-31b6-412e-af88-1e0b59cd7140)
![table 4](https://github.com/user-attachments/assets/80ca545b-c8e2-4d7a-8eea-a8a01bfd4ba3)
