# Set up Primsa db

### Install Prisma CLI

`$ npm install -g prisma`

### Set up new service

`$ NODE_TLS_REJECT_UNAUTHORIZED=0 yarn prisma init name-of-your-service`

Choose `Demo server`

Rename `datamodel.prisma` to `datamodel.graphql`

`$ prisma deploy`

`$ prisma playground`
