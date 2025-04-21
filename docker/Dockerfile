FROM python:3.10
ENV PYTHONUNBUFFERED 1

WORKDIR /pierre-decheck

# Install required python packages
COPY requirements.txt /pierre-decheck/
RUN pip install -r requirements.txt

# DONT run as ROOT
RUN useradd -ms /bin/bash app
RUN chown -R app:app /pierre-decheck
USER app
COPY --chown=app:app . /pierre-decheck/

CMD gunicorn -b 0.0.0.0:$PORT wsgi:app
