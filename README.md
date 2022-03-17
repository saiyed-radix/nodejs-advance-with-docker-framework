# Node Js Advance: Docker, Frameworks and Perfomance Enhancing

## Milestone 1:

- Set up node application with Docker
- Docker compose basics, Images, commands, Cli
- Writing node dockerfiles & best practises.

### Reference links:

- https://www.docker.com/
- https://www.docker.com/get-started
- https://www.bezkoder.com/docker-compose-nodejs-mongodb/

## Milestone 2:

- Learn node framework KOA Or Hapi
  - https://koajs.com/
  - https://hapi.dev/
- Enhancing Performance (clustering, forking- children)

  - **clustering**
    - https://www.w3schools.com/nodejs/ref_cluster.asp
    - https://nodejs.org/api/cluster.html
    - https://blog.logrocket.com/optimize-node-js-performance-with-clustering/
    - https://blog.appsignal.com/2021/02/03/improving-node-application-performance-with-clustering.html
    - https://www.arubacloud.com/tutorial/how-to-use-cluster-to-increase-node-js-performance.aspx

- PM2 Installation & configuration
  - https://pm2.io/docs/runtime/guide/installation/
  - https://www.digitalocean.com/community/tutorials/how-to-use-pm2-to-setup-a-node-js-production-environment-on-an-ubuntu-vps
  - https://www.tecmint.com/install-pm2-to-run-nodejs-apps-on-linux-server/
- Datacaching with Redis
  - https://redis.com/ebook/part-1-getting-started/chapter-2-anatomy-of-a-redis-web-application/2-4-database-row-caching/
  - https://redis.io/topics/client-side-caching
- Error logging practises - sentry or stackify
  - **sentry**
    - https://sentry.io/for/node/
    - https://daily.dev/blog/error-logging-with-sentry-on-fastify
  - **stackify**
    - https://stackify.com/node-js-logging/

## Exercise:
- Create a architecture using docker (The application should be built as a collection of two Docker containers)
    - ApplicationModel Container 
        - This component should be the database component.
        - This should be contains docker-compose.yml and Dockerfile for configuring the PostgreSQL/mongoDb/mySQL database.
        - When docker is set-up that time default schema will be create based on default schema file.
        - Default Schema should like
          - User schema

            | field | type | constraint | Default |
            |------|------|------|------|
            |id| auto increment | PRIMARY KEY |  |
            |oid| text | UNIQUE NOT NULL  | |
            |date_created| TIMESTAMPTZ |  | NOW()|
            |date_edited| TIMESTAMPTZ |  | NOW()|
            |email| text | UNIQUE NOT NULL | |
            |first_name| text | NOT NULL | |
            |middle_name| text | NOT NULL | |
            |last_name| text | NOT NULL | |
            |verify_email_token| text | | |
            |verify_email_token_expiry| timestamp | | |
            |activation_token| text | | |
            |activation_token_expiry| timestamp | | |
            |status| text |  NOT NULL| 'unverified' |
            |date_status_changed| text | | |
            |password_reset_token| text | | |
            |password_reset_expiry| timestamp | | |
            |password_salt| text | | |
            |password_hash| text | | |
            |password_algo| text | | |
            

    - Controller Container
        - This component should be the NodeJS application exposing all API endpoints needed by the applicat.
        - This is a purely back-end application and primarily accepts and returns JSON. HTML is not returned from any API endpoints - front-ends are responsible for displaying or parsing returned data.
        - This contains the docker-compose.yml and Dockerfile for configuring the NodeJS with specific verison.
        - Configure pm2 in dockerfile and run the controller application
        - Create an end-points for user-management with error handling and logs using the 
          - Sign-up
            - endpoint: `/sign-up`
          - Login
            - endpoint: `/login`
          - User email verification, after registration
            - endpoint: `/user-verified-email`
          - User set password request after email verification
            - endpoint: `/user-activate`
          - User forgot password request when user forgot the password
            - endpoint: `/user-init-password-reset`
          - User reset password request when receive an email for set new password link
            - endpoint: `/user-complete-password-reset`

- Create a security, User can only able to register max 5 users per day from same ip address
  - Use datas caching mechanism for log user registration based on ip.

## What you will be able to do post this course:

- can learn new framework expect then express
- Can learn perfomance optimization using node code
- Can learn datas caching mechanism with node code
- Can lean PM2 deployment for node
