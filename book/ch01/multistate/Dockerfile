FROM golang:1.17.3-alpine3.15 as builder

WORKDIR /home/gmaster

COPY ./main.go ./

RUN go build -o ./go-app ./main.go


FROM alpine:3.15

COPY --from=builder /home/gmaster/go-app .

EXPOSE 8080

USER gmaster

ENTRYPOINT [ "./go-app" ]
