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
                './sites/api-miniorange/docker-compose.yml',
                './sites/api/docker-compose.yml'])
docker_build('govcms.api/drupal', './.docker/drupal')
docker_build('govcms.api/govcms', './.docker/govcms')
docker_build('govcms.api/govcms-client', './.docker/govcms-client')
docker_build('govcms.api/govcms-miniorange', './.docker/govcms-api')

# Group the development services.
dc_resource('api', labels=['API'])
dc_resource('api-miniorange', labels=['API'])
dc_resource('client1', labels=['Client'])
dc_resource('client2', labels=['Client'])
dc_resource('mariadb', labels=['Development'])
dc_resource('mailhog', labels=['Development'])
dc_resource('adminer', labels=['Development'])

# Good bye.
if config.tilt_subcommand == 'down':
    print('Goodbye world!')
