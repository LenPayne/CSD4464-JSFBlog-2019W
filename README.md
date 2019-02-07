# JSF Blog Sample

This sample has been prepared as a basic JavaServer Faces Blog. It is built in
NetBeans on GlassFish with JavaDB.

The following SQL is provided for reference:

    CREATE TABLE users (
        id INT NOT NULL PRIMARY KEY GENERATED ALWAYS AS IDENTITY (START WITH 1, INCREMENT BY 1),
        username VARCHAR(255) NOT NULL UNIQUE,
        passhash VARCHAR(255) NOT NULL
    );

    CREATE TABLE posts (
        id INT NOT NULL PRIMARY KEY GENERATED ALWAYS AS IDENTITY (START WITH 1, INCREMENT BY 1),
        user_id INT NOT NULL,
        title VARCHAR(255) NOT NULL UNIQUE,
        created_time TIMESTAMP NOT NULL,
        contents LONG VARCHAR,
        FOREIGN KEY (user_id) REFERENCES users(id)
    );
    
    -- Optional Sample Data
    -- Sets up 'user' with password 'P@ssw0rd'
    INSERT INTO users (username, passhash) 
        VALUES('user', 'E0478D09678A204E0DFD77C3F12500C08E03345E');
    
    INSERT INTO posts (user_id, title, created_time, contents)
        VALUES (1, 'Sample Post', CURRENT_TIMESTAMP, 'Lorem ipsum dolor sit amet.');