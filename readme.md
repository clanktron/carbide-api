# Secure Pipeline Database API 

## Build

```bash
# compile the binary
make
# for more options try
make help
```
## Environment

| Environment Variable  | Description               | Optional                  |
| --------------------  | -----------               | --------                  |
| DBUSER                | MySQL/MariaDB username    | false                     |
| DBPASS                | MySQL/MariaDB password    | false                     |
| DBHOST                | MySQL/MariaDB host        | false                     |
| DBPORT                | MySQL/MariaDB port        | false                     |
| DBNAME                | MySQL/MariaDB name        | false                     |
| PORT                  | port to serve api         | true (defaults to 5000)   |

## Develop
```bash
# This will start the api and hot reload such whenever changes are saved to a .go file.
./reload.sh
```

## Deploy
Bare-metal, docker, and k8s deployments are all supported - though k8s is recommended.
```bash
helm install carbide-api ./chart --values <values-file>
```

## REST Schema
>prefix: https://\<backendurl\>/api/v0/

#### Functional Endpoints:
- /product
    - GET: get all products
    - POST: create new product
- /product/{product_name}
    - GET: get product
    - PUT: update product
    - DELETE: delete product
- /product/{product_name}/release
    - GET: get all releases for product
    - POST: create new release for product
- /product/{product_name}/release/{release_name}
    - GET: get release
    - PUT: update release
    - DELETE: delete release
- /image
    - GET: get all images
    - POST: create new image
- /image/{image_id}
    - GET: get image
    - PUT: update image
    - DELETE: delete image
- /releaseimgmapping
    - GET: get all releaseimgmappings
    - POST: create new releaseimgmapping
    - DELETE: delete releaseimgmapping

#### Possible Additions:
- /user
    - POST: should accept username and password
        - only returns cookie first time user is created
- /login
    - POST: should accept username and password
        - returns authentication cookie/token (stored in browser by frontend)
- /product/{product_name}/release/{release_name}/image
    - GET: get all images for product release
    - POST: create new image for product release
- /product/{product_name}/release/{release_name}/image/{image_name}
    - GET: get image from product release
    - PUT: update image from product release
    - DELETE: delete image from product release
- /release
    - GET: get all releases
    - POST: create new release
- /release/{release_name}
    - GET: get release
    - PUT: update release
    - DELETE: delete release
