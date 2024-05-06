[MarketValueApp.postman_collection.json](https://github.com/nabisaheb782/MarketValueApp/files/15215115/MarketValueApp.postman_collection.json)
*************** Market Value Calculator *****************

This project is a Spring Boot application that provides RESTful APIs for calculating the market value of funds and investors' portfolios. It allows users to add funds, holdings, and investors, and then calculate the market value of individual funds or the entire portfolio of an investor, optionally excluding specific holdings.

Table of Contents:

Introduction
Technologies Used
Setup
Project Structure
Dependencies
API Endpoints
Testing


Introduction:
This project is aimed at managing market investments, specifically focusing on funds, holdings, and investors. It provides functionalities to add funds, add holdings to funds, and calculate market values based on fund or investor.

Technologies Used:
Java
Spring Boot
Spring Data JPA
H2 Database (for local testing, can be replaced with other databases like MySQL, PostgreSQL, etc.)
JUnit 5 (for testing)
Mockito (for mocking dependencies in tests)
Maven (for dependency management and building)

Setup:
1.Clone the repository: git clone https://github.com/your-username/market-value-calculator.git
2.Navigate to the project directory:cd market-value-calculator
3.Build the project: mvn clean install
4.Run the application: mvn spring-boot:run

The application will start running on http://localhost:8080.

Project Structure:

Controller Package:
1.FundController.java: Manages endpoints related to fund operations such as adding funds.
2.GraphController.java: Handles endpoints for calculating market values.
3.HoldingController.java: Handles endpoints for holding operations like adding holdings.

Entity Package:
1.Fund.java: Represents a fund entity with properties like id, name, and list of holdings.
2.Holding.java: Represents a holding entity with properties like id, name, quantity, and reference to fund.
3.Investor.java: Represents an investor entity with properties like id, name, and list of funds.

Service Package:
1.FundService.java: Provides service methods for fund-related operations like adding funds.
2.GraphService.java: Provides service methods for calculating market values.
3.HoldingService.java: Provides service methods for holding-related operations like adding holdings.
4.InvestorService.java: Provides service methods for investor-related operations like adding investors and      retrieving investor details.


Dependencies
Spring Boot: Provides the framework for building Spring-based applications.
JPA (Java Persistence API): Used for managing relational data in Java applications.
H2 Database: Embedded database for storing application data during development.
Jakarta Persistence: Provides API for managing entities and relational databases.


API Endpoints:
1. Add Fund: POST /fund/{investorName}
Add a new fund for a specific investor.

2. Calculate Market Value of Fund: GET /marketValue/{fundName}?exclusion={holdingName}
Calculate the market value of a specific fund, optionally excluding a specific holding.

3.Calculate Market Value of Investor's Portfolio: GET /InvestorMarketValue/{investorName}?exclusion={holdingName}
Calculate the market value of an investor's entire portfolio, optionally excluding a specific holding.

4.Add Holding: POST /holding/{fundName}/{investorName}
Add a new holding to a specific fund for a specific investor.



[Uploading MarketValueApp.postman{
	"info": {
		"_postman_id": "518acf3e-bed3-47f4-8e0f-e47b87dfac7f",
		"name": "MarketValueApp",
		"schema": "https://schema.getpostman.com/json/collection/v2.1.0/collection.json",
		"_exporter_id": "33988050"
	},
	"item": [
		{
			"name": "Create Investor",
			"request": {
				"method": "POST",
				"header": [],
				"body": {
					"mode": "raw",
					"raw": "    {\r\n      \"name\": \"nani\"\r\n      \r\n    }",
					"options": {
						"raw": {
							"language": "json"
						}
					}
				},
				"url": {
					"raw": "http://localhost:8080/investor",
					"protocol": "http",
					"host": [
						"localhost"
					],
					"port": "8080",
					"path": [
						"investor"
					]
				}
			},
			"response": []
		},
		{
			"name": "CreateFundForInvestor",
			"request": {
				"method": "POST",
				"header": [],
				"body": {
					"mode": "raw",
					"raw": "{\r\n          \"name\": \"f1\"\r\n          \r\n         \r\n        }\r\n",
					"options": {
						"raw": {
							"language": "json"
						}
					}
				},
				"url": {
					"raw": "http://localhost:8080/fund/nani",
					"protocol": "http",
					"host": [
						"localhost"
					],
					"port": "8080",
					"path": [
						"fund",
						"nani"
					]
				}
			},
			"response": []
		},
		{
			"name": "CreateHoldingForFunds",
			"request": {
				"method": "POST",
				"header": [],
				"body": {
					"mode": "raw",
					"raw": "\r\n            {\r\n              \"name\": \"h1\",\r\n              \"quantity\": 10.0\r\n            }",
					"options": {
						"raw": {
							"language": "json"
						}
					}
				},
				"url": {
					"raw": "http://localhost:8080/holding/f1/nani",
					"protocol": "http",
					"host": [
						"localhost"
					],
					"port": "8080",
					"path": [
						"holding",
						"f1",
						"nani"
					]
				}
			},
			"response": []
		},
		{
			"name": "GetsMarketValue",
			"request": {
				"method": "GET",
				"header": [],
				"url": {
					"raw": "http://localhost:8080/marketValue/f1?exclusion=\"h1\"",
					"protocol": "http",
					"host": [
						"localhost"
					],
					"port": "8080",
					"path": [
						"marketValue",
						"f1"
					],
					"query": [
						{
							"key": "exclusion",
							"value": "\"h1\""
						}
					]
				}
			},
			"response": []
		},
		{
			"name": "GetsInvestorMarketValue",
			"request": {
				"method": "GET",
				"header": [],
				"url": {
					"raw": "http://localhost:8080/marketValue/InvestorMarketValue/{nani}",
					"protocol": "http",
					"host": [
						"localhost"
					],
					"port": "8080",
					"path": [
						"marketValue",
						"InvestorMarketValue",
						"{nani}"
					]
				}
			},
			"response": []
		}
	]
}_collection.json…]()



