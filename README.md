> [!Note]
> DO NOT UPLOAD API KEY TO GITHUB OR OTHER PUBLIC PLATFORM!!!!!


## Requirements
+ docker
+ docker-compose

## Usage

+ Build Image
```
docker compose build
```

+ Deploy
```
docker compose up -d
```

+ Play

  + Connect to the environment
    ```
    ssh player@127.0.0.1
    ```
    > Password: isc

  + Start a new access (execute one more time if not working)
    ```
    ./newsess
    ```
   


+ Shut off

```
docker compose down
```



