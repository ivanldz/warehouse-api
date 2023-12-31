# Warehouse Microservice

Part of a challenge involving the creation of 3 microservices responsible for managing a culinary API. These microservices collectively handle order management and its states, inventory management, and frontend interaction. This microservice, specifically, is responsible for warehouse management.

## Responsibility

This stock management service is responsible for coordinating and executing operations related to inventory management. This includes validating product availability to generate orders, as well as managing the replenishment of depleted products. Additionally, the service records purchase transactions and provides functionality to display an updated listing of available ingredients.

## About the Project

The project is structured following the clean architecture pattern, which is a software design approach that aims to create highly independent, decoupled, and layered systems, facilitating code understanding, maintenance, and evolution.

### Folder Structure

- Domain: System policies. Entities and repositories that will exist in the application are declared here.
- Application: Business logic of the system. Contains all the use cases of the application.
- Infrastructure: Everything unrelated to the core business logic of our application. This includes database connection and configuration, actual implementation of domain elements, and the use of application services by injecting these new implementations.



## API Reference

#### Valid stock

```http
  POST /api/stock
```

- Body **Required**:
```json
[
	{
		"quantity": // Required quantity,
		"ingredient": {
			"id": // Ingredient ID,
			"name": // Ingredient name
		}
	}
]
```

- __Response__: 
| Type     | Description| 
|:------- | :------------ |
| `boolean` | Whether the stock is available. A purchase is made if it's not |

#### Get purchases

```http
  GET /api/purchases/${id}
```

| Parameter | Type     | Description                       |
| :-------- | :------- | :-------------------------------- |
| `page`      | `number` | **Required**. page |

- __Response__: 
| Type     | Description| 
:------- | :------------ |
| `Page` |  Responds with a page containing records of all purchases made in the Marketplace |



#### Get ingredients

```http
  GET /api/ingredients/${id}
```

| Parameter | Type     | Description                       |
| :-------- | :------- | :-------------------------------- |
| `page`    | `number` | **Required**. page |

- __Response__: 
| Type   | Description| 
|:-------| :------------ |
| `Page` | Responds with a page containing ingredients and their quantities|



## Usage

You can use the Dockerfile present in the project root to launch the application, or you can use docker-compose.yaml to start the app along with a mongoose service.

You can also install everything locally using:
```bash
  yarn install
  yarn dev
```