#📌 Task 04 – Analyzing Accident Data(SkillCraft Internship)

## 🚆 Railway Crossing Accident Data Analysis

## 📋 Project Overview

This project analyzes traffic accident data to identify patterns related to road conditions, weather, and time of day. The objective is to visualize accident hotspots and contributing factors to provide actionable insights for transportation safety improvement.

**Internship**: SkillCraft Data Science Program  
**Task**: Task 4 - Traffic Accident Pattern Analysis  
**Duration**: [Project Timeline]  
**Status**: ✅ Completed

## 🎯 Objectives# 1️⃣ Ensure Date column is datetime
df['Date'] = pd.to_datetime(df['Date'], errors='coerce')

# 2️⃣ Create a Year-Month column
df['Year_Month'] = df['Date'].dt.to_period('M').dt.to_timestamp()

# 3️⃣ Count incidents per month
monthly_counts = df.groupby('Year_Month').size().reset_index(name='Incidents')

# 4️⃣ Get top 10 months with the highest incidents
top10 = monthly_counts.nlargest(10, 'Incidents').sort_values('Year_Month')

# 5️⃣ Ensure Year_Month is datetime for plotting
top10['Year_Month'] = pd.to_datetime(top10['Year_Month'])

# 6️⃣ Plot
plt.figure(figsize=(12, 6))
plt.plot(
    top10['Year_Month'].to_numpy(),
    top10['Incidents'].to_numpy(),
    marker='o',
    linestyle='-'
)

plt.title('Top 10 Months with Highest Incident Counts')
plt.xlabel('Month')
plt.ylabel('Number of Incidents')
plt.grid(True)

# 7️⃣ Format x-axis as "Mon YYYY"
plt.gca().xaxis.set_major_formatter(mdates.DateFormatter('%b %Y'))

# 8️⃣ Set limits slightly outside the top10 range
plt.xlim(
    top10['Year_Month'].min() - pd.Timedelta(days=15),
    top10['Year_Month'].max() + pd.Timedelta(days=15)
)

plt.xticks(rotation=45)
plt.tight_layout()
plt.show()

- Analyze temporal patterns in railway crossing accidents
- Identify correlation between weather conditions and accident frequency
- Map geographical accident hotspots across different regions
- Examine demographic factors and equipment-related incidents
- Generate data-driven safety recommendations for policy makers

## 📊 Dataset Information

- **Source**: Railway Accident Database (railacc.csv)
- **Records**: 10,000+ accident incidents
- **Features**: 160+ variables
- **Time Period**: Multi-year dataset (2016+)
- **Key Variables**: Date, Time, Weather, Location, Equipment Type, User Demographics

## 🛠️ Technical Stack

```
Programming Language: Python 3.8+
Libraries:
├── pandas          # Data manipulation and analysis
├── numpy           # Numerical computations  
├── matplotlib      # Data visualization
├── seaborn         # Statistical visualizations
└── datetime        # Time series processing
```

## 📈 Analysis Methodology

### 1. Data Preprocessing
- DateTime conversion and formatting standardization
- Missing value identification and handling
- Data type optimization for memory efficiency

### 2. Exploratory Data Analysis
- **Temporal Analysis**: Hour-wise and day-wise incident patterns
- **Weather Impact**: Correlation analysis between weather conditions and accidents
- **Geographic Mapping**: State-wise and regional incident distribution
- **Demographic Profiling**: Age distribution and risk factor analysis

### 3. Statistical Analysis
- Pattern recognition and trend identification
- Correlation coefficient calculations
- Frequency distribution analysis

## 🔍 Key Findings

### ⏰ Temporal Patterns
- **Peak Hours**: Identified specific hours with highest accident frequency
- **Day Variations**: Significant differences between weekdays and weekends
- **Seasonal Trends**: Monthly patterns revealing high-risk periods

### 🌤️ Weather Insights  
- **Counter-intuitive Discovery**: 70% of accidents occur during clear weather conditions
- **Visibility Impact**: Strong correlation between poor visibility and accident severity
- **Weather Paradox**: Clear weather may lead to driver overconfidence

### 🗺️ Geographic Analysis
- **Hotspot States**: Top 5 states with highest accident rates identified
- **Equipment Correlation**: Different train types show varying accident patterns
- **Regional Factors**: Infrastructure and demographic influences on accident rates

## 📊 Visualizations

The project includes comprehensive visualizations:
- Incident distribution by hour of day
- Weather condition impact analysis
- State-wise accident frequency mapping
- Age demographic distribution charts
- Equipment type incident correlation
- Monthly trend analysis with peak identification

## 💼 Business Impact & Recommendations

### Immediate Actions
- Enhanced safety protocols during identified peak hours
- Targeted awareness campaigns for clear weather conditions
- Infrastructure improvements in high-risk geographic areas

### Policy Implications
- Resource allocation optimization based on hotspot analysis
- Age-specific safety education programs
- Equipment-specific safety protocols

## 🚧 Challenges Overcome

1. **Data Quality Issues**: Handled inconsistent datetime formats across 160+ columns
2. **Memory Optimization**: Processed large dataset (10K+ records) efficiently
3. **Complex Visualization**: Created meaningful insights from multi-dimensional data
4. **Pattern Recognition**: Identified counter-intuitive trends requiring deep analysis

## 📁 Repository Structure

```
railway-accident-analysis/
│
├── data/
│   └── railacc.csv                 # Raw dataset
├── notebooks/
│   └── task4_analysis.ipynb        # Jupyter notebook with complete analysis
├── scripts/
│   └── accident_analysis.py        # Python script version
├── visualizations/
│   ├── hourly_patterns.png
│   ├── weather_analysis.png
│   ├── state_distribution.png
│   └── equipment_correlation.png
├── results/
│   └── analysis_report.md           # Detailed findings report
└── README.md
```

## 🚀 Getting Started

### Prerequisites
```bash
Python 3.8+
pip install pandas numpy matplotlib seaborn
```

### Installation & Usage
```bash
# Clone the repository
git clone https://github.com/yourusername/railway-accident-analysis.git
cd railway-accident-analysis

# Install dependencies
pip install -r requirements.txt

# Run the analysis
python scripts/accident_analysis.py
```

## 📊 Sample Results

Key statistics from the analysis:
- **Total Incidents Analyzed**: 10,000+
- **Peak Accident Hour**: [Hour] with [X]% of daily incidents
- **Highest Risk State**: [State] with [X] incidents per year
- **Weather Paradox**: 70% accidents during clear weather

## 🔮 Future Enhancements

- [ ] Machine Learning model for accident prediction
- [ ] Real-time data integration and dashboard
- [ ] Mobile application for safety alerts
- [ ] Advanced geospatial analysis with mapping APIs

## 🎓 Learning Outcomes

- Advanced data preprocessing and cleaning techniques
- Statistical analysis and pattern recognition
- Professional data visualization best practices
- Business insight generation from complex datasets
- Real-world problem-solving using data science

## 🤝 Acknowledgments

- **SkillCraft Technology** for providing the learning opportunity
- **Mentorship Team** for guidance throughout the project
- **Railway Safety Community** for domain expertise insights

---

**Note**: This project demonstrates practical application of data science techniques for transportation safety analysis, showcasing end-to-end analytical skills from data preprocessing to actionable business recommendations.
