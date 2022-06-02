# Welcome to GovCMS!
print("""
-----------------------------------------------------------------
✨ Hello GovCMS!
-----------------------------------------------------------------
""".strip())

# Include sub sites.
docker_compose(['./docker-compose.yml',
               './sites/client1/docker-compose.yml',
                './sites/client2/docker-compose.yml',
                './sites/api/docker-compose.yml'])
docker_build('govcms.api/govcms', './.docker/govcms')

# Group the development services.
dc_resource('api', labels=['Frontend'])
dc_resource('client1', labels=['Frontend'])
dc_resource('client2', labels=['Frontend'])
dc_resource('mariadb', labels=['Backend'])
dc_resource('mailhog', labels=['Development'])
dc_resource('adminer', labels=['Development'])

# Good bye.
if config.tilt_subcommand == 'down':
    print('Goodbye world!')
