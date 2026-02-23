FROM ubuntu:22.04

WORKDIR /app

# Install required packages
RUN apt-get update && \
    apt-get install -y python3 python3-pip && \
    apt-get install -y cron && \
    apt-get install -y mysql-client && \
    apt-get clean &&\
    rm -rf /var/lib/apt/lists/*


# Install dependencies
COPY app/requirements.txt ./
RUN pip3 install -r requirements.txt

# Copy application files 
COPY app/server.py /app/server.py


# Set entrypoint
EXPOSE 8000
ENTRYPOINT ["fastapi", "run", "server.py", "--host", "0.0.0.0", "--port", "8000"]