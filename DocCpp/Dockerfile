FROM gcc:12
RUN apt-get update && apt-get install -y  build-essential cmake gdb valgrind linux-perf
COPY . /app
WORKDIR /app
EXPOSE 8080
CMD ["./microservicio"]
