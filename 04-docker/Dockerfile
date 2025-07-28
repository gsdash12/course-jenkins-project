FROM python:3.12-slim as builder
WORKDIR /application
COPY requirements.txt .
RUN pip install --prefix=/install -r requirements.txt
COPY . /application

FROM gcr.io/distroless/python3
WORKDIR /app
COPY --from=builder /install /usr/local
COPY --from=builder /application /app/
ENTRYPOINT [ "python3" ]
EXPOSE 5000
CMD [ "app.py" ]
