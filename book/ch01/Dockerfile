FROM golang:1.17.3-alpine3.15

COPY ./main.go ./

RUN go build -o ./go-app ./main.go

USER gmaster

ENTRYPOINT [ "./go-app" ]
