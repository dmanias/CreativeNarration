# docker build -t creativenarration -f ./deployments/Dockerfile --target development .

ARG GO_VERSION=1.21
FROM golang:${GO_VERSION}-alpine AS development

WORKDIR /app
COPY ../ ./

RUN go mod download
CMD ["go", "run", "./app/main.go"]

# docker build -t creativenarration -f ./deployments/Dockerfile --target testing .
FROM development AS testing
RUN go test -v ./...

FROM development AS build
RUN CGO_ENABLED=0 GOOS=linux go build -a -installsuffix cgo -o creativenarration ./app/main.go

FROM gcr.io/distroless/cc-debian11@sha256:8aad707f96620ee89e27febef51b01c6ff244277a3560fcfcfbe68633ef09193 as production
COPY --from=build /app/creativenarration /bin/creativenarration
CMD ["/bin/creativenarration"]