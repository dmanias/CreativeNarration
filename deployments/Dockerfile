# Use the official Golang image to create a build artifact.
# This is the compilation stage, where we build our application.
FROM golang:1.21 AS builder

# Set the Current Working Directory inside the container
WORKDIR /app

# Assuming the go.mod and go.sum files are at the root of creative_narration
# Adjust the COPY paths to reflect the Dockerfile's location in deployments folder
COPY ../go.mod ../go.sum ./
# Ensure all dependencies are fetched.
RUN go mod download

# Copy the source code and vendor directories into the container
COPY ../app ./app
COPY ../vendor ./vendor

# Build the Go app for a linux target
# The path here assumes main.go is directly inside the app folder
RUN CGO_ENABLED=0 GOOS=linux go build -a -installsuffix cgo -o main ./app/main.go

# Use a Docker multi-stage build to create a lean production image.
# Start from the alpine image to have a small footprint.
FROM alpine:3.19

# Update certificates and add non-root user for security purposes
RUN apk --no-cache add ca-certificates && \
    adduser -D user

# Set the Current Working Directory to /home/user
WORKDIR /home/user

# Copy the Pre-built binary file from the previous stage.
COPY --from=builder /app/main .

# Use the non-root user to run our application
USER user

# Command to run the executable
CMD ["./main"]
