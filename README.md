# Pulumi Example Project

This repository contains a minimal Pulumi program written in TypeScript based on the [Pulumi fundamentals tutorial](https://www.pulumi.com/tutorials/pulumi-fundamentals/). It demonstrates how to deploy a simple application stack using Pulumi and Docker. The stack includes a frontend, backend, and MongoDB database, all running in Docker containers.

## Prerequisites

- [Node.js](https://nodejs.org/) (v18 or later)
- [Pulumi CLI](https://www.pulumi.com/docs/get-started/install/)
- [Docker](https://www.docker.com/)

## Installation

1. Clone the repository:

   ```sh
   git clone https://github.com/mikeeggertsen/pulumi-example.git
   cd pulumi-example
   ```

2. Install dependencies:

   ```sh
   npm install
   ```

## Configuration

The project uses Pulumi configuration to manage environment-specific settings. Update the configuration files (`Pulumi.dev.yaml`, `Pulumi.staging.yaml`) as needed.

### Example Configuration (`Pulumi.dev.yaml`)

```yaml
config:
  pulumi-example:frontendPort: "3001"
  pulumi-example:backendPort: "3000"
  pulumi-example:mongoPort: "27017"
  pulumi-example:mongoHost: mongodb://mongo:27017
  pulumi-example:database: cart
  pulumi-example:nodeEnvironment: development
  pulumi-example:protocol: http://
```

## Usage

1. Log in to Pulumi:

   ```sh
   pulumi login
   ```

2. Select or create a stack:

   ```sh
   pulumi stack select dev
   ```

3. Configure the stack:

   ```sh
   pulumi config set pulumi-example:frontendPort 3001
   pulumi config set pulumi-example:backendPort 3000
   pulumi config set pulumi-example:mongoPort 27017
   pulumi config set pulumi-example:mongoHost mongodb://mongo:27017
   pulumi config set pulumi-example:database cart
   pulumi config set pulumi-example:nodeEnvironment development
   pulumi config set pulumi-example:protocol http://
   pulumi config set pulumi-example:mongoUsername admin
   pulumi config set --secret pulumi-example:mongoPassword <your-password>
   ```

4. Preview the changes:

   ```sh
   pulumi preview
   ```

5. Deploy the stack:

   ```sh
   pulumi up
   ```

6. Destroy the stack when done:

   ```sh
   pulumi destroy
   ```

## Project Details

- **Frontend**: Runs on the configured `frontendPort`.
- **Backend**: Runs on the configured `backendPort` and connects to MongoDB.
- **MongoDB**: Runs on the configured `mongoPort` with authentication enabled.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
