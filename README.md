# Book Recommendation Copilot

Book Recommendation Copilot is a virtual assistant built with Microsoft Copilot Studio. It searches for similar books using the Google Books API and returns up to three recommendations based on a given title. The assistant can also provide short descriptions of the suggested books to help users explore new readings.

## Features

- **Searches for similar books**: Using the Google Books API, it finds books similar to the one provided by the user.
- **Returns book recommendations**: It shows up to three books with their titles and links.
- **Optional book descriptions**: If desired, it can provide short descriptions of the recommended books.

## How it Works

1. **User Interaction**:
    - The assistant prompts the user: *"Which book would you like to use as a comparison guide?"*
    - The user provides a book title.
    
2. **Search Process**:
    - The assistant searches the Google Books database to find books with similar titles or within the same genre.

3. **Return Results**:
    - The assistant returns a brief list of up to three book recommendations with their titles and links.

4. **Optional Book Descriptions**:
    - If the user asks for more information, the assistant can provide short descriptions of the recommended books to help explore new readings.

## Instructions

### You are a virtual assistant specialized in online book recommendations. Your responses should be informal, clear, and informative. Follow these steps:

1. **Ask the user**: 
    - "Which book would you like to use as a comparison guide?"

2. **Search the database**:
    - Once the user provides the book title, search for books with similar titles or genres.

3. **Return up to three book recommendations**:
    - Show a brief list (up to 3) of books, including their titles and links.

4. **Polite and friendly replies**:
    - Ensure all replies are helpful, polite, and friendly.

## Example Topic - AdaptiveDialog

```yaml
kind: AdaptiveDialog
beginDialog:
  kind: OnRecognizedIntent
  id: main
  intent:
    triggerQueries:
      - find similar book
      - recommend similar books
      - books like this one
      - suggest books like this
      - similar book recommendations
      - books that are similar
      - find related books
      - book alternatives

  actions:
    - kind: Question
      id: Question_wm9M0P
      variable: Topic.BookTitle
      prompt: Please provide a book title for recommendations.
      entity: StringPrebuiltEntity

    - kind: SendActivity
      id: SendActivity_cQvKGG
      activity: Searching for books similar to {Topic.BookTitle}...

    - kind: SendActivity
      id: SendActivity_Jv34gt
      activity: |-
        Here are some recommended books based on your title:
        1. [Book 1](https://www.googleapis.com/books/v1/volumes?q={Topic.BookTitle})
        2. [Book 2](https://www.googleapis.com/books/v1/volumes?q={Topic.BookTitle})
        3. [Book 3](https://www.googleapis.com/books/v1/volumes?q={Topic.BookTitle})

inputType: {}
outputType: {}