# 🌐  Code and Research Findings for KindaLike App Backend Recommendation Engine 🚀

[Presentation](https://www.canva.com/design/DAF2RCbKEes/XFvFeqfXlQxqYszve-LOfQ/view?utm_content=DAF2RCbKEes&utm_campaign=designshare&utm_medium=link&utm_source=viewer)

## Tech Stack
- **Front-end**: React Native
- **Front-end framework**: Expo
- **Back-end**: Node.js
- **Recommendation server backend**: Python
- **Middle-ware**: Express.js
- **Database**: MongoDB
- **Deployment**: Heroku

## How to Run the Project Locally

### Back-end
1. Clone the repository to your local machine [here](https://github.com/KindaLike2020/frontend).
2. Run `npm run dev`.
3. The backend will listen on `localhost:3000` or `process.env`.

### Front-end
1. Clone the repository to your local machine [here](https://github.com/KindaLike2020/frontend).
2. Run `npm install` to install all packages and dependencies.
3. Follow the instructions [here](https://docs.expo.dev/get-started/installation/) to install Expo CLI.
4. Run `npm start`.
5. The Expo interface will automatically pop up in your browser. You can review the front-end on an Android emulator or a physical device by following Expo instructions.

### Recommendation API
1. Clone the repository to your local machine (the repo is private, so ensure you log in with the GitHub account provided).
2. Run `python app.py`.
3. The recommendation server will listen on `localhost:8000` or `process.env`.

## How to Update the Project in Production Environment

### Front-end
- To publish on Expo and let users access the app through Expo: run `expo publish`. Documentation is [here](https://docs.expo.dev/workflow/publishing/).
- To build an APK: run `expo build:android`. Documentation is [here](https://docs.expo.dev/classic/building-standalone-apps/).

### Back-end
- The Heroku account is connected to GitHub. Simply push the new code to the GitHub backend repo, and Heroku will automatically rebuild the backend.

### Recommendation API
- The Heroku account is connected to GitHub. Simply push the new code to the GitHub recommendation repo, and Heroku will automatically rebuild the recommendation API.

## Features

### Signup/Login
- **Database**: User information is passed from front-end to back-end and saved in MongoDB.
- **Persistent Login**: Implemented persistent login. Login token is stored in `AsyncStorage`; every time users open the app, it looks for the login token in `AsyncStorage` first and directly navigates users to the post-login pages if the token is found.

### Password Reset
- When the user clicks “forgot password” and enters their email address, the server sends a 6-digit code to the email address. The function is implemented with Nodemailer. The code has a 30-minute expiration timer (adjustable in the backend). Once the user enters the code, they will be directed to enter a new password which is passed to the backend, encoded, and saved in the database. The old password is overwritten.

### ChatBot
- **Messaging Interface**: Implemented interface with Gifted Chat.
- **Natural Language Processing Platform**: Implemented text parsing/reading and response generation with Google DialogFlow.

### Filtering
- **Scrollable Interface**: Implemented scrollable interface with `react-native-scrollable-tab-view`.
- **Multiple Select Interface**: Implemented multiple select interface with `react-native-multiselect-view`.
- **Location Slider**: Implemented location slider interface with `react-native-multi-slider`.
- **Category Searchable Selection**: Implemented searchable selection for food categories with `react-native-sectioned-multi-select`.

### Recommendation
- **Animated Map View Interface**: Implemented map view with `react-native-maps`.
- **Recommendation Engine**: Built the recommendation engine on top of the open-source Python library `Surprise`.

### Restaurant Information
- **Service Provider**: Connected to Yelp API to search for a list of restaurants and detailed information of a specific restaurant.

### Review
- **Would Recommend Reviews**: Encoded “wouldn’t recommend” as `1`, “neutral” as `2`, and “would recommend” as `3`. All users’ review information is saved in the `reviews` collection on MongoDB.
- **Best of Breed Review**: Saved all users’ best of breed reviews in the `likes` collection on MongoDB.

### User Account
- **Profile Image**: Users can select profile images from mobile albums. The pictures are saved to Amazon S3.
- **Account Info Change**: Changed values are sent to MongoDB and overwrite the previous values.

## Code Files

### Front-end
- **assets**: All media resources used in the project.
- **src/api/yelp**: Yelp API.
- **src/api/server**: Backend server API.
- **src/api/recommend**: Recommend server API.
- **src/component**: Various UI components including `ButtonToBot`, `Categories_data.json`, `ChatCategories`, `ChatHour`, `ChatLocation`, `Price`, `cities`, `ConvertToResponse`, `EditAccountForm`, `ResultsDetail`, `ResultsList`, `TabList`.
- **src/hooks**: Custom hooks like `useBusinessInfo`, `useResults`, `useReviews`.
- **src/screens**: Various screens including `accountRestaurantDetailScreen`, `accountScreen`, `changePasswordScreen`, `chatFilterScreen`, `chatRecommendScreen`, `chatScreen`, `editAccountScreen`, `enterResetCodeScreen`, `enterResetEmailScreen`, `enterResetPasswordScreen`, `initialScreen`, `loginScreen`, `pictureScreen`, `registerScreen`, `restaurantDetailScreen`, `restaurantListScreen`, `reviewHistory`.

### Back-end Server
- **routes/accountRoutes**: `/account` (read account information of a user), `/account_edit` (edit account information).
- **routes/authRoutes**: `/signup` (sign up an account), `/signin` (sign in an account), `/password_reset_send_email` (send a code to reset password), `/signin_code` (verify the reset code).
- **routes/historyRoutes**: `/review_history` (add reviews to restaurants), `/like_history` (add “best of the kind”), `/remove_like` (remove “best of the kind”), `/view_like` (view “best of the kind” restaurants), `/view_review` (view reviewed restaurants).
- **routes/imageRoutes**: `/image_upload` (upload avatar), `/image_download` (get avatar download URL).
- **routes/pwdResetRoutes**: `/password_reset` (reset password within the Account), `/password_reset_no_old_pwd` (reset password when the user forgot their password).

### Recommendation Server
- **app.py**: `/recommend` (recommend a list of restaurant IDs).
- **recommend.py**: Business logic of the recommendation engine.

