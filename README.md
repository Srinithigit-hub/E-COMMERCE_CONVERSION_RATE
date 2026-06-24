# E-COMMERCE_CONVERSION_RATE
A modern, full-stack e-commerce platform designed for a seamless shopping experience. Features secure user authentication, product catalog filtering, integrated payment processing, and a comprehensive admin dashboard.

🔗 View Live Site | 🖥️ Admin Dashboard

✨ Key Features:


●🔒 Secure Authentication: JWT-based user login, registration, and password recovery via OAuth.


●🔍 Advanced Search & Filter: Dynamic product filtering by category, price range, ratings, and real-time text search.


●🛒 Shopping Cart & Checkout: Persistent local-storage cart, real-time inventory checks, and single-page checkout.


●💳 Payment Integration: Secure sandbox payment processing integrated via Stripe / PayPal.


●📊 Admin Analytics Panel: Management suite for updating stock, tracking revenue metrics, and handling order fulfillment statuses.


●📱 Fully Responsive UI: Optimized layout for desktop, tablet, and mobile devices using CSS Grid and Flexbox.


🛠️ Tech Stack:


Layer:	Technologies Used


Frontend:	React.js, Tailwind CSS, Redux Toolkit (State Management)


Backend	:Node.js, Express.js


Database	:MongoDB (Mongoose ORM) / PostgreSQL


Payments	:Stripe API


Hosting	:Vercel (Frontend), Render / AWS (Backend)


⚙️ Getting Started:


Follow these steps to set up the project locally on your machine.

Prerequisites:


●Node.js (v18.x or higher)


●npm or yarn


●A free MongoDB Atlas account (or local MongoDB setup)


●A Stripe Developer Account (for API keys)


Clone the Repository:


git clone [https://github.com/your-username/your-repo-name.git](https://github.com/your-username/your-repo-name.git)
cd your-repo-name


Installation & Local Run:


You can run both client and server concurrently, or spin them up in separate terminals.

🗺️ API Endpoint Preview:


Method	 Endpoint 	Description	Auth Required


GET	/api/products	Fetch all products with pagination	No


GET	/api/products/:id	Fetch details for a specific item	No


POST	/api/cart	Sync local cart to user profile	Yes


POST	/api/orders	Create a new order after checkout	Yes


GET	/api/admin/analytics	Fetch sales stats (Admin only)	Yes


AUTHOR : SRINITHI

CODE:

 1. Category Distribution


plt.figure(figsize=(10, 6))
sns.countplot(data=df, x='Category', palette='viridis', order=df['Category'].value_counts().index)
plt.title('Product Category Distribution')
plt.xlabel('Category')
plt.ylabel('Count')
plt.xticks(rotation=45)

plt.show()

# 2. Payment Method Distribution
plt.figure(figsize=(8, 5))
sns.countplot(data=df, x='Payment_Method', palette='pastel', order=df['Payment_Method'].value_counts().index)


plt.title('Payment Method Distribution')
plt.xlabel('Payment Method')
plt.ylabel('Count')

plt.show()

 First, let's encode categorical variables
df_encoded = df.copy()

# Encode 'Payment_Method' using One-Hot Encoding
df_encoded = pd.get_dummies(df_encoded, columns=['Payment_Method'], drop_first=True)

# Prepare features (X) and target (y)
X = df_encoded[['Price (Rs.)', 'Discount (%)'] + [col for col in df_encoded.columns if 'Payment_Method' in col]]

y = df_encoded['Final_Price(Rs.)']

# Train-Test Split
from sklearn.model_selection import train_test_split

X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

# Train a Linear Regression Model
from sklearn.linear_model import LinearRegression
lr_model = LinearRegression()
lr_model.fit(X_train, y_train)

# Predict on Test Set
y_pred = lr_model.predict(X_test)

# Evaluate Model
from sklearn.metrics import mean_squared_error, r2_score
mse = mean_squared_error(y_test, y_pred)
r2 = r2_score(y_test, y_pred)

print(f'Mean Squared Error: {mse}')
print(f'R2 Score: {r2}')

from sklearn.cluster import KMeans
from sklearn.preprocessing import StandardScaler

# Select features for clustering
clustering_features = df[['Price (Rs.)', 'Discount (%)', 'Final_Price(Rs.)']]

# Standardizing the features
scaler = StandardScaler()
clustering_features_scaled = scaler.fit_transform(clustering_features)

# Applying K-Means Clustering
kmeans = KMeans(n_clusters=4, random_state=42)
df['Cluster'] = kmeans.fit_predict(clustering_features_scaled)

# Plot the clusters
plt.figure(figsize=(10, 6))
sns.scatterplot(x='Price (Rs.)', y='Discount (%)', hue='Cluster', data=df, palette='Set1', s=100)
plt.title('Clustering Users Based on Purchase Behavior')
plt.xlabel('Price (Rs.)')
plt.ylabel('Discount (%)')
plt.legend(title='Cluster')
plt.show()