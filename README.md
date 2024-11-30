# Symfony + Next.js Dev Container Example

This is a dev container example for Symfony and Next.js. It is based on the [Symfony-DevContainer](https://github.com/yoanbernabeu/Symfony-DevContainer).

VS Code or PhpStorm can be used as IDE.

## Usage

Open this project with your IDE's dev container feature.

### Symfony

```bash
symfony new backend
cd backend
composer install
symfony server:start --no-tls
```

`http://localhost:8000` should be available.

### Next.js

```bash
npx create-next-app@latest frontend
cd frontend
npm install
npm run dev
```

`http://localhost:3000` should be available.

### MySQL

You can connect to the MySQL database using IDE SQL tools with the following credentials:

- Host: `database`
- Port: `3306`
- User: `root`
- Password: `passw0rd`

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
