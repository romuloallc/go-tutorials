# Build Stage
FROM golang:latest AS build-stage

WORKDIR /app

COPY go.* ./ 

RUN go mod tidy

COPY . .

RUN go build -o hello ./hello

# Final Stage
FROM gcr.io/distroless/static-debian12

WORKDIR /app
COPY --from=build-stage /app/hello .

CMD [ "./hello" ]
