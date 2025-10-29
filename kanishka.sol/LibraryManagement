// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

/// @title Simple Library Management System
/// @author 
/// @notice This contract lets the owner add books and users borrow or return them.

contract LibraryManagement {
    // Owner of the contract (library admin)
    address public owner;

    // Structure to hold book information
    struct Book {
        uint256 id;
        string title;
        string author;
        uint256 copies; // number of available copies
    }

    // Map book IDs to Book structs
    mapping(uint256 => Book) public books;

    // Track who borrowed which book
    mapping(address => mapping(uint256 => bool)) public borrowed;

    // Total number of books added
    uint256 public bookCount;

    // Events
    event BookAdded(uint256 bookId, string title, string author, uint256 copies);
    event BookBorrowed(address indexed borrower, uint256 bookId);
    event BookReturned(address indexed borrower, uint256 bookId);

    // Modifier to restrict actions to the owner
    modifier onlyOwner() {
        require(msg.sender == owner, "Only owner can perform this action");
        _;
    }

    constructor() {
        owner = msg.sender; // set deployer as owner
    }

    /// @notice Add a new book to the library
    /// @param _title The title of the book
    /// @param _author The author of the book
    /// @param _copies Number of available copies
    function addBook(string memory _title, string memory _author, uint256 _copies) public onlyOwner {
        require(_copies > 0, "Copies must be greater than zero");
        bookCount++;
        books[bookCount] = Book(bookCount, _title, _author, _copies);
        emit BookAdded(bookCount, _title, _author, _copies);
    }

    /// @notice Borrow a book from the library
    /// @param _bookId The ID of the book to borrow
    function borrowBook(uint256 _bookId) public {
        Book storage book = books[_bookId];
        require(book.id != 0, "Book does not exist");
        require(book.copies > 0, "No copies available");
        require(!borrowed[msg.sender][_bookId], "You already borrowed this book");

        book.copies--;
        borrowed[msg.sender][_bookId] = true;
        emit BookBorrowed(msg.sender, _bookId);
    }

    /// @notice Return a borrowed book
    /// @param _bookId The ID of the book to return
    function returnBook(uint256 _bookId) public {
        Book storage book = books[_bookId];
        require(borrowed[msg.sender][_bookId], "You haven't borrowed this book");

        book.copies++;
        borrowed[msg.sender][_bookId] = false;
        emit BookReturned(msg.sender, _bookId);
    }

    /// @notice Get book details by ID
    function getBook(uint256 _bookId) public view returns (Book memory) {
        return books[_bookId];
    }
}

