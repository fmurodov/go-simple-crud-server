### Simple go http CRUD server

```mermaid
graph LR;

	DATABASE --> server[MOVIES SERVER]
	
	subgraph  
		server[MOVIES SERVER]
	end
	
	subgraph ROUTES
		server[MOVIES SERVER] --> getall[GET ALL];
		server[MOVIES SERVER] --> getbyid[GET BY ID];
		server[MOVIES SERVER] --> CREATE;
		server[MOVIES SERVER] --> UPDATE;
		server[MOVIES SERVER] --> DELETE;
	end

	subgraph FUNCTIONS
		getall[GET ALL] --> getMovies;
		getbyid[GET BY ID] --> getMovie;
		CREATE --> createMovie;
		UPDATE --> updateMovie;
		DELETE --> deleteMovie;
	end

	subgraph ENTRYPOINTS
		getMovies --> epGetAll["/movies"];
		getMovie --> epGetID["/movies/id"];
		createMovie --> epCreate["/movies"];
		updateMovie --> epUpdate["/movies/id"];
		deleteMovie --> epDelete["/movies/id"];
	end

	subgraph METHODS
		epGetAll["/movies"] --> methodGetAll[GET];
		epGetID["/movies/id"] --> methodGetID[GET];
		epCreate["/movies"] --> methodCreate[POST];
		epUpdate["/movies/id"] --> methodupdate[PUT];
		epDelete["/movies/id"] --> methodDelete[DELETE];
	end

	methodGetAll[GET] --- client;
	methodGetID[GET] --- client;
	methodCreate[POST] --- client;
	methodupdate[PUT] --- client;
	methodDelete[DELETE] --- client;

```

#### Usage:

GET ALL
```
GET http://localhost:8000/movies
```


GET BY ID
```
GET http://localhost:8000/movies/3
```


CREATE
```
POST http://localhost:8000/movies
```
body:
```json
{
    "isbn": "101",
    "title": "Matrix",
    "director": {
        "firstname": "Lana",
        "lastname": "Wachowski"
    }
}
```


UPDATE
```
	PUT http://localhost:8000/movies/8498081
```
body:
```json
{
    "isbn": "789",
    "title": "The Dark Knight",
    "director": {
        "firstname": "Christopher",
        "lastname": "Nolan"
    }
}
```


DELETE
```
DELETE http://localhost:8000/movies/3
```
