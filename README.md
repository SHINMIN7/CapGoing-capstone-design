# Personalized Drip Coffee Recipe Generator

## Deploy
 URL : https://main--brewbuzzrecipe.netlify.app/

# 📚 STACKS 
___
## Environment
![Visual Studio Code](https://img.shields.io/badge/Visual%20Studio%20Code-0078d7.svg?style=for-the-badge&logo=visual-studio-code&logoColor=white) ![Git](https://img.shields.io/badge/git-%23F05033.svg?style=for-the-badge&logo=git&logoColor=white) ![GitHub](https://img.shields.io/badge/github-%23121011.svg?style=for-the-badge&logo=github&logoColor=white)

## Config
![NPM](https://img.shields.io/badge/NPM-%23CB3837.svg?style=for-the-badge&logo=npm&logoColor=white) 

## Development
![JavaScript](https://img.shields.io/badge/javascript-%23323330.svg?style=for-the-badge&logo=javascript&logoColor=%23F7DF1E) ![React](https://img.shields.io/badge/react-%2320232a.svg?style=for-the-badge&logo=react&logoColor=%2361DAFB) ![NodeJS](https://img.shields.io/badge/node.js-6DA55F?style=for-the-badge&logo=node.js&logoColor=white) ![Express.js](https://img.shields.io/badge/express.js-%23404d59.svg?style=for-the-badge&logo=express&logoColor=%2361DAFB) ![Bootstrap](https://img.shields.io/badge/bootstrap-%238511FA.svg?style=for-the-badge&logo=bootstrap&logoColor=white) ![Figma](https://img.shields.io/badge/figma-%23F24E1E.svg?style=for-the-badge&logo=figma&logoColor=white) ![Arduino](https://img.shields.io/badge/-Arduino-00979D?style=for-the-badge&logo=Arduino&logoColor=white)



# Database
  ![](https://img.shields.io/badge/AmazonRDS-527FFF?style=for-the-badge&logo=amazonrds&logoColor=white) ![MySQL](https://img.shields.io/badge/mysql-4479A1.svg?style=for-the-badge&logo=mysql&logoColor=white)



## Deployment
![EC2](https://img.shields.io/badge/ec2-FF9900.svg?style=for-the-badge&logo=amazonec2&logoColor=white) ![Nginx](https://img.shields.io/badge/nginx-%23009639.svg?style=for-the-badge&logo=nginx&logoColor=white) ![Netlify](https://img.shields.io/badge/netlify-%23000000.svg?style=for-the-badge&logo=netlify&logoColor=#00C7B7) 

### Project Purpose
The goal of this project is to create personalized drip coffee recipes that reflect individual preferences using generative AI. Drip coffee, brewed by pouring hot water over coffee grounds, exhibits varying flavors (cup notes) based on several extraction variables such as water temperature, extraction time, and quantity. For example, a coffee bean with green apple, lemon grass, and herb notes can have these flavors amplified or reduced depending on these variables.

Traditional cafe drip coffee recipes do not consider personal preferences and often provide only one recipe per coffee bean, failing to highlight each bean's unique characteristics. To address this, our project uses generative AI to create customized drip coffee recipes based on two user preferences, aiming to increase or decrease specific cup notes and control elements like strength and acidity. This personalized approach enhances user satisfaction and helps them brew coffee that suits their taste.

### Design Topic
The project involves creating modified drip coffee recipes using generative AI to reflect individual preferences and sending these recipes to an Arduino equipped with a weight sensor. The Arduino displays the recipe information on an LCD screen to guide users through the coffee extraction process.

### Problem Definition
- **Performance - Response Time:** Delays may occur in generating personalized drip coffee recipes using generative AI. The model's fine-tuning process to predict cup notes also introduces delays. Reducing latency between the generative AI model and the server is crucial.
- **Data - Input:** Accurate data collection is challenging. Coffee beans vary widely in variety, origin, processing method, and roasting stage, leading to limited data for predicting cup notes. Additionally, verifying the accuracy of existing cup note data is necessary.
- **Economics - Profit:** A new market needs to be developed to provide drip coffee recipes that reflect individual preferences. The current market offers standardized recipes requiring multiple trials to suit personal tastes. Our service aims to meet this demand.
- **Service - Scalability and Stability:** The current system only operates on our project's web platform and struggles to reflect diverse user preferences. Moreover, the Arduino scale has location limitations.
- **Service - Exception Handling:** The generative AI relies on ChatGPT, posing issues if ChatGPT encounters problems. The system also struggles with unexpected user input.

## Background

### Trends in Related Technologies
Generative AI is highly advanced, offering personalized recommendations in various fields like shopping and video platforms by analyzing user behavior and preferences. However, there are no applications in food that create new recipes reflecting user preferences. Existing coffee scales only display total extraction time and weight, lacking detailed step-by-step extraction information.

### Demand and Outlook for Related Technologies
As generative AI technology progresses, users will increasingly seek specialized services. With over 600 million Chat-GPT users worldwide and continuous advancements in generative AI, it will apply to new areas. The drip coffee market is growing annually, and the demand for personalized coffee recipes will rise, driven by the project's innovative approach.

## Requirements Analysis

### Functional Requirements
- **AI Requirements:**
  - Generate recipes reflecting user preferences.
  - Create recipes within a standard format.
  - Output recipes in a specified format.
  - Predict cup notes using other bean information when not available.
- **Web Requirements:**
  - Design a UI considering whether cup note information is available.
  - Users must register and log in to use the service.
  - Provide forms for inputting coffee bean information and preferences.
  - Display step-by-step recipe information on the web.
  - Send recipe information to AWS IoT.
  - Allow users to save generated recipes.
- **Arduino Requirements:**
  - Provide start/zero calibration functions.
  - Display extraction steps and total time.
  - Show step-by-step water quantity, bloom time, and extraction time.
  - Display total weight.
  - Receive messages from AWS IoT.

### Performance Specifications
- Recipes should be output in JSON format.
- Follow a standard recipe format.
- Parse responses from ChatGPT into object format.
- Transmit recipe data to AWS IoT using topic rules.
- Ensure secure API requests and responses using https.
- Scale recognizes weights up to 5kg with 0.1g precision.
- Show time in seconds on the LCD screen.
- Receive MQTT messages from AWS IoT.

## Constraints

### Operating Environment
The process of automatically sending recipe information to Arduino requires deploying the backend server on AWS EC2 with Nginx. The ESP32 Wi-Fi module supports only low-bandwidth environments (2.4GHz-2.5GHz).

### Development Environment
- **OS:** Windows 10
- **Design:** Figma
- **Deployment:** Netlify, AWS EC2, Nginx, Certbot
- **Database:** AWS RDS, MySQL
- **Languages:** React, Node.js, Express
- **Tools:** Vscode
- **Collaboration:** GitHub

### Economic Constraints
- Generative AI fine-tuning and API call costs.
- Purchase of Arduino and sensors.
- Domain name purchase cost.
- Server maintenance cost.

## Design

### Service Flow Chart
Users start at the main screen and must log in to use the recipe generation service. The user inputs coffee information and preferences, which are sent to ChatGPT for recipe generation. The generated recipe is then displayed step-by-step, with an option to save it or send it to the Arduino.

### Service Architecture
The architecture separates frontend and backend code management using GitHub. The frontend is deployed on Netlify, and the backend on AWS EC2. Secure HTTP communication is ensured using Certbot and Nginx. AWS RDS manages the database, and AWS IoT securely transmits data to the Arduino.

### Evaluation Criteria and Methods
The evaluation criteria include checking the existence of cup notes, generating appropriate recipes, verifying user login, sending recipe data to Arduino, and displaying step-by-step extraction information on the Arduino.

## Implementation

### Implementation Tools
- **Recipe Generation:** Chat GPT-4
- **Web Interface:** React
- **Web Server:** Node.js
- **Embedded Hardware:** ESP WROOM 32 Wi-Fi, HX711 scale, I2C LCD module
- **Development Editor:** Vscode
- **Version Control:** GitHub
- **Design Tools:** Figma

## Results

### AI
The generative AI creates appropriate drip coffee recipes based on user preferences, validated by expert comparison. Fine-tuned models accurately predict cup notes for beans without existing data.

### Web
The web interface allows users to input coffee information and preferences, generate personalized recipes, and view step-by-step instructions. Users can save recipes or send them to the Arduino.

### Arduino
The Arduino setup receives recipe data via MQTT from AWS IoT, guiding users through the extraction process with detailed step-by-step instructions displayed on the LCD.

## Conclusion

### Result Analysis
The project successfully automates the process of generating and following personalized drip coffee recipes, enhancing user satisfaction by reflecting individual preferences. Generative AI's potential is demonstrated through this innovative application.

### Future Development
Future improvements include continuous user feedback integration for fine-tuning individual AI models, enhancing hardware design for user-friendliness, and expanding the service to accommodate more preferences and environments.

### Expected Outcomes
The project is expected to increase user satisfaction by offering personalized drip coffee recipes, encouraging more people to enjoy high-quality coffee at home, and contributing to the growth of the drip coffee market.

## References
1. YM Coffee Brewing Extraction Variables: [YM커피 브루잉 추출변수 자료](https://community.unspecialty.com/column/c/9cf2913b-715d-4a73-b97c-067dbde898e5)
2. Kaggle Coffee_Data_CoffeeReview dataset: [Kaggle Coffee_Data_CoffeeReview dataset](https://www.kaggle.com/datasets/hanifalirsyad/coffee-scrap-coffeereview)
3. GPT Fine-tuning Official Documentation: [GPT Fine-tuning 공식문서](https://platform.openai.com/docs/guides/fine-tuning)
4. AWS IoT Core Official Documentation: [AWS IoT core 공식문서](https://docs.aws.amazon.com/ko_kr/iot/latest/developerguide/what-is-aws-iot.html)
5. AWS IoT and ESP32 Module Connection: [AIWS IoT와 ESP32 모듈 연결 공식문서](https://aws.amazon.com/ko/blogs/compute/building-an-aws-iot-core-device-using-aws-serverless-and-an-esp32/)
6. OpenAI API Quickstart: [OpenAI API 호출 공식문서](https://platform.openai.com/docs/quickstart?context=node)
7. Nginx Server Official Documentation: [Nginx 서버 공식문서](https://docs.nginx.com/nginx/admin-guide/web-server/)
