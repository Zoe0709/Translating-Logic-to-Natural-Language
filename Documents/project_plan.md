By Wednesday, March 9, you have to submit to the GitLab repository a plan with (1) a description of the project, (2) all the resources to be used (textbooks, manuals, software, articles, etc.), (3) division of work, (4) weekly schedule. The project plan should have 2 - 3 pages. Use markdown, not Word; use LaTeX only if you need the math features. All group members have to commit to the repository for the plan to receive a grade. The description has to elaborate on the problem, how the implementation will be tested and measured (if efficiency is the goal), how it will be documented, and what insight you hope to gain from it. You will receive feedback on the project plan.

# COMPSCI 4TB3 Group 19 Final Project Plan


## Overview:
**Course:** COMPSCI 4TB3\
**Term:** 2022 Winter\
**Topic:** Translating Logic to Natural Language (Topic 11)\
**Group Number:** 19\
**Group Members:**\
1). Haoyang Tao, taoh4\
2). Huaijin Ning, ningh4\
3). Run Zhang, zhangr75


## Description of the project
The purpose of this project is to find a method to convert logical formulas into natural language. It is known that the foundation of all mathematical reasoning is logic. Elements like symbolic sets, relations, functions, and mathematical logic are usually involved in logic formulas, which are not easy to comprehend by natural language. The common use of logic formulas is in textual specification languages and graphical specification languages to express preconditions, postconditions, invariants, and other properties. However, these expressions can be hard to read. Therefore, what we are going to do is developing a translator that translates logic structure/expressions into natural language (English sentences). Details of the project are expalined below. 

### Plan in details
- Build a scanner.
- Build a propositional-logic parser:
    - Symobols will include: OR (∨) , AND (∧) , NOT/Negation (¬), Implication (⇒) and Equivalence / If and only if (≡ or ⇔).
    - Build rules to translate parsed propositional-logic expressions to natural laguage or simple mathematical prose.
- (After finishing building the propositional-logic parser) Build a predicate-logic (first order logic) parser:
    - Symbols will include: For All (∀), Exist (∃).
- Create comprehensive test cases for both parsers.
- (Optional) Build an evaluator if time permits.
- Implimentation will be done in Jupyter Notebook and testing will be done through creating test cells.


## Resources to be used

- Textbook by David Gries and Fred B. Schneider: A Logical Approach to Discrete Math
- Propositional Logic in Discrete Math: https://ggc-discrete-math.github.io/logic.html
- Propositional Logic Syntax: https://www.logicthrupython.org/chapter01.pdf
- Getting Started with the CalcCheck Language: http://calccheck.mcmaster.ca/CalcCheckDoc/GettingStartedWithCalcCheck.html
- Getting Started with CalcCheckWeb: http://calccheck.mcmaster.ca/CalcCheckDoc/GettingStartedWithCalcCheckWeb.html
- CalcCheck Syntax: http://calccheck.mcmaster.ca/CalcCheckDoc/2019-12-20_CalcCheck-Syntax-Hints.pdf
- CalcCheck Theorem List: https://www.cas.mcmaster.ca/~kahl/CS2DM3/2018/2DM3-2018-Mid-November-ThmReference.html


## Division of work
- Haoyang Tao, taoh4
    - Implementation of AND, OR, Negation, Implication and Equivalence.
    - Contribute toward documentation and presentation materials.

- Huaijin Ning, ningh4
    - Implementation of Scanner and Forall.
    - Research part of predicate-logic.
    - Contribute toward documentation and presentation materials.

- Run Zhang, zhangr75
    - Implementation of Scanner and Exist.
    - Research part of predicate-logic.
    - create test cases.
    - Contribute toward documentation and presentation materials.


## Weekly schedule

|Milestone       |Deliverable                    |Date                         |
|----------------|-------------------------------|-----------------------------|
| Completion of Scanner                          | Gather resources and conduct deeper research into the project topic. Discuss and make agreement on the structure/API of the project Implementation of scanner, and rules for parsing (first half).                  |Mar 14 - Mar 20 > Week 1  |
| Completion of propositional-logic              | Implementation of scanner, and rules for parsing (second half). Implement and complete parts for propositional-logic.  |Mar 21 - Mar 27 > Week 2    |
| Completion of predicate-logic                  | Implement and complete parts for predicate-logic. Verify the program integrity and make adjustments as necessary.      |Mar 28 - Apr 3 > Week 3 |
| Test and measure project implementation, presentation preparation  | Test the project, make changes to the code to fix bugs and improve, prepare presentation materials  |Apr 4 - Apr 10 > Week 4|
|Project presentation preparation                | Prepare and practice for the presentation, final check everything                                       |Apr 11 - Apr 19 > Week 5|
|Project presentation | Presentation to the class |Apr 19 - Apr 20  |
