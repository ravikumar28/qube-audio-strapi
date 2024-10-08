# 🚀 Getting started with Strapi

Strapi comes with a full featured [Command Line Interface](https://docs.strapi.io/dev-docs/cli) (CLI) which lets you scaffold and manage your project in seconds.

### `develop`

Start your Strapi application with autoReload enabled. [Learn more](https://docs.strapi.io/dev-docs/cli#strapi-develop)

```
npm run develop
# or
yarn develop
```

### `start`

Start your Strapi application with autoReload disabled. [Learn more](https://docs.strapi.io/dev-docs/cli#strapi-start)

```
npm run start
# or
yarn start
```

### `build`

Build your admin panel. [Learn more](https://docs.strapi.io/dev-docs/cli#strapi-build)

```
npm run build
# or
yarn build
```

## ⚙️ Deployment
 
If you're developing on the server, make sure to stop the PM2 process before running the app in development mode:

```
pm2 stop <appname>
npm run develop
pm2 start <appname>
```

### `Production`

#### Production

##### Managing the Application with PM2

PM2 is used to manage the application in a production environment.

Start All Applications:
```
pm2 start all
```

Stop All Applications:
```
pm2 stop all
```

Restart All Applications:
```
pm2 restart all
```

Restart a Specific Application:
```
pm2 restart <appname>
```

to check the log:
```
pm2 log <appname>
```

#### Known Issue with Location Plugin

There's a known issue with the location plugin in Strapi that may affect location data. If you encounter problems related to location data, you can resolve it by running the following SQL query:

```sql
UPDATE theatres
SET theatre_location = jsonb_build_object(
    'lat', (theatre_location->>'lat')::float,
    'lng', (theatre_location->>'lng')::float
)
WHERE theatre_location IS NOT NULL;
```

This query converts the latitude and longitude values to proper float types, which should resolve most location-related issues.

## 📚 Learn more

- [Resource center](https://strapi.io/resource-center) - Strapi resource center.
- [Strapi documentation](https://docs.strapi.io) - Official Strapi documentation.
- [Strapi tutorials](https://strapi.io/tutorials) - List of tutorials made by the core team and the community.
- [Strapi blog](https://strapi.io/blog) - Official Strapi blog containing articles made by the Strapi team and the community.
- [Changelog](https://strapi.io/changelog) - Find out about the Strapi product updates, new features and general improvements.

Feel free to check out the [Strapi GitHub repository](https://github.com/strapi/strapi). Your feedback and contributions are welcome!

## ✨ Community

- [Discord](https://discord.strapi.io) - Come chat with the Strapi community including the core team.
- [Forum](https://forum.strapi.io/) - Place to discuss, ask questions and find answers, show your Strapi project and get feedback or just talk with other Community members.
- [Awesome Strapi](https://github.com/strapi/awesome-strapi) - A curated list of awesome things related to Strapi.

---

<sub>🤫 Psst! [Strapi is hiring](https://strapi.io/careers).</sub>
