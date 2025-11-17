# Spark Lab - Big Data Processing with Apache Spark

## 🎯 Overview
This lab provides hands-on experience with Apache Spark for big data processing, including batch processing, streaming, and machine learning.

## 🏗️ Architecture
- **Spark Cluster**: Master + 2 Workers (distributed processing)
- **Kafka**: KRaft mode for streaming data ingestion
- **PostgreSQL**: Structured data storage
- **Redis**: Caching and real-time data
- **Jupyter Lab**: Interactive development environment

## 🚀 Quick Start

### Prerequisites
- Docker and Docker Compose
- Python 3.8+ (for local development)
- Git
- Conda environment (datalab)

### Setup
```bash
# Navigate to Spark lab
cd Spark_lab

# Run setup script
chmod +x setup_spark_lab.sh
./setup_spark_lab.sh

# Start the cluster
docker-compose up -d

# Wait for services to be ready (30-60 seconds)
sleep 30

# Test connectivity
python test_spark_connectivity.py

# Check cluster status
docker-compose ps
```

### Access Points
- **Spark Master UI**: http://localhost:8080
- **Jupyter Lab**: http://localhost:8888
- **PostgreSQL**: localhost:5432
- **Redis**: localhost:6379
- **Kafka**: localhost:9092

## 📚 Lab Structure

### Lab 1: Spark Batch Processing ✅
**File**: `notebooks/01_spark_batch_processing.ipynb`

**Topics Covered**:
- DataFrame operations (select, filter, groupBy, join)
- Aggregations and window functions
- Multi-table joins and data integration
- Performance optimization (caching, partitioning, broadcast joins)
- Data persistence and export (Parquet, JSON, CSV)

**Sample Datasets**:
- Sales transactions (1000 records)
- Customer demographics (8 customers)
- Product catalog (8 products)

**Exercises**:
1. Basic DataFrame Operations
2. Aggregations and Grouping
3. Joins and Data Integration
4. Performance Optimization
5. Data Persistence and Export

### Lab 2: Spark Streaming ✅
**File**: `notebooks/02_spark_streaming.ipynb`

**Topics Covered**:
- Structured Streaming basics
- Kafka integration with Spark
- Real-time aggregations
- Window functions and watermarking
- Stream-to-stream joins
- Performance monitoring

**Sample Datasets**:
- High-frequency stock data streams
- Real-time analytics and alerts

**Exercises**:
1. Basic Stream Processing
2. Real-time Aggregations
3. Window Functions and Watermarking
4. Real-time Alerts and Monitoring
5. Stream to Stream Joins
6. Performance Monitoring and Optimization

### Lab 3: Spark MLlib ✅
**File**: `notebooks/03_spark_ml.ipynb`

**Topics Covered**:
- Feature engineering with Spark ML
- Classification (Random Forest)
- ML pipeline creation
- Model evaluation metrics
- Customer segmentation

**Sample Datasets**:
- Customer classification (1000 records)
- Sales regression (800 records)
- Customer clustering (600 records)

**Exercises**:
1. Customer Classification (Random Forest)
2. Sales Regression (Linear Regression)
3. Customer Clustering (K-means)
4. Model Evaluation and Tuning
5. Feature Engineering Pipeline

## 🔧 Configuration

### Environment Variables
The lab uses the following configuration (see `.env` file):
```bash
# Spark Configuration
SPARK_MASTER_URL=spark://spark-master:7077
SPARK_APP_NAME=SparkLab

# Database Configuration
POSTGRES_HOST=postgres
POSTGRES_PORT=5432
POSTGRES_DB=spark_lab
POSTGRES_USER=spark_user
POSTGRES_PASSWORD=spark_password

# Kafka Configuration
KAFKA_BOOTSTRAP_SERVERS=kafka:29092
KAFKA_TOPIC_PREFIX=spark_lab

# Redis Configuration
REDIS_HOST=redis
REDIS_PORT=6379
```

### Spark Configuration
- **Master**: 1 core, 1GB RAM
- **Workers**: 2 cores, 2GB RAM each
- **Total Cluster**: 5 cores, 5GB RAM

## 📊 Sample Data Generation

### Batch Data
```python
# Generate sales data
python scripts/generate_sales_data.py

# Generate customer data
python scripts/generate_customer_data.py
```

### Streaming Data
```python
# Start IoT sensor simulator
python scripts/iot_sensor_simulator.py

# Start web click simulator
python scripts/web_click_simulator.py
```

## 🛠️ Development

### Local Development
```bash
# Install dependencies
pip install -r requirements.txt

# Connect to Spark cluster
export SPARK_MASTER_URL=spark://localhost:7077

# Run Python scripts
python code/batch_processing/sales_analysis.py
```

### Jupyter Development
1. Access Jupyter Lab at http://localhost:8888
2. Use the provided notebooks in `notebooks/` directory
3. Spark context is automatically configured

## 📈 Monitoring

### Spark UI
- **Master**: http://localhost:8080
- **Application**: http://localhost:4040 (when running)

### Kafka Monitoring
- **Topics**: Use Kafka CLI tools
- **Consumer Groups**: Monitor via Spark UI

### Database Monitoring
- **PostgreSQL**: Connect via psql or GUI tools
- **Redis**: Use redis-cli or GUI tools

## 🔍 Troubleshooting

### Common Issues

1. **Spark Master not accessible**
   ```bash
   docker-compose logs spark-master
   ```

2. **Kafka connection issues**
   ```bash
   docker-compose logs kafka
   ```

3. **Jupyter not connecting to Spark**
   - Check SPARK_MASTER_URL in Jupyter environment
   - Verify network connectivity

### Logs
```bash
# View all logs
docker-compose logs -f

# View specific service logs
docker-compose logs -f spark-master
docker-compose logs -f kafka
```

## 📝 Best Practices

### Performance
- Use appropriate partitioning strategies
- Cache frequently accessed DataFrames
- Optimize shuffle operations
- Use broadcast joins for small tables

### Development
- Use Jupyter notebooks for exploration
- Move to Python scripts for production
- Implement proper error handling
- Use logging for debugging

### Data Management
- Use Parquet format for storage
- Implement data validation
- Use schema evolution strategies
- Monitor data quality

## 🎓 Learning Objectives

After completing this lab, you will be able to:
- Process large datasets with Spark DataFrames
- Implement real-time data processing with Structured Streaming
- Build machine learning pipelines with Spark MLlib
- Optimize Spark applications for performance
- Integrate Spark with various data sources
- Monitor and debug Spark applications

## 📚 Additional Resources

- [Apache Spark Documentation](https://spark.apache.org/docs/latest/)
- [Spark SQL Guide](https://spark.apache.org/docs/latest/sql-programming-guide.html)
- [Structured Streaming Guide](https://spark.apache.org/docs/latest/structured-streaming-programming-guide.html)
- [MLlib Guide](https://spark.apache.org/docs/latest/ml-guide.html)

## 🤝 Contributing

Feel free to contribute improvements, additional exercises, or bug fixes to this lab.

## 📄 License

This lab is provided for educational purposes. Please refer to the individual component licenses for more details.
