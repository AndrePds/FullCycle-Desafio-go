FROM golang:1.19 AS build

WORKDIR /app

# pre-copy/cache go.mod for pre-downloading dependencies and only redownloading them in subsequent builds if they change
COPY go.mod ./
#RUN go mod download && go mod verify
COPY hello.go ./

RUN go build -o /rocks

FROM scratch

WORKDIR /

COPY --from=build /rocks /rocks

CMD [ "/rocks" ]