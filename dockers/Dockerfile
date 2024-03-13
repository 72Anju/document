# Use sphinxdoc/sphinx as the base image
FROM sphinxdoc/sphinx


# Install git and any other dependencies
RUN apt-get update && apt-get install -y git \
    && pip install sphinx_rtd_theme

# Set the working directory in the container
WORKDIR /docs

# Clone your GitHub repository
# Replace the URL with your repository URL
RUN git clone https://github.com/72Anju/document.git .

# Copy the startup script into the container and make it executable
COPY entrypoint.sh /entrypoint.sh
RUN chmod +x /entrypoint.sh

# When the container starts, run the startup script
CMD ["/entrypoint.sh"]


#docker build -t your-image-name .
#docker run -p 8000:8000 your-image-name