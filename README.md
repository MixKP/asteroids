# Asteroids Game

## Project Overview

This project is a **JavaFX-based recreation of the classic arcade game Asteroids**, developed as part of the **SE233 Advanced Programming** course. The game features a player-controlled spaceship navigating through space, shooting asteroids and enemy ships while avoiding collisions.

## Game Description

**Asteroids** is a space-themed multidirectional shooter where players control a triangular spaceship in an asteroid field. The objective is to destroy asteroids and enemy ships to earn points while avoiding collisions that deplete the player's lives.

### Key Features

- **Classic Asteroids Gameplay**: Navigate a spaceship in 2D space with realistic physics (momentum, rotation, friction)
- **Multiple Enemy Types**: 
  - Asteroids that break apart when hit
  - Normal Enemies (slime-like entities)
  - Elite Enemies with special attack patterns
- **Weapon Systems**:
  - Normal Attack (standard projectiles)
  - Special Attack (powered-up shots with cooldown)
- **Player Abilities**:
  - Shield mechanic for temporary invulnerability
  - Random warp teleportation to escape danger
- **Score System**: Points awarded for destroying asteroids and enemies
- **Lives System**: Three lives; game over when all are lost
- **Animated Sprites**: Smooth animations for all game entities

## Technology Stack

- **Java 21**: Core programming language
- **JavaFX 21**: GUI framework for graphics and animations
- **Maven**: Build automation and dependency management
- **JUnit 5**: Unit testing framework
- **TestFX**: JavaFX testing library
- **Mockito**: Mocking framework for tests
- **Log4j 2**: Logging framework

## Project Architecture

The project follows the **Model-View-Controller (MVC)** architectural pattern:

### Model (`se233.asteroids.model`)
- **Character**: Abstract base class for all game entities
- **PlayerShip**: Player-controlled spaceship with movement, shooting, and special abilities
- **Asteroid**: Destructible space rocks
- **NormalEnemies**: Basic enemy ships
- **EliteEnemies**: Advanced enemy ships with more complex behavior
- **Projectile** (Abstract): Base class for all attacks
  - **NormalAttack**: Standard player projectile
  - **SpecialAttack**: Powered-up player projectile
  - **EnemiesAttack**: Normal enemy projectile
  - **EliteAttack**: Elite enemy projectile
- **AnimatedSprite**: Handles sprite animation
- **Explosion**: Visual effect for destroyed entities

### View (`se233.asteroids.view`)
- **GameStage**: Main game window, manages UI elements (score, lives, game over screen)

### Controller (`se233.asteroids.controller`)
- **GameStageController**: Main game loop coordinator
- **PlayerShipController**: Handles player input and ship updates
- **AsteroidController**: Manages asteroid spawning and behavior
- **NormalEnemiesController**: Controls normal enemy behavior
- **EliteEnemiesController**: Controls elite enemy behavior
- **NormalAttackController**: Manages player normal projectiles
- **SpecialAttackController**: Manages player special projectiles
- **EnemiesAttackController**: Manages normal enemy projectiles
- **EliteAttackController**: Manages elite enemy projectiles
- **ExplosionController**: Manages explosion animations

### Utilities (`se233.asteroids.util`)
- **ImageUtil**: Image loading and processing
- **SpriteUtil**: Sprite manipulation and collision detection

## Gameplay Mechanics

### Controls
| Action | Key |
|--------|-----|
| Move Forward | W |
| Move Backward | S |
| Move Left | A |
| Move Right | D |
| Rotate Left | Q |
| Rotate Right | E |
| Shoot (Normal) | SPACE |
| Special Shoot | R |
| Random Warp | SHIFT |

### Game Rules

1. **Objective**: Destroy asteroids and enemies to earn points
2. **Lives**: Start with 3 lives; lose a life when hit by asteroids, enemies, or enemy projectiles
3. **Game Over**: Occurs when all lives are lost
4. **Scoring**: 
   - Points earned for destroying asteroids
   - Points earned for destroying enemies
5. **Abilities**:
   - **Shield**: Temporary invulnerability after taking damage
   - **Special Attack**: More powerful shots with limited cooldown
   - **Warp**: Random teleportation with cooldown (6 seconds)

## Building and Running

### Prerequisites

- **Java 21** or higher
- **Maven 3.6+** (included via Maven Wrapper)

### Build the Project

```bash
# Using Maven Wrapper (recommended)
./mvnw clean package

# Or using system Maven
mvn clean package
```

### Run the Game

```bash
# Using Maven
./mvnw javafx:run

# Or run the packaged JAR
java -jar target/asteroids-*.jar
```

### Run Tests

```bash
./mvnw test
```

## Project Structure

```
asteroids/
├── src/
│   ├── main/
│   │   ├── java/
│   │   │   └── se233/asteroids/
│   │   │       ├── controller/     # Game logic controllers
│   │   │       ├── model/          # Game entities and data models
│   │   │       ├── view/           # UI components
│   │   │       ├── util/           # Utility classes
│   │   │       ├── Launcher.java   # Main application entry point
│   │   │       └── JarLauncher.java # JAR entry point
│   │   └── resources/
│   │       └── se233/asteroids/assets/
│   │           ├── asteroids/      # Asteroid sprites
│   │           ├── background/     # Background images
│   │           ├── elite/          # Elite enemy sprites
│   │           ├── playerShip/     # Player ship sprites
│   │           ├── projectile/     # Projectile sprites
│   │           └── slime/          # Normal enemy sprites
│   └── test/
│       └── java/                   # Unit tests
├── pom.xml                         # Maven configuration
└── README.md                       # This file
```

## Development

### Code Organization

- **Separation of Concerns**: MVC pattern ensures clear separation between game logic, rendering, and user input
- **Object-Oriented Design**: Inheritance hierarchy for characters and projectiles
- **Animation System**: Reusable animated sprite system for all game entities
- **Collision Detection**: Efficient hitbox-based collision system
- **Game Loop**: 60 FPS game loop using JavaFX Timeline

### Key Design Patterns

1. **Model-View-Controller (MVC)**: Separates game state, rendering, and control logic
2. **Abstract Factory**: Character and Projectile base classes
3. **Observer Pattern**: Event handling for keyboard input
4. **Singleton**: Controllers maintain single instances for managing game entities

## Credits

- **Course**: SE233 Advanced Programming
- **Game Concept**: Based on the classic Atari Asteroids (1979)
- **Framework**: JavaFX 21
- **Sprites**: Custom sprite assets for educational purposes

## License

This project is created for educational purposes as part of the SE233 course.
