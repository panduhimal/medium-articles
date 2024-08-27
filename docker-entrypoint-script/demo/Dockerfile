FROM python:3.12

# Set working directory
WORKDIR /app

# Install dependencies
RUN apt-get update && apt-get install -y netcat-openbsd

# Install Python dependencies
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

# Copy the Django app
COPY . .

# Copy the entrypoint script
COPY entrypoint.sh /entrypoint.sh
# Make the entrypoint script executable
RUN chmod +x /entrypoint.sh

# Set the entrypoint to the script
ENTRYPOINT ["/entrypoint.sh"]

# Default command to run the Django server
CMD ["python", "manage.py", "runserver", "0.0.0.0:8000"]