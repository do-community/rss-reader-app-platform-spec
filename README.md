# rss-reader-app-platform-spec
The spec file and deployment instructions for the RSS Reader App.

# Deployment Instructions

To deploy the RSS Reader application to App Platform in its entirety follow
these steps:

1. Download [doctl](https://do.co/doctl) and install it following the 
instructions in the README.
2. Create an DigitalOcean API token and have it ready to paste
3. Run `doctl auth init -t YOUR_TOKEN` to authenticate yourself. 
4. Clone this repo. 
5. Search for every instance of CHANGE_ME in `spec.yaml` and fill it in with
the appropriate repsone. Currently it's just if your own custom domain and the
`DJANGO_ALLOWED_HOSTS` which should also just be your domain.
5. Run the command `doctl apps create --spec spec.yaml` to deploy your app. 
6. Once the app is up and running, go to the console tab under the API component
and run the following commands
    * `python manage.py migrate` - This does the initial database setup
    * `python manage.py createsuperuser` - Follow this prompt to create a 
    superuser to authenticate with
7. If you decided to use a custom domain, go to the Settings tab and follow
the instructions under `domain` to setup your DNS record properly.
8. Wait a while for the DNS to propogate and the SSL certificate to become valid
9. Go to your domain, add some RSS feeds and enjoy your app!
