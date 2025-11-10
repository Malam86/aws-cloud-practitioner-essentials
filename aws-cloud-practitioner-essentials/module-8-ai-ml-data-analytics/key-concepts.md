# AI/ML & Data Analytics Key Concepts

## Artificial Intelligence (AI) vs Machine Learning (ML)

### Artificial Intelligence (AI)
- **Broad Concept**: Machines performing tasks that typically require human intelligence
- **Goal**: Create systems that can reason, learn, and act intelligently
- **Examples**: Speech recognition, decision-making, visual perception
- **AWS Approach**: Pre-trained AI services for common use cases

### Machine Learning (ML)
- **Subset of AI**: Systems that learn and improve from experience without explicit programming
- **Core Idea**: Algorithms learn patterns from data to make predictions or decisions
- **Training Process**: Feed data → Algorithm learns patterns → Make predictions on new data
- **AWS Service**: Amazon SageMaker for building custom ML models

## Types of Machine Learning

### Supervised Learning
- **Labeled Data**: Training data includes both input and desired output
- **Goal**: Learn mapping from inputs to outputs
- **Examples**:
  - **Classification**: Spam detection (spam/not spam)
  - **Regression**: Price prediction (continuous values)
- **AWS Use**: Fraud detection, demand forecasting

### Unsupervised Learning
- **Unlabeled Data**: Training data has no predefined labels
- **Goal**: Discover hidden patterns or groupings in data
- **Examples**:
  - **Clustering**: Customer segmentation
  - **Anomaly Detection**: Identifying unusual patterns
- **AWS Use**: Customer behavior analysis, network security

### Reinforcement Learning
- **Learning by Interaction**: Agent learns through trial and error
- **Reward System**: Receives rewards or penalties for actions
- **Examples**: Game playing, robotics, recommendation systems
- **AWS Use**: Personalization, autonomous systems

## Data Processing Concepts

### ETL (Extract, Transform, Load)
- **Extract**: Get data from source systems
- **Transform**: Clean, enrich, and reformat data
- **Load**: Load transformed data into target system
- **AWS Service**: AWS Glue for serverless ETL

### ELT (Extract, Load, Transform)
- **Modern Approach**: Load raw data first, then transform
- **Benefits**: Faster loading, more flexible transformations
- **Use Case**: Data lakes where schema is defined on read
- **AWS Service**: Amazon Redshift, Amazon Athena

## Data Storage Concepts

### Data Warehouses
- **Structured Data**: Organized in tables with predefined schema
- **Purpose**: Business intelligence and analytics
- **Optimized For**: Complex queries and aggregations
- **AWS Service**: Amazon Redshift

### Data Lakes
- **All Data Types**: Structured, semi-structured, unstructured
- **Schema-on-Read**: Define structure when reading data, not when storing
- **Cost-Effective**: Store vast amounts of raw data
- **AWS Service**: Amazon S3 as data lake storage

### Data Marts
- **Subset of Data**: Department-specific or use-case specific
- **Focused Scope**: Marketing, sales, finance data marts
- **Faster Access**: Pre-aggregated and optimized for specific queries

## Analytics Maturity Model

### Descriptive Analytics
- **What Happened?**: Historical data analysis
- **Examples**: Reports, dashboards, KPIs
- **AWS Service**: Amazon QuickSight

### Diagnostic Analytics
- **Why Did It Happen?**: Root cause analysis
- **Examples**: Drill-down reports, correlation analysis
- **AWS Service**: Amazon Athena with SQL queries

### Predictive Analytics
- **What Will Happen?**: Forecasting future outcomes
- **Examples**: Demand forecasting, customer churn prediction
- **AWS Service**: Amazon Forecast, Amazon SageMaker

### Prescriptive Analytics
- **What Should We Do?**: Recommend actions
- **Examples**: Optimization, recommendation engines
- **AWS Service**: Amazon Personalize

## Natural Language Processing (NLP)

### Text Analysis
- **Sentiment Analysis**: Determine positive/negative/neutral sentiment
- **Entity Recognition**: Identify people, places, organizations
- **Key Phrase Extraction**: Identify important phrases and topics
- **AWS Service**: Amazon Comprehend

### Language Understanding
- **Language Detection**: Identify document language
- **Syntax Analysis**: Parse sentence structure and parts of speech
- **Semantic Analysis**: Understand meaning and context
- **AWS Service**: Amazon Comprehend

## Computer Vision

### Image Analysis
- **Object Detection**: Identify and locate objects in images
- **Scene Understanding**: Recognize settings and environments
- **Content Moderation**: Detect inappropriate content
- **AWS Service**: Amazon Rekognition

### Facial Analysis
- **Face Detection**: Identify faces in images and videos
- **Facial Analysis**: Detect attributes (age range, emotions, gender)
- **Face Comparison**: Measure similarity between faces
- **AWS Service**: Amazon Rekognition

## Business Intelligence (BI)

### Self-Service BI
- **User Empowerment**: Business users create their own reports
- **Drag-and-Drop Interface**: No technical skills required
- **Interactive Dashboards**: Real-time data exploration
- **AWS Service**: Amazon QuickSight

### Traditional BI
- **IT-Centric**: IT department creates and manages reports
- **Scheduled Reports**: Pre-defined, static reports
- **Complex Implementation**: Longer setup and deployment
- **Comparison**: QuickSight enables self-service vs traditional BI

## Machine Learning Workflow

### Data Preparation
- **Data Collection**: Gather relevant data from multiple sources
- **Data Cleaning**: Handle missing values, remove outliers
- **Feature Engineering**: Create meaningful input variables
- **AWS Service**: AWS Glue, SageMaker Data Wrangler

### Model Training
- **Algorithm Selection**: Choose appropriate ML algorithm
- **Hyperparameter Tuning**: Optimize model parameters
- **Cross-Validation**: Validate model performance
- **AWS Service**: Amazon SageMaker

### Model Deployment
- **Endpoint Creation**: Deploy model as API endpoint
- **Auto Scaling**: Handle varying inference workloads
- **Monitoring**: Track model performance and drift
- **AWS Service**: SageMaker Endpoints

### Model Monitoring
- **Performance Tracking**: Monitor accuracy and metrics
- **Data Drift Detection**: Identify when input data patterns change
- **Concept Drift**: Detect when relationships between inputs and outputs change
- **AWS Service**: SageMaker Model Monitor

## Big Data Processing

### Batch Processing
- **Scheduled Jobs**: Process large volumes of data at intervals
- **Use Cases**: Daily reports, monthly analytics
- **High Latency**: Results available after processing completes
- **AWS Service**: Amazon EMR, AWS Glue

### Stream Processing
- **Real-time**: Process data as it arrives
- **Use Cases**: Fraud detection, IoT data, clickstream analysis
- **Low Latency**: Immediate processing and results
- **AWS Service**: Amazon Kinesis

### Lambda Architecture
- **Hybrid Approach**: Combine batch and stream processing
- **Batch Layer**: Handles comprehensive historical data
- **Speed Layer**: Handles real-time streaming data
- **Serving Layer**: Merges results from both layers

## Serverless Analytics

### Benefits
- **No Infrastructure Management**: AWS handles servers and scaling
- **Pay-per-Use**: Only pay for actual compute time
- **Automatic Scaling**: Handle variable workloads seamlessly
- **Faster Time-to-Market**: Focus on code, not infrastructure

### AWS Serverless Analytics Services
- **Data Processing**: AWS Glue, AWS Lambda
- **Query Services**: Amazon Athena
- **Orchestration**: AWS Step Functions
- **Real-time**: Amazon Kinesis Data Analytics
