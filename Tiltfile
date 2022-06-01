# Welcome to GovCMS!
print("""
-----------------------------------------------------------------
✨ Hello GovCMS!
-----------------------------------------------------------------
""".strip())

# Build local instances.
k8s_yaml(kustomize('./configs/kustomize'))

# include sub sites.
include('./api/Tiltfile')

# Good bye.
if config.tilt_subcommand == 'down':
    print('Goodbye world!')
