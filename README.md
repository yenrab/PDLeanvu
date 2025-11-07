# PDLearnvu

PDLearnvu is an intelligent learning assistant that helps university juniors learn patterns, data structures, beginning Elixir, and OTP through competency-based education. The system uses a conversational approach with two learning advisors who work together to provide personalized guidance and support.

## Architecture

PDLearnvu uses a **1-mode-3-actor** pattern:

### Mode

- **Learning Mode** - The single mode where all learning interactions occur

### Actors

1. **LearningActor1** (Senior Learning Advisor) - Experienced educator knowledgeable in Andragogy and competency-based education
2. **LearningActor2** (Junior Learning Advisor) - Enthusiastic educator with complementary teaching style
3. **LearningStateActor** (State Manager) - Manages learning state, student information, and understanding levels

## Learning Topics

PDLearnvu covers 23 competency topics organized into four areas:

### Language Topics
1. Variables, Tuples, Lists, and List BIFs
2. Functions
3. Stateless Processes
4. Stateful Processes

### OTP Topics
5. gen_server
6. gen_statem
7. Supervisors

### Patterns Topics
8. Factory Pattern
9. State Pattern
10. Lazy Computation Pattern
11. Functors
12. Monoids
13. Monads
14. Memoization
15. Chaining
16. Beautiful Code

### Data Structure Topics
17. Queues
18. Deques
19. Binary Search Trees
20. Red-Black Trees
21. Leftist Min-Heaps
22. Random Access Lists
23. Tries

## Features

### Personalized Learning

- **Two-Person Conversation**: Two learning advisors respond separately to create a natural, engaging learning experience
- **Student Name Recognition**: Personas ask for and remember the student's name, using it when addressing them directly
- **Adaptive Teaching**: Code examples and guidance adapt based on the student's understanding level

### Teaching Approach

- **Language Topics**: Provides Elixir code examples starting simple, gradually increasing complexity based on rubric assessment
- **Patterns/Data Structures/OTP Topics**: Guides students to write their own code without providing solutions
- **Rubric-Based Feedback**: Uses competency rubrics to guide feedback and help students self-assess
- **Understanding Levels**: Tracks student understanding per topic (Not Yet Ready, Competent, Exceptional)

### Quality Assurance

- **Verification System**: Both personas verify analogies and examples against source files before presenting
- **Consensus Building**: Personas discuss privately when they disagree, presenting the most accurate option
- **Assessment Task Detection**: Proactively detects when students are trying to use PDLearnvu for assessment practice and redirects them to PDIntervu

### Natural Interaction

- **Name-Based Communication**: Personas always refer to themselves by name, not "I", creating clear distinction between personas and student
- **Encouraging Tone**: Friendly and supportive but not overly enthusiastic (avoids phrases like "Great job!" or "Fantastic!")
- **Topic Switching**: Students can switch topics mid-conversation; personas adapt seamlessly

## File Structure

```
PDLearnvu/
├── PDLearnvu.jsonld              # Main agent definition and execution instructions
├── competencies.jsonld           # List of all available learning topics
├── patterns.jsonld                # Pattern definitions and examples
├── data_structures_pseudocode.jsonld  # Pseudocode examples for data structures
├── data_structure_rubic.jsonld   # Assessment rubric for data structures
├── patterns_rubric.jsonld        # Assessment rubric for design patterns
├── pseudocode_primer.jsonld      # Pseudocode primer and guidelines
├── LICENSE                        # License file
└── README.md                      # This file
```

## Usage

PDLearnvu is designed to be executed as an AALang prompt. When loaded, the PDLearnvu agent will:

1. **Introduce the learning advisors** by name
2. **Ask for the student's name**
3. **Display all available topics** organized by area
4. **Wait for topic selection** and begin personalized learning
5. **Adapt teaching style** based on topic type and student understanding level

### Learning Flow

1. Student selects a topic from the list
2. Learning advisors engage in conversation about the topic
3. For Language topics: Code examples are provided with increasing complexity
4. For Patterns/Data Structures/OTP: Students are guided to write their own code
5. Understanding level is assessed and tracked
6. Students can switch topics or ask for analogies/examples at any time

## Rubrics

PDLearnvu uses rubrics to guide feedback and help students understand their progress:

- `data_structure_rubic.jsonld` - Assessment criteria for data structures competency
- `patterns_rubric.jsonld` - Assessment criteria for design patterns competency

**Note**: Rubrics are used for informational purposes to guide learning, not for rigorous assessment. For actual assessment practice, students should use [PDIntervu](https://github.com/yenrab/PDIntervu).

## Integration with PDIntervu

PDLearnvu is designed to complement [PDIntervu](https://github.com/yenrab/PDIntervu), a technical interview assessment tool:

- **PDLearnvu**: For learning and understanding concepts
- **PDIntervu**: For practicing job interviews and receiving assessments

When PDLearnvu detects that a student is trying to use it for assessment practice, it will:
- Remind them that memorization doesn't work for job interviews
- Reference PDIntervu as the appropriate tool for interview practice
- Continue focusing on understanding concepts and problem-solving approaches

## Technical Details

- **Format**: JSON-LD (JSON for Linking Data)
- **Vocabulary**: Uses AALang.org specification (`https://aalang.org/spec/`)
- **State Management**: Centralized state management via LearningStatePersona
- **Message Protocol**: Uses AALang messaging with semantic filtering for actor coordination
- **Language Support**: Personas adapt their names based on user's language preference (default: English)

## State Management

The LearningStatePersona maintains:
- `studentName` - The student's name
- `currentTopic` - Currently selected learning topic
- `conversationHistory` - Recent conversation entries
- `languagePreference` - User's language preference (default: English)
- `userUnderstandingLevel` - Mapping of topics to understanding levels (Not Yet Ready, Competent, Exceptional)

## License

This project is licensed under a custom "No-Sale License" that:

- ✅ Allows use for private, educational, and business purposes
- ✅ Allows modification and distribution
- ✅ Allows products built with PDLearnvu to be sold freely
- ❌ Prohibits selling PDLearnvu itself or any derivative works

See the [LICENSE](LICENSE) file for full details.

## Copyright

Copyright (c) 2025 Lee S. Barney

---

**Created using [AALang](https://aalang.org) and [gab](https://aalang.org)**

