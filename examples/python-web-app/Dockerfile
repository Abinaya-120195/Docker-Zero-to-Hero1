FROM ubuntu

WORKDIR /app

COPY requirements.txt /app
COPY devops /app

# Install required packages and create a virtual environment
RUN apt-get update && \
    apt-get install -y python3 python3-pip python3-venv && \
    python3 -m venv venv && \
    . venv/bin/activate && \
    pip install --upgrade pip && \
    pip install -r requirements.txt

# Activate the virtual environment
ENV VIRTUAL_ENV /app/venv
ENV PATH="/app/venv/bin:$PATH"

# Set entry point to use the virtual environment
ENTRYPOINT ["python3", "manage.py"]
CMD ["runserver", "0.0.0.0:8000"]
