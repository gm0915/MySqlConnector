---
title: MySqlBulkCopyColumnMapping
---

# MySqlBulkCopyColumnMapping class

Use [`MySqlBulkCopyColumnMapping`](../MySqlBulkCopyColumnMappingType/) to specify how to map columns in the source data to columns in the destination table when using [`MySqlBulkCopy`](../MySqlBulkCopyType/).

Set [`SourceOrdinal`](../MySqlBulkCopyColumnMapping/SourceOrdinal/) to the index of the source column to map. Set [`DestinationColumn`](../MySqlBulkCopyColumnMapping/DestinationColumn/) to either the name of a column in the destination table, or the name of a user-defined variable. If a user-defined variable, you can use [`Expression`](../MySqlBulkCopyColumnMapping/Expression/) to specify a MySQL expression that assigns its value to destination column.

Source columns that don't have an entry in [`ColumnMappings`](../MySqlBulkCopy/ColumnMappings/) will be ignored (unless the [`ColumnMappings`](../MySqlBulkCopy/ColumnMappings/) collection is empty, in which case all columns will be mapped one-to-one).

MySqlConnector will transmit all binary data as hex, so any expression that operates on it must decode it with the `UNHEX` function first. (This will be performed automatically if no [`Expression`](../MySqlBulkCopyColumnMapping/Expression/) is specified, but will be necessary to specify manually for more complex expressions.)

Example code:

```csharp
new MySqlBulkCopyColumnMapping
{
    SourceOrdinal = 2,
    DestinationColumn = "user_name",
},
new MySqlBulkCopyColumnMapping
{
    SourceOrdinal = 0,
    DestinationColumn = "@tmp",
    Expression = "column_value = @tmp * 2",
},
```

```csharp
public sealed class MySqlBulkCopyColumnMapping
```

## Public Members

| name | description |
| --- | --- |
| [MySqlBulkCopyColumnMapping](../MySqlBulkCopyColumnMapping/MySqlBulkCopyColumnMapping/)() | Initializes [`MySqlBulkCopyColumnMapping`](../MySqlBulkCopyColumnMappingType/) with the default values. |
| [MySqlBulkCopyColumnMapping](../MySqlBulkCopyColumnMapping/MySqlBulkCopyColumnMapping/)(…) | Initializes [`MySqlBulkCopyColumnMapping`](../MySqlBulkCopyColumnMappingType/) to the specified values. |
| [DestinationColumn](../MySqlBulkCopyColumnMapping/DestinationColumn/) { get; set; } | The name of the destination column to copy to. To use an expression, this should be the name of a unique user-defined variable. |
| [Expression](../MySqlBulkCopyColumnMapping/Expression/) { get; set; } | An optional expression for setting a destination column. To use an expression, the [`DestinationColumn`](../MySqlBulkCopyColumnMapping/DestinationColumn/) should be set to the name of a user-defined variable and this expression should set a column using that variable. |
| [SourceOrdinal](../MySqlBulkCopyColumnMapping/SourceOrdinal/) { get; set; } | The ordinal position of the source column to map from. |

## See Also

* namespace [MySqlConnector](../../MySqlConnectorNamespace/)
* assembly [MySqlConnector](../../MySqlConnectorAssembly/)

<!-- DO NOT EDIT: generated by xmldocmd for MySqlConnector.dll -->