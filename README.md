# Facundia Demo

A Spring Boot demonstration application showcasing the capabilities of the [Facundia](https://github.com/jorgeamadosoria/facundia) library - a powerful Java library for Spanish language word manipulation and processing.

## Overview

Facundia Demo is a web-based application that provides an interactive interface to demonstrate the various features of the Facundia library. It allows users to perform advanced Spanish language operations including number conversion, pluralization, syllabication, and verb conjugation.

## Features

The application demonstrates four main functionalities of the Facundia library:

### 1. **Cardinal Number Writing** (`cardinal`)
Converts numeric values to their textual representation in Spanish. The library follows the long scale format up to quadrillions (cuatrillones), which is the largest quantity recognized by the Real Academia Española.

**Example:**
- Input: `123`
- Output: `ciento veintitrés`

### 2. **Pluralization** (`plural`)
Generates the plural form of any Spanish word following a comprehensive set of structural rules and a list of exceptional plurals. The library uses structural analysis rather than semantic analysis.

**Example:**
- Input: `casa`
- Output: `casas`

### 3. **Syllabication** (`syllabicate`)
Divides words into syllables using a tonic approach. For instance, the word "desahucio" is divided as "de-sahu-cio" (tonic) rather than "des-ahu-cio" (etymological).

**Example:**
- Input: `palabra`
- Output: `pa·la·bra`

### 4. **Verb Conjugation** (`conjugate`)
Generates all conjugations of a Spanish verb across different tenses, moods, and persons. The system has been tested with over 9,000 Spanish verbs extracted from the official DRAE (Diccionario de la Real Academia Española).

**Supported conjugations:**
- Indicativo: Presente, Copretérito, Futuro, Pretérito, Pospretérito
- Subjuntivo: Futuro, Presente, Pretérito
- Imperativo
- Infinitivo, Gerundio, Participio

**Example:**
- Input: `hablar`
- Output: All conjugated forms across all tenses and persons

**Note:** Some verbs have dual forms (e.g., asolar, desolar, engrosar), in which case only one form is generated. Defective verbs are generated as if all personal forms existed.

## Technology Stack

### Backend
- **Spring Boot 2.2.2** - Main application framework
- **Spring Web** - RESTful API support
- **Maven** - Dependency management and build tool
- **Java 8** - Programming language
- **Facundia 3.0.7** - Spanish language processing library

### Frontend
- **Spectre.css** - Lightweight CSS framework
- **jQuery 3.4.1** - JavaScript library for DOM manipulation
- **Font Awesome** - Icon library

### Deployment
- **Heroku** - Cloud platform (configured via Procfile)
- **JitPack** - Maven repository for Facundia library

## Project Structure

```
facundia/
├── src/
│   ├── main/
│   │   ├── java/org/jasr/facundia/demo/
│   │   │   ├── FacundiaDemoApplication.java    # Spring Boot main application
│   │   │   ├── ServletInitializer.java         # Servlet configuration
│   │   │   └── controller/
│   │   │       └── DemoController.java         # REST API endpoints
│   │   └── resources/
│   │       ├── application.properties          # Application configuration
│   │       └── static/
│   │           ├── index.html                  # Main web interface
│   │           ├── css/                        # Stylesheets
│   │           ├── webfonts/                   # Font files
│   │           └── verbos.txt                  # 9185 Spanish verbs dataset (6MB+)
│   └── test/
│       └── java/org/jasr/facundia/demo/
│           └── FacundiaDemoApplicationTests.java
├── pom.xml                                     # Maven configuration
├── Procfile                                    # Heroku deployment configuration
└── .gitignore                                  # Git ignore rules
```

## API Endpoints

The application exposes the following REST endpoints:

### `GET /version`
Returns the current version of the Facundia library.

**Response:** String (version number)

### `GET /cardinal?number={number}`
Converts a number to its cardinal text representation in Spanish.

**Parameters:**
- `number` (string): The number to convert

**Response:** String (textual representation)

### `GET /plural?word={word}`
Returns the plural form of a Spanish word.

**Parameters:**
- `word` (string): The singular word

**Response:** String (plural form)

### `GET /syllabicate?word={word}`
Divides a word into syllables.

**Parameters:**
- `word` (string): The word to syllabicate

**Response:** List of strings (syllables)

### `GET /conjugate?infinitive={infinitive}`
Returns all conjugations of a Spanish verb.

**Parameters:**
- `infinitive` (string): The verb in infinitive form

**Response:** Array of strings (all conjugated forms)

## Building and Running

### Prerequisites
- Java 8 or higher
- Maven 3.x

### Local Development

1. Clone the repository:
```bash
git clone https://github.com/jorgeamadosoriaramirez/facundia.git
cd facundia
```

2. Build the project:
```bash
mvn clean package
```

3. Run the application:
```bash
mvn spring-boot:run
```

4. Access the web interface:
```
http://localhost:8080
```

### Deployment to Heroku

The application includes a `Procfile` for Heroku deployment:

```bash
heroku create
git push heroku main
```

## Dependencies

The Facundia library includes another library for syllable separation using a Deterministic Finite Automaton (DFA). The DFA library can be found at [https://github.com/jorgeamadosoria/dfa](https://github.com/jorgeamadosoria/dfa).

## Resources

- **Verb Dataset**: The application includes a comprehensive list of 9,185 Spanish verbs (6MB+) used for conjugation rule verification. Access it at `/verbos.txt` when the application is running.
- **Related Projects**:
  - [Facundia Library](https://github.com/jorgeamadosoria/facundia)
  - [DFA Library](https://github.com/jorgeamadosoria/dfa)

## Limitations

- The library uses structural analysis, not semantic analysis
- Some verbs with dual forms only generate one variant
- Defective verbs are treated as complete verbs

## License

This project is for demonstration purposes only. No copyright.

## Author

**Jorge Amado Soria Ramirez**
- Email: jorgeamadosoria@gmail.com
- GitHub: [@jorgeamadosoria](https://github.com/jorgeamadosoria)
- CV: [https://live-cv-jasr.herokuapp.com/](https://live-cv-jasr.herokuapp.com/)

## Acknowledgments

This project is a programming exercise and personal discipline demonstration, created to prove that it could be done. Facundia has no commercial objectives.
