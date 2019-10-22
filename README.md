# Tugas-8-Pemrograman-Jaringan

## Docker  
step			              | command							                                          | output  
------------------------+---------------------------------------------------------------+------------------------  
create go module folder	| mkdir go-mongodb-crud						                              | go-mongodb-crud folder  
into go module folder   | cd go-mongodb-crud						                                |  
create go module        | go mod init go-mongodb-crud					                          | go.mod  
go get depedency        | go get github.com/gorilla/mux; go.mongodb.org/mongo-driver/	  | go.sum  
create dockerfile	      |								                                                | Dockerfile  
build docker image      | sudo docker build -t go-mongodb-crud .			                  | go-mongodb-crud image  
run docker image        | sudo docker run --net=host -it go-mongodb-crud		            | running image
