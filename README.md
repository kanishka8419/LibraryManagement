🧠 Features

👑 Owner-controlled: Only the contract owner can add new books.

📖 Book tracking: Each book has a title, author, and number of available copies.

🙋 Borrow & return system: Users can borrow available books and return them later.

🔔 Events: Emits events when books are added, borrowed, or returned for easy on-chain tracking.

🧩 Smart Contract Overview
Function	Description	Access
addBook(string title, string author, uint256 copies)	Add a new book to the library	Owner only
borrowBook(uint256 bookId)	Borrow a book if available	Any user
returnBook(uint256 bookId)	Return a borrowed book	Any user
getBook(uint256 bookId)	Get details of a specific book	Public view
⚙️ How to Run
1. Open in Remix

Go to Remix IDE
.

Create a new file named LibraryManagement.sol.

Paste the smart contract code inside it.

2. Compile

Select Solidity Compiler on the left panel.

Set the compiler version to 0.8.0 or higher.

Click Compile LibraryManagement.sol.

3. Deploy

Go to the Deploy & Run Transactions tab.

Select the LibraryManagement contract.

Click Deploy.

4. Interact

Once deployed, you can:

Call addBook("1984", "George Orwell", 3) — adds a new book (only the contract owner can do this).

Call borrowBook(1) — borrows the book with ID 1.

Call returnBook(1) — returns that book.

Call getBook(1) — views book details.
<img width="1920" height="1080" alt="Screenshot (145)" src="https://github.com/user-attachments/assets/38b0b46f-b6d9-4b98-bd8f-e3bfbf8f87d1" />
