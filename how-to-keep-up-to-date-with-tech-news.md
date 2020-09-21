#How to keep up to date with tech news

As technology evolves at a rapid pace, as engineers, we need to keep ourselves up to date with it to stay relevant.

For myself, I find [Hacker News](https://news.ycombinator.com/), one of the most popular newsletter for technology to be a good source.

**How to automate the delivery of newsletter**

As I was learning Golang at that time, I decide to create a simple Go client that will run cron tasks that sends me newsletter. This automation can save a lot of time since you will get the stories delivered to you rather than have to check the website multiple times a day/week.

**Building the client**

Github repo: https://github.com/dan-l/hn-newsletter


To get the stories from HackerNews, we can query from the [Firebase Hacker News API](https://hacker-news.firebaseio.com/). Once we get the stories in JSON format, we can post process that into a formatted HTML string which represents the body of the email for the newsletter we will be sending out.

We want to make sure our email schedule and email recipient address is configurable, so we will create a config JSON file. We will then read that in to determine when we should be sending out this newsletter. Since the server will be in UTC time, make sure to specify the timezone you desire for your email schedule.

Once we know the email schedule, we can use [GoCron](https://github.com/jasonlvhit/gocron) which makes scheduling cron task in Go simple. Finally, we will send out our newsletter that we can build previously using the mail client [Mailgun](https://documentation.mailgun.com/quickstart.html).

**Deploying the client**

Finally we have a client that we can deploy so that it will actually send us the newsletter at the configured interval that we have tell it to. [In a few simple steps](https://github.com/dan-l/hn-newsletter#deployment-with-heroku), you will have your newsletter client up and running and ready to receive your newsletter!