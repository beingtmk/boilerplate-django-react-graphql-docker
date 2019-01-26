# Pull base image
FROM python:3.7-slim

# Set environment varibles
ENV PYTHONDONTWRITEBYTECODE 1
ENV PYTHONUNBUFFERED 1

# Set work directory
WORKDIR /code

# Requirements have to be pulled and installed here, otherwise caching won't work
COPY ./requirements /code/requirements
RUN pip install -r /code/requirements/local.txt

COPY ./docker/development/scripts/start.sh /start.sh
COPY ./docker/development/scripts/entrypoint.sh /entrypoint.sh

# Copy project
COPY . /code/

RUN sed -i 's/\r//' /entrypoint.sh \
  && sed -i 's/\r//' /start.sh \
  && chmod +x /entrypoint.sh \
  && chmod +x /start.sh

ENTRYPOINT ["/entrypoint.sh"]

EXPOSE 8000
