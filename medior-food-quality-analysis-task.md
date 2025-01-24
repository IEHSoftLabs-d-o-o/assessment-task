
# Food Quality Analysis Task

This task simulates a real-world challenge in the food industry and provides an opportunity to showcase your technical skills.


## **System Description**
1. **QualityManager**:
   - API service for submitting food batch data and initiating analyses.
   - Handles user requests and sends analysis tasks.

2. **AnalysisEngine**:
   - Processes data and simulates food quality analysis.
   - Communicates with QualityManager.

## **Environment**
1. **Technologies**:
   - Backend: C# .NET 8+ for services.
   - Database: PostgreSQL or SQL Server (candidate chooses one).
   - Message broker: RabbitMQ or Azure Service Bus (candidate chooses one).
2. **Containers**:
   - Use Docker and docker-compose to run the application.


## **Workflow**
1. **QualityManager**:
   - Provides an endpoint to process food batch data: `/api/food/process`.
   - Accepts food name, serial number, and type of analysis (e.g., microbiological analysis).
   - Validates input and stores the data in the database.
   - Sends a message to **AnalysisEngine** via a message broker with analysis details.

2. **AnalysisEngine**:
   - Receives the message and simulates analysis execution (e.g., sleeps for 2 seconds instead of real processing).
   - Generates a result (random textual output) and sends it back to **QualityManager** via the message broker.
   - Stores the result in its database.

3. **QualityManager**:
   - Updates the processing status in its database.
   - Provides a `/status/{serial_number}` endpoint for users to check the processing status and the analysis result (e.g., "Processing complete: Microorganisms are within limits").


## **Notes**
1. The candidate should:
   - Explain their choice of technologies (e.g., why PostgreSQL or RabbitMQ).
   - Include one example **unit test** (e.g., validating input in QualityManager) and one **integration test** (e.g., testing communication between QualityManager and AnalysisEngine via the message broker).
   - Create a docker-compose file to run the application (database, services, and message broker).

2. Excluded complexity:
   - No dynamic containers or gRPC communication, to keep the task simple for a medior-level developer.

---

Good luck! We look forward to your solution.
