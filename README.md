{
  "name": "newDatabaseExistingServer",
  "schemaVersion": "2014-01.1.0-preview",
  "tags": {
    "foo": "bar"
  },
  "parameters": {
    "serverName": {
      "type": "string"
    },
    "databaseName": {
      "type": "string"
    },
    "collation": {
      "type": "string"
    },
    "edition": {
      "type": "string"
    },
    "maxSizeBytes": {
      "type": "string"
    }
  },
  "variables": {},
  "resources": [
    {
      "name": "[parameters('serverName')]",
      "type": "Microsoft.SQLDatabase/Server",
      "resources": [
        {
          "name": "[parameters('databaseName')]",
          "type": "Microsoft.SQLDatabase/DatabaseServer/Database",
          "properties": {
            "edition": "Web",
            "collation": "[parameters('collation')]",
            "maxSizeBytes": "1073741824"
          }
        }
      ]
    }
  ],
  "outputs": {
    "connectionString": {
      "type": "string",
      "value": "[reference('[parameters('serverName')]').properties.connectionString]"
    }
  }
}
