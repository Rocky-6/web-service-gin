# 概要
Goのチュートリアル<br>
･Tutorial: Developing a RESTful API with Go and Gin<br>
https://go.dev/doc/tutorial/web-service-gin<br>
･Tutorial: Accessing a relational database<br>
https://go.dev/doc/tutorial/database-access<br>
で作ったプログラムを合わせてDockerで起動する<br>
<br>

# 使い方
```
git clone https://github.com/Rocky-6/web-service-gin.git

cd web-service-gin

docker-compose up --build
```
<br>

From a new command line window, use curl to make a request to your running web service.<br>
<br>
Add Album
```
curl http://localhost:8080/albums \
    --include \
    --header "Content-Type: application/json" \
    --request "POST" \
    --data '{"title": "The Modern Sound of Betty Carter","artist": "Betty Carter","price": 49.99}'
```
The command should display headers and JSON for the added album.
```
HTTP/1.1 201 Created
Content-Type: application/json; charset=utf-8
Date: Fri, 05 Aug 2022 08:09:40 GMT
Content-Length: 114

{
    "id": 0,
    "title": "The Modern Sound of Betty Carter",
    "artist": "Betty Carter",
    "price": 49.99
}

```
<br>

Get Albums
```
curl http://localhost:8080/albums
```
The command should display the data you added.
```
[
    {
        "id": 1,
        "title": "The Modern Sound of Betty Carter",
        "artist": "Betty Carter",
        "price": 49.99
    }
]
```
<br>

Get Albums by id, title or artist.
```
curl http://localhost:8080/albums/id/2
```
```
curl http://localhost:8080/albums/artist/Betty%20Carter
```
The command should display JSON for the album whose ID you used. If the album wasn’t found, you’ll get JSON with an error message.
```
{
    "id": 2,
    "title": "Blue Train",
    "artist": "John Coltrane",
    "price": 56.99
}
```
```
[
    {
        "id": 1,
        "title": "The Modern Sound of Betty Carter",
        "artist": "Betty Carter",
        "price": 49.99
    }
]
```