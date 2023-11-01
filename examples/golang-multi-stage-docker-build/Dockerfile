######################################################################################
# BASE IMAGE

# Base image section is to build with all dependencies, this will have high size of image.
#########################################################################################

FROM ubuntu AS build

RUN apt-get update && apt-get install -y golang-go

ENV GO111MODULE=off

COPY . .

RUN CGO_ENABLED=0 go build -o /app .

###############################################################################
# HERE STARTS THE MAGIC OF MULTI STAGE BUILD

# This section uses distroless images which makes the image size very less
###########################################################################

# Distorless image ( scratch is for go lang, to you python or java use those distroless images)

FROM scratch  

# Copy the compiled binary from the build stage
COPY --from=build /app /app

# Set the entrypoint for the container to run the binary
ENTRYPOINT ["/app"]

