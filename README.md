## Project Overview
When it comes to machine learning, it is widely known that building an AI model requires a high volume of training data. In the context of PlaiCraft.ai, researchers aim to collect 10,000 hours of multiplayer Minecraft gameplay to train an AI agent. 

One major challenge is acquiring and maintaining an *active* player base—participants who will dedicate substantial time playing on the server and generating training data. While video games like Minecraft are often assumed to appeal primarily to a younger, male audience, recent research suggests that gaming demographics are broadening (Engelstätter & Ward, 2022). However, there is limited research on the specific demographics of Minecraft players.

This predictive analysis seeks to answer the question: **Which age range(s) contribute the most playtime on the PlaiCraft Minecraft server?**

By answering this question, we aim to infer potential player contributions and make informed decisions on which demographics to target for recruitment efforts.

---

## Data Description
The analysis utilizes `players.csv`, which contains information on a sample of PlaiCraft.ai players.

Each row in the dataset represents a unique player. The dataset consists of **196 observations** (excluding the header row). Below is a detailed description of the dataset's variables:

| Variable Name    | Description | Type | Issues |
|-----------------|-------------|------|--------|
| `experience` | Player's familiarity with Minecraft. Ordered values: Noob → Amateur → Regular → Pro → Veteran. | `<chr>` | No apparent issues. |
| `subscribe` | Indicates if the player is subscribed to the mailing list (`TRUE` = subscribed, `FALSE` = not subscribed). | `<lgl>` | No apparent issues. |
| `hashedEmail` | Encoded email address of the player, likely for privacy purposes. | `<chr>` | No apparent issues. |
| `played_hours` | Total hours the player was online on the server, either actively playing or away from the keyboard. | `<dbl>` | Potential ambiguity: Does this metric measure active playtime or total online time (including AFK)? |
| `name` | First name of the player. | `<chr>` | Ethical concerns regarding anonymity, mitigated by omitting surnames. |
| `gender` | Player's gender. | `<chr>` | Lack of representation of certain genders may impact the validity of conclusions. |
| `age` | Age of the player (in years). | `<dbl>` | Older age groups are severely underrepresented, limiting predictive accuracy. |
| `individualId` | Meaning unclear, but variable type (`<lgl>`) suggests a `TRUE/FALSE` value. | `<lgl>` | Variable name is readable but not informative. |
| `organizationName` | Possibly indicates player affiliation with an unspecified organization. | `<lgl>` | No apparent issues. |

---

## Methodology
For our project, we will be analyzing the `players.csv` data specifically. Our goal is to understand how the factors `age` and `gender` influence the general *playing time* on the server.  

We will analyze this by graphing the data:
- **Graph 1**: `age` vs `played_hours`, with coloring by `gender` (**scatterplot with line of best fit**)

### Research Question:
This analysis seeks to determine what *kinds* of players are most likely to contribute data. To address this, we examine the independent variables (`age` and `gender`) and plot them against the dependent variable (`played_hours`), which represents data contribution.

We are using `players.csv` because it includes the critical variables for this analysis (`played_hours` and `age`) and focuses on total playing time rather than specific session times.

### Predictive Analysis:
To answer this question, we will use **linear regression** to predict `played_hours` using `age`. This will provide insight into the age groups most likely to contribute data. A higher total playing time suggests a greater contribution to the study.

### Justification for Linear Regression:
We chose **linear regression** over **KNN regression** for the following reasons:
1. **Prediction beyond the training set**: KNN regression struggles when predicting beyond the range of training data, whereas linear regression allows for extrapolation.
2. **Scalability**: KNN regression becomes slower as the dataset grows. While `players.csv` only contains around 200 observations, as PlaiCraft.ai continues collecting data, future analyses will benefit from the efficiency of linear regression.

Thus, linear regression is a more scalable and practical approach for our study.

---

## Goals & Methodology
- **Objective:** Identify the age range(s) contributing the most playtime.
- **Approach:** Perform statistical analysis and data visualization on `players.csv`.
- **Outcome:** Provide insights to optimize recruitment strategies for training PlaiCraft.ai’s AI agent.

---
