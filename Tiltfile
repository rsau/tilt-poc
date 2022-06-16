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
                './sites/api-oauth/docker-compose.yml',
                './sites/api/docker-compose.yml'])
docker_build('govcms.api/drupal', './.docker/drupal')
docker_build('govcms.api/govcms', './.docker/govcms')
docker_build('govcms.api/govcms-client', './.docker/govcms-client')
docker_build('govcms.api/govcms-miniorange', './.docker/govcms-api')
docker_build('govcms.api/govcms-oauth', './.docker/govcms-api-oauth')

#docker_compose(['./sites/client3/docker-compose.yml'])
#docker_compose(['./sites/client4/docker-compose.yml'])

# Group the development services.
dc_resource('nginx-proxy', labels=['Service'])
dc_resource('mariadb', labels=['Service'])
dc_resource('mailhog', labels=['Development'])
dc_resource('adminer', labels=['Development'])

# Group the keycloak.
dc_resource('postgres', labels=['Keycloak'])
dc_resource(
    'keycloak',
    resource_deps=['postgres'],
    labels=['Keycloak'])

# Group the Kong.
dc_resource('kong-database', labels=['Kong'])
dc_resource(
    'kong-migration',
    resource_deps=['kong-database'],
    labels=['Kong'])
dc_resource(
    'kong',
    resource_deps=['kong-migration'],
    links=['api.govcms.local'],
    labels=['Kong'])
dc_resource(
    'konga-prepare',
    resource_deps=['kong-database'],
    labels=['Kong'])
dc_resource(
    'konga',
    resource_deps=['kong'],
    labels=['Kong'])

# Group the sites.
dc_resource(
    'client1',
    resource_deps=['nginx-proxy', 'mariadb'],
    links=['client1.govcms.local'],
    labels=['Client'])
dc_resource(
    'client2',
    resource_deps=['nginx-proxy', 'mariadb'],
    links=['client2.govcms.local'],
    labels=['Client'])
dc_resource(
    'api',
    resource_deps=['nginx-proxy', 'mariadb'],
    links=['api-keycloak.govcms.local'],
    labels=['API'])
dc_resource(
    'api-miniorange',
    resource_deps=['nginx-proxy', 'mariadb'],
    links=['api-miniorange.govcms.local'],
    labels=['API'])
dc_resource(
    'api-oauth',
    resource_deps=['nginx-proxy', 'mariadb'],
    links=['api-oauth.govcms.local'],
    labels=['API'])

# Conditionally load a local.tiltfile for additional functionality.
if os.path.exists('local.tiltfile'):
  load_dynamic('local.tiltfile')

# Good bye.
if config.tilt_subcommand == 'down':
    print('Greetings!')
