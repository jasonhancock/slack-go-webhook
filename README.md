# slack-go-webhook

[![Go Reference](https://pkg.go.dev/badge/github.com/jasonhancock/slack-go-webhook.svg)](https://pkg.go.dev/github.com/jasonhancock/slack-go-webhook)

Go library to send messages to Slack via Incoming Webhooks.

This is a fork of [github.com/ashwanthkumar/slack-go-webhook](github.com/ashwanthkumar/slack-go-webhook)

## Usage

```go
package main

import (
	"fmt"
	"github.com/jasonhancock/slack-go-webhook"
)

func main() {
	webhookUrl := "https://hooks.slack.com/services/foo/bar/baz"

	attachment1 := slack.Attachment{}
	attachment1.AddField(slack.Field{Title: "Author", Value: "Ashwanth Kumar"}).AddField(slack.Field{Title: "Status", Value: "Completed"})
	attachment1.AddAction(slack.Action{Type: "button", Text: "Book flights 🛫", Url: "https://flights.example.com/book/r123456", Style: "primary"})
	attachment1.AddAction(slack.Action{Type: "button", Text: "Cancel", Url: "https://flights.example.com/abandon/r123456", Style: "danger"})
	payload := slack.Payload{
		Text:        "Hello from <https://github.com/jasonhancock/slack-go-webhook|slack-go-webhook>, a Go-Lang library to send slack webhook messages.\n<https://golangschool.com/wp-content/uploads/golang-teach.jpg|golang-img>",
		Username:    "robot",
		Channel:     "#general",
		IconEmoji:   ":monkey_face:",
		Attachments: []slack.Attachment{attachment1},
	}
	err := slack.Send(webhookUrl, "", payload)
	if len(err) > 0 {
		fmt.Printf("error: %s\n", err)
	}
}
```

## License

Licensed under the Apache License, Version 2.0: http://www.apache.org/licenses/LICENSE-2.0
