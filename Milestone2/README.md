# FranchiseOps AI – Milestone 2
FranchiseOps AI is an intelligent web application developed using Python and Streamlit to help franchise businesses manage and analyze their operations. The application combines Artificial Intelligence (AI), Machine Learning (ML), and secure authentication to provide business insights, user management, and decision support.

The system is designed with multiple AI agents, analytics dashboards, weather integration, and administrative tools. It demonstrates the practical implementation of authentication, clustering algorithms, predictive models, and AI-powered assistance in a single application.

# Objectives

The main objectives of this project are:

- Develop a secure authentication system.
- Provide AI-based assistance using an AI Copilot.
- Display real-time weather information.
- Classify franchise outlets using the K-Means clustering algorithm.
- Predict business insights using Machine Learning models.
- Allow administrators to manage users.
- Display model performance through an ML Model Card.
- Demonstrate end-to-end deployment using Streamlit.
# Features

## 1. User Authentication

The application provides a secure authentication system.

Features include:

- User Registration
- User Login
- Forgot Password
- OTP Verification
- JWT Session Authentication
- Password Validation
- Email Validation
- Account Lock after multiple failed attempts
- Unlock User by Admin

## 2. AI Copilot

The AI Copilot allows users to ask business-related questions.

Example:
- Sales analysis
- Revenue suggestions
- Inventory recommendations
- Business guidance

The Copilot displays both the user prompt and the generated AI response.

## 3. Weather Demo

The Weather Demo allows users to enter a city name and retrieve weather information.

Displayed information includes:

- City Name
- Temperature
- Weather Condition
- Humidity
- Wind Speed

Example:

City: Hyderabad

Temperature: 30°C

Condition: Cloudy

Humidity: 65%

Wind Speed: 10 km/h

## 4. Agent 1 – Workforce Attrition

Agent 1 predicts employee attrition using Machine Learning.

It helps businesses identify employees who may leave the organization.

Displayed Metrics:

- Accuracy
- Precision
- Recall
- F1 Score
- ROC-AUC

## 5. Agent 2 – Revenue Simulation

Agent 2 predicts revenue and performs outlet analysis.

It provides:

- Revenue prediction
- Sales analysis
- Outlet performance

Displayed Metrics:

- R² Score
- MAE
- RMSE

## 6. Agent 3 – Inventory Demand

Agent 3 predicts inventory demand.

Benefits:

- Prevent stock shortages
- Reduce overstock
- Improve inventory planning

Displayed Metrics:

- R² Score
- MAE
- RMSE

# K-Means Outlet Tier Analysis

The application uses the K-Means clustering algorithm to classify outlets into four performance tiers.

The tiers are:

Tier 1 – Excellent Performing Outlets

Tier 2 – Good Performing Outlets

Tier 3 – Average Performing Outlets

Tier 4 – Low Performing Outlets

The clustering visualization helps franchise managers identify the best and weakest outlets.

# Admin Panel

The Admin Panel provides complete user management.

Features include:

- Add User
- Delete User
- Unlock User
- View Users
- ML Model Card

Only administrators can access these features.

# ML Model Card

The ML Model Card displays the performance of all Machine Learning models used in the project.

It includes:

Agent 1 Metrics

- Accuracy
- Precision
- Recall
- F1 Score
- ROC-AUC

Agent 2 Metrics

- R² Score
- MAE
- RMSE

Agent 3 Metrics

- R² Score
- MAE
- RMSE

K-Means Information

- Number of Clusters
- Tier Distribution
- Clustering Summary

# Technologies Used

Programming Language

- Python

Frontend

- Streamlit

Machine Learning

- Scikit-Learn

Data Processing

- Pandas
- NumPy

Authentication

- JWT
- Gmail SMTP

Deployment

- Google Colab
- Pyngrok

Version Control

- Git
- GitHub

# Folder Structure

Milestone2/

├── app.py

├── requirements.txt

├── README.md

├── screenshots/

│ ├── home_page.png

│ ├── ai_copilot.png

│ ├── weather_demo.png

│ ├── outlet_tiers.png

│ ├── ml_model_card.png

│ ├── admin_actions.png

│ └── lockout_message.png

---

# Screenshots

## Home Page
Displays the main dashboard after successful login.

<img width="944" height="428" alt="Home page" src="https://github.com/user-attachments/assets/eab48f87-60ec-4d2f-a3f9-bd61337cbcd9" />

---

## AI Copilot
Shows the prompt entered by the user and the AI-generated response.
<img width="943" height="423" alt="AI Copilot" src="https://github.com/user-attachments/assets/64bdf07d-2eeb-4b98-b87f-308052fa32f8" />


## Weather Demo
Shows the city entered and its weather details.
<img width="932" height="421" alt="Weather Demo" src="https://github.com/user-attachments/assets/0523ef25-6a51-4782-9426-5bf92a325a03" />


## Outlet Tiers
Displays the K-Means clustering chart with four outlet tiers.
<img width="932" height="383" alt="Outlet Tiers Page" src="https://github.com/user-attachments/assets/c811151e-ba89-4363-ab98-0723d5390123" />


## Admin User Management
Shows Add User, Delete User, and Unlock User features.
<img width="245" height="448" alt="Admin Panel(3 agents&#39;s metrics)" src="https://github.com/user-attachments/assets/e227baee-c48d-4d7a-bb46-1cf24f04d8b7" />

## Account Lock / OTP Cooldown
Displays account lock or OTP cooldown functionality.
<img width="952" height="437" alt="otp" src="https://github.com/user-attachments/assets/8e2c0588-695b-4b9c-b17c-d34b29cb9fd5" />


# Future Enhancements
- Mobile application support
- Cloud database integration
- Advanced AI chatbot
- Predictive analytics dashboard
- Sales forecasting improvements
- Multi-language support
- Email notifications
- PDF report generation
- Interactive analytics dashboard

# Conclusion

FranchiseOps AI is a complete AI-powered franchise management system that integrates secure authentication, machine learning, AI assistance, weather services, outlet performance analysis, and user management into a single application. The project demonstrates practical implementation of AI, Machine Learning, and Streamlit while providing useful business insights through an interactive dashboard.


