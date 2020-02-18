This is an example project for working with rails and postgres.

### Setup:
1. Install docker
2. Run `docker-compose up` to start rails and postgres containers (takes a while the first time)
3. We need to create the db before we can go any further. For this we'll connect to the docker container. 
	1. In a second terminal connect to the rails container by running: `docker exec -it rails-basics_api_1 bash`
	3. Run `rake db:create && rake db:migrate`
4. Open [http://localhost:3456/](http://localhost:3456/) to verify the project is working.

### Working in the console:
1. Run `docker-compose up` to start rails and postgres containers 
2. In a second terminal connect to the rails container by running: `docker exec -it rails-basics_api_1 bash`
    3. Open the console with `rails console`
    4. A (non-rails) ruby console can be opened with the `irb` command



