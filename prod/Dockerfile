FROM python:3.11
ENV PYTHONBUFFERED=1
WORKDIR /app

RUN pip install --upgrade pip "poetry==1.8.3"
RUN poetry config virtualenvs.create false --local
COPY pyproject.toml poetry.lock ./
RUN poetry install
COPY mysite .

RUN python manage.py collectstatic --noinput


CMD ["gunicorn", "mysite.wsgi:application", "--bind", "0.0.0.0:8000"]
