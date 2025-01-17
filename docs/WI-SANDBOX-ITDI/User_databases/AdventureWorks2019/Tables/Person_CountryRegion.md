#### 

[Project](../../../../index.md) > [WI-SANDBOX-ITDI](../../../index.md) > [User databases](../../index.md) > [AdventureWorks2019](../index.md) > [Tables](Tables.md) > Person.CountryRegion

# ![Tables](../../../../Images/Table32.png) [Person].[CountryRegion]

---

## <a name="#description"></a>MS_Description

Lookup table containing the ISO standard codes for countries and regions.

## <a name="#properties"></a>Properties

| Property | Value |
|---|---|
| Collation | SQL_Latin1_General_CP1_CI_AS |
| Row Count (~) | 238 |
| Created | 12:07:29 PM Monday, May 8, 2023 |
| Last Modified | 12:07:39 PM Monday, May 8, 2023 |


---

## <a name="#columns"></a>Columns

| Key | Name | Data Type | Max Length (Bytes) | Nullability | Default | Description |
|---|---|---|---|---|---|---|
| [![Cluster Primary Key PK_CountryRegion_CountryRegionCode: CountryRegionCode](../../../../Images/pkcluster.png)](#indexes) | CountryRegionCode | nvarchar(3) | 6 | NOT NULL |  | _ISO standard code for countries and regions._ |
| [![Indexes AK_CountryRegion_Name](../../../../Images/Index.png)](#indexes) | Name | [dbo].[Name] | 100 | NOT NULL |  | _Country or region name._ |
|  | ModifiedDate | datetime | 8 | NOT NULL | (getdate()) | _Date and time the record was last updated._ |


---

## <a name="#indexes"></a>Indexes

| Key | Name | Key Columns | Unique | Description |
|---|---|---|---|---|
| [![Cluster Primary Key PK_CountryRegion_CountryRegionCode: CountryRegionCode](../../../../Images/pkcluster.png)](#indexes) | PK_CountryRegion_CountryRegionCode | CountryRegionCode | YES | _Primary key (clustered) constraint_ |
|  | AK_CountryRegion_Name | Name | YES | _Unique nonclustered index._ |


---

## <a name="#sqlscript"></a>SQL Script

```sql
CREATE TABLE [Person].[CountryRegion]
(
[CountryRegionCode] [nvarchar] (3) COLLATE SQL_Latin1_General_CP1_CI_AS NOT NULL,
[Name] [dbo].[Name] NOT NULL,
[ModifiedDate] [datetime] NOT NULL CONSTRAINT [DF_CountryRegion_ModifiedDate] DEFAULT (getdate())
) ON [PRIMARY]
GO
ALTER TABLE [Person].[CountryRegion] ADD CONSTRAINT [PK_CountryRegion_CountryRegionCode] PRIMARY KEY CLUSTERED ([CountryRegionCode]) ON [PRIMARY]
GO
CREATE UNIQUE NONCLUSTERED INDEX [AK_CountryRegion_Name] ON [Person].[CountryRegion] ([Name]) ON [PRIMARY]
GO
EXEC sp_addextendedproperty N'MS_Description', N'Lookup table containing the ISO standard codes for countries and regions.', 'SCHEMA', N'Person', 'TABLE', N'CountryRegion', NULL, NULL
GO
EXEC sp_addextendedproperty N'MS_Description', N'ISO standard code for countries and regions.', 'SCHEMA', N'Person', 'TABLE', N'CountryRegion', 'COLUMN', N'CountryRegionCode'
GO
EXEC sp_addextendedproperty N'MS_Description', N'Date and time the record was last updated.', 'SCHEMA', N'Person', 'TABLE', N'CountryRegion', 'COLUMN', N'ModifiedDate'
GO
EXEC sp_addextendedproperty N'MS_Description', N'Country or region name.', 'SCHEMA', N'Person', 'TABLE', N'CountryRegion', 'COLUMN', N'Name'
GO
EXEC sp_addextendedproperty N'MS_Description', N'Default constraint value of GETDATE()', 'SCHEMA', N'Person', 'TABLE', N'CountryRegion', 'CONSTRAINT', N'DF_CountryRegion_ModifiedDate'
GO
EXEC sp_addextendedproperty N'MS_Description', N'Primary key (clustered) constraint', 'SCHEMA', N'Person', 'TABLE', N'CountryRegion', 'CONSTRAINT', N'PK_CountryRegion_CountryRegionCode'
GO
EXEC sp_addextendedproperty N'MS_Description', N'Unique nonclustered index.', 'SCHEMA', N'Person', 'TABLE', N'CountryRegion', 'INDEX', N'AK_CountryRegion_Name'
GO
EXEC sp_addextendedproperty N'MS_Description', N'Clustered index created by a primary key constraint.', 'SCHEMA', N'Person', 'TABLE', N'CountryRegion', 'INDEX', N'PK_CountryRegion_CountryRegionCode'
GO

```


---

## <a name="#uses"></a>Uses

* [dbo].[Name]
* [Person]


---

## <a name="#usedby"></a>Used By

* [Person].[StateProvince]
* [Sales].[CountryRegionCurrency]
* [Sales].[SalesTerritory]
* [[HumanResources].[vEmployee]](../Views/HumanResources_vEmployee.md)
* [Person].[vStateProvinceCountryRegion]
* [Purchasing].[vVendorWithAddresses]
* [Sales].[vIndividualCustomer]
* [Sales].[vSalesPerson]
* [Sales].[vStoreWithAddresses]


---

###### Author:  Smith, JC

###### Copyright 2024 - All Rights Reserved

###### Created: Thursday, July 11, 2024 1:50:21 PM

