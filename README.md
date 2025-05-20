# NBA Top 5 Players' Salary Insurance Premium Pricing
NBA Salary Insurance Premium Pricing Model

This actuarial project models and prices salary insurance premiums for the top 5 highest-paid NBA players on each team, based on the probability that they miss 41 or more games due to injury in a single season. The policy covers career-impacting or season-ending injuries, and will pay 80% of a player's salary per game missed after 41 consecutive games due to injury.

📥 Data Collection

Manually gathered from multiple public sources, the dataset includes player-specific data such as:

Team affiliation

Age

Weight

Position

Contract duration and salary

Historical games played and missed

Injury history (including need for surgery)

Data was cleaned and entered into Excel for modeling purposes.

📊 Variables & Key Formulas

Injury Projection

To estimate the expected games missed, I calculated:

Career missed games and missed games over the last 2 seasons

Weighted average to estimate next season's expected missed games

Injury % = Expected missed games / 82

Adjusted for season-ending injuries using conditional probability:

~61% of NBA players get injured per year

~10% of those have season-ending injuries (41+ missed games)

Conditional Probability = 10% / 61% ≈ 16.39%

Final Season-Ending Injury % = Injury % × 0.1639

Expected Loss

expected_loss = annual_salary × salary_coverage × probability_41+_games

Where salary coverage = 0.80, based on policy payout rules (80% of salary per game missed).

Premium Formula

premium = [expected_loss / (1 + i)] × age_factor × contract_factor × position_factor × injury_factor × (1 + risk_load) × (1 + admin_load)

Where:

i = 3% (interest rate used to discount present value)

Risk Load = 25% (conservative buffer for volatility and profit)

Admin Load = 5% (expenses, overhead)

Actuarial Assumptions

Factor Type

Criteria

Factor

Age

<25 = 0.8; 25–29 = 1.0; 30–34 = 1.3; 35+ = 1.7



Contract

1 yr = 0.9; 2+ yrs = 1.1



Position

C = 1.2; all others = 1.0



Injury

Based on injury type and surgery status (see below)

0.9–1.8

Injury Factor Criteria

Injury Type

Examples

Factor

Rationale

No Injury History

—

0.9

Strong durability signal

Minor Injury (No Surgery)

Mild ankle sprain, contusion

1.0

Baseline

Moderate Injury (No Surgery)

Tendinitis, muscle strains

1.2

Recurrence risk

Moderate Injury (With Surgery)

Meniscus repair

1.3

Higher downtime but recoverable

Major Lower Body Injury

ACL, Achilles, patellar tendon

1.5

Career-threatening risk

Multiple Major Injuries

ACL + Achilles combo

1.7

Significantly elevated risk

Recent Major Injury (<12 mo)

Return from ACL/Achilles

1.6–1.8

High recurrence risk

Chronic Conditions

Degenerative back/knee issues

1.6

Long-term degradation

✅ Premium Validation

📈 Premium % of Salary

After calculating the final premium for each player, I divided it by their salary:

premium_rate = premium / annual_salary

Average Premium Rate: 5.72%

✅ Matches the real-world range of 4–7% for NBA salary insurance

📉 Loss Ratio Analysis

loss_ratio = expected_loss / premium

Average Loss Ratio: 0.47

While slightly lower than the 70–80% typical range, this is acceptable given:

Limited player-level data

High claim volatility

Large per-game salary payouts and need for conservatism

📌 Key Takeaways

🔎 Manual player-level data sourcing ensures personalized risk assessment

🧮 Factor-based actuarial pricing mirrors real-world underwriting

✅ Premiums and loss ratios align with professional benchmarks

💡 Can be extended to simulate real insurance portfolios, sensitivity testing, or reinsurance layers

📂 File Contents

Top 5 Player Salary Insurance.xlsx: Raw data, assumptions, and final premium model

README.md: Project methodology and summary

📬 Contact

For questions, improvements, or collaboration, feel free to reach out or submit a pull request.

This project demonstrates applied actuarial thinking, insurance product design, and Excel modeling for niche high-cost risk exposures like professional athlete contracts.
