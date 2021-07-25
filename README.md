# heroku-wake-up

A NextJS frontend that sends wake up calls to all heroku rest endpoints specified in ENV once an hour to prevent free tier sleep mode.

## What is the project for?

Since Heroku puts hosted backend applications to sleep after several hours of being inactive and the non-sleeping-tier costs 7 USD per application per month I searched for ways to host backend servers without sleeping.

I came to the conclusion that it might be the easiest solution to have a cronjob that pings the heroku backend servers every hour so they never go to sleep but also don't generate too much used server time and run out of the free tier.

While there are some free cronjob tools on the web I wanted to be in full control and host the project myself. The problem in general here is that hosting a backend for free is something not found easily on the web and cronjobs are usually parts of servers/backends. So to have a server that keeps all other backends on heroku awake you would need to have another backend online that does not go asleep.

During my research I found https://github.com/baulml/nextjs-cron which uses github actions as cronjob trigger to call to a deployed serverless Next.js function of your liking. Next.js is a frontend technology which can be hosted easily and for free at many services and within Next.js is a tiny node backend that is converted by Vercel.com to serverless functions. So you can access backend functions without having to run a backend server. Thus it is possible to have a github actions cronjob that calls the Vercel.com Next.js serverless functions once an hour that then calls all your heroku backends and keeps them awake.

## Getting Started

First, run the development server:

```bash
npm run dev
# or
yarn dev
```

Open [http://localhost:3000](http://localhost:3000) with your browser to see the result.

You can start editing the page by modifying `pages/index.js`. The page auto-updates as you edit the file.

[API routes](https://nextjs.org/docs/api-routes/introduction) can be accessed on [http://localhost:3000/api/hello](http://localhost:3000/api/hello). This endpoint can be edited in `pages/api/hello.js`.

The `pages/api` directory is mapped to `/api/*`. Files in this directory are treated as [API routes](https://nextjs.org/docs/api-routes/introduction) instead of React pages.

## Learn More

To learn more about Next.js, take a look at the following resources:

- [Next.js Documentation](https://nextjs.org/docs) - learn about Next.js features and API.
- [Learn Next.js](https://nextjs.org/learn) - an interactive Next.js tutorial.

You can check out [the Next.js GitHub repository](https://github.com/vercel/next.js/) - your feedback and contributions are welcome!

## Deploy on Vercel

The easiest way to deploy your Next.js app is to use the [Vercel Platform](https://vercel.com/new?utm_medium=default-template&filter=next.js&utm_source=create-next-app&utm_campaign=create-next-app-readme) from the creators of Next.js.

Check out our [Next.js deployment documentation](https://nextjs.org/docs/deployment) for more details.
