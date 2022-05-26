# Welcome to GovCMS!
print("""
-----------------------------------------------------------------
✨ Hello GovCMS!
-----------------------------------------------------------------
""".strip())


# Build Docker image.
docker_compose('./docker-compose.yml')
# docker_compose(['./docker-compose.yml', './docker-compose.override.yml'])

dc_resource("mariadb", labels=["backend"])
dc_resource("mariadb-client1", labels=["backend"])
dc_resource("mariadb-client2", labels=["backend"])
dc_resource("mariadb-client3", labels=["backend"])
dc_resource("adminer", labels=["development"])
dc_resource("mailhog", labels=["development"])
dc_resource("api", labels=["app"])
dc_resource("client1", labels=["app"])
dc_resource("client2", labels=["app"])
#dc_resource("client3", labels=["app"])

# Good bye.
if config.tilt_subcommand == 'down':
    print('Goodbye world!')
