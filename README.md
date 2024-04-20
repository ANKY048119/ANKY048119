- 👋 Hi, I’m @ANKY048119
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...

<!---
ANKY048119/ANKY048119 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
import pandas as pd
from sklearn.ensemble import RandomForestRegressor

# Load your dataset
data = pd.read_csv('player_performance.csv')

# Feature engineering
# Assume 'data' has columns for player stats
features = data[['runs', 'wickets', 'strike_rate', 'economy_rate']]
target = data['dream11_points']

# Initialize the model
model = RandomForestRegressor()

# Split data into training and testing sets
from sklearn.model_selection import train_test_split
X_train, X_test, y_train, y_test = train_test_split(features, target, test_size=0.2)

# Train the model
model.fit(X_train, y_train)

# Predict points for a new match
new_match_data = pd.read_csv('new_match_data.csv')
predicted_points = model.predict(new_match_data)

# Select top 11 players based on predicted points
predicted_team = new_match_data.iloc[predicted_points.argsort()[-11:]]
print(predicted_team)

