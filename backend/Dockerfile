FROM node:18-alpine

# Install OpenSSL and other necessary libraries
RUN apk add --no-cache openssl libc6-compat

WORKDIR /app

COPY package*.json ./
RUN npm install

COPY . .

# Generate Prisma client
RUN npx prisma generate
RUN npx prisma migrate dev
RUN npm run prisma:seed

EXPOSE 3001

CMD ["npm", "start"]

