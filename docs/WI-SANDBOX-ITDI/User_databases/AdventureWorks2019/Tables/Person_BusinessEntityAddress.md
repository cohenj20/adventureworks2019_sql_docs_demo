#### 

[Project](../../../../index.md) > [WI-SANDBOX-ITDI](../../../index.md) > [User databases](../../index.md) > [AdventureWorks2019](../index.md) > [Tables](Tables.md) > Person.BusinessEntityAddress

# ![Tables](../../../../Images/Table32.png) [Person].[BusinessEntityAddress]

---

## <a name="#description"></a>MS_Description

Cross-reference table mapping customers, vendors, and employees to their addresses.

## <a name="#properties"></a>Properties

| Property | Value |
|---|---|
| Row Count (~) | 19614 |
| Created | 12:07:29 PM Monday, May 8, 2023 |
| Last Modified | 12:07:38 PM Monday, May 8, 2023 |


---

## <a name="#columns"></a>Columns

| Key | Name | Data Type | Max Length (Bytes) | Nullability | Default | Description |
|---|---|---|---|---|---|---|
| [![Cluster Primary Key PK_BusinessEntityAddress_BusinessEntityID_AddressID_AddressTypeID: BusinessEntityID\AddressID\AddressTypeID](../../../../Images/pkcluster.png)](#indexes)[![Foreign Keys FK_BusinessEntityAddress_BusinessEntity_BusinessEntityID: [Person].[BusinessEntity].BusinessEntityID](../../../../Images/fk.png)](#foreignkeys) | BusinessEntityID | int | 4 | NOT NULL |  | _Primary key. Foreign key to BusinessEntity.BusinessEntityID._ |
| [![Cluster Primary Key PK_BusinessEntityAddress_BusinessEntityID_AddressID_AddressTypeID: BusinessEntityID\AddressID\AddressTypeID](../../../../Images/pkcluster.png)](#indexes)[![Indexes IX_BusinessEntityAddress_AddressID](../../../../Images/Index.png)](#indexes)[![Foreign Keys FK_BusinessEntityAddress_Address_AddressID: [Person].[Address].AddressID](../../../../Images/fk.png)](#foreignkeys) | AddressID | int | 4 | NOT NULL |  | _Primary key. Foreign key to Address.AddressID._ |
| [![Cluster Primary Key PK_BusinessEntityAddress_BusinessEntityID_AddressID_AddressTypeID: BusinessEntityID\AddressID\AddressTypeID](../../../../Images/pkcluster.png)](#indexes)[![Indexes IX_BusinessEntityAddress_AddressTypeID](../../../../Images/Index.png)](#indexes)[![Foreign Keys FK_BusinessEntityAddress_AddressType_AddressTypeID: [Person].[AddressType].AddressTypeID](../../../../Images/fk.png)](#foreignkeys) | AddressTypeID | int | 4 | NOT NULL |  | _Primary key. Foreign key to AddressType.AddressTypeID._ |
| [![Indexes AK_BusinessEntityAddress_rowguid](../../../../Images/Index.png)](#indexes) | rowguid | uniqueidentifier | 16 | NOT NULL | (newid()) | _ROWGUIDCOL number uniquely identifying the record. Used to support a merge replication sample._ |
|  | ModifiedDate | datetime | 8 | NOT NULL | (getdate()) | _Date and time the record was last updated._ |


---

## <a name="#indexes"></a>Indexes

| Key | Name | Key Columns | Unique | Description |
|---|---|---|---|---|
| [![Cluster Primary Key PK_BusinessEntityAddress_BusinessEntityID_AddressID_AddressTypeID: BusinessEntityID\AddressID\AddressTypeID](../../../../Images/pkcluster.png)](#indexes) | PK_BusinessEntityAddress_BusinessEntityID_AddressID_AddressTypeID | BusinessEntityID, AddressID, AddressTypeID | YES | _Primary key (clustered) constraint_ |
|  | AK_BusinessEntityAddress_rowguid | rowguid | YES | _Unique nonclustered index. Used to support replication samples._ |
|  | IX_BusinessEntityAddress_AddressID | AddressID |  | _Nonclustered index._ |
|  | IX_BusinessEntityAddress_AddressTypeID | AddressTypeID |  | _Nonclustered index._ |


---

## <a name="#foreignkeys"></a>Foreign Keys

| Name | Columns | Description |
|---|---|---|
| FK_BusinessEntityAddress_Address_AddressID | AddressID->[Person].[Address].[AddressID] | _Foreign key constraint referencing Address.AddressID._ |
| FK_BusinessEntityAddress_AddressType_AddressTypeID | AddressTypeID->[Person].[AddressType].[AddressTypeID] | _Foreign key constraint referencing AddressType.AddressTypeID._ |
| FK_BusinessEntityAddress_BusinessEntity_BusinessEntityID | BusinessEntityID->[[Person].[BusinessEntity].[BusinessEntityID]](Person_BusinessEntity.md) | _Foreign key constraint referencing BusinessEntity.BusinessEntityID._ |


---

## <a name="#sqlscript"></a>SQL Script

```sql
CREATE TABLE [Person].[BusinessEntityAddress]
(
[BusinessEntityID] [int] NOT NULL,
[AddressID] [int] NOT NULL,
[AddressTypeID] [int] NOT NULL,
[rowguid] [uniqueidentifier] NOT NULL ROWGUIDCOL CONSTRAINT [DF_BusinessEntityAddress_rowguid] DEFAULT (newid()),
[ModifiedDate] [datetime] NOT NULL CONSTRAINT [DF_BusinessEntityAddress_ModifiedDate] DEFAULT (getdate())
) ON [PRIMARY]
GO
ALTER TABLE [Person].[BusinessEntityAddress] ADD CONSTRAINT [PK_BusinessEntityAddress_BusinessEntityID_AddressID_AddressTypeID] PRIMARY KEY CLUSTERED ([BusinessEntityID], [AddressID], [AddressTypeID]) ON [PRIMARY]
GO
CREATE NONCLUSTERED INDEX [IX_BusinessEntityAddress_AddressID] ON [Person].[BusinessEntityAddress] ([AddressID]) ON [PRIMARY]
GO
CREATE NONCLUSTERED INDEX [IX_BusinessEntityAddress_AddressTypeID] ON [Person].[BusinessEntityAddress] ([AddressTypeID]) ON [PRIMARY]
GO
CREATE UNIQUE NONCLUSTERED INDEX [AK_BusinessEntityAddress_rowguid] ON [Person].[BusinessEntityAddress] ([rowguid]) ON [PRIMARY]
GO
ALTER TABLE [Person].[BusinessEntityAddress] ADD CONSTRAINT [FK_BusinessEntityAddress_Address_AddressID] FOREIGN KEY ([AddressID]) REFERENCES [Person].[Address] ([AddressID])
GO
ALTER TABLE [Person].[BusinessEntityAddress] ADD CONSTRAINT [FK_BusinessEntityAddress_AddressType_AddressTypeID] FOREIGN KEY ([AddressTypeID]) REFERENCES [Person].[AddressType] ([AddressTypeID])
GO
ALTER TABLE [Person].[BusinessEntityAddress] ADD CONSTRAINT [FK_BusinessEntityAddress_BusinessEntity_BusinessEntityID] FOREIGN KEY ([BusinessEntityID]) REFERENCES [Person].[BusinessEntity] ([BusinessEntityID])
GO
EXEC sp_addextendedproperty N'MS_Description', N'Cross-reference table mapping customers, vendors, and employees to their addresses.', 'SCHEMA', N'Person', 'TABLE', N'BusinessEntityAddress', NULL, NULL
GO
EXEC sp_addextendedproperty N'MS_Description', N'Primary key. Foreign key to Address.AddressID.', 'SCHEMA', N'Person', 'TABLE', N'BusinessEntityAddress', 'COLUMN', N'AddressID'
GO
EXEC sp_addextendedproperty N'MS_Description', N'Primary key. Foreign key to AddressType.AddressTypeID.', 'SCHEMA', N'Person', 'TABLE', N'BusinessEntityAddress', 'COLUMN', N'AddressTypeID'
GO
EXEC sp_addextendedproperty N'MS_Description', N'Primary key. Foreign key to BusinessEntity.BusinessEntityID.', 'SCHEMA', N'Person', 'TABLE', N'BusinessEntityAddress', 'COLUMN', N'BusinessEntityID'
GO
EXEC sp_addextendedproperty N'MS_Description', N'Date and time the record was last updated.', 'SCHEMA', N'Person', 'TABLE', N'BusinessEntityAddress', 'COLUMN', N'ModifiedDate'
GO
EXEC sp_addextendedproperty N'MS_Description', N'ROWGUIDCOL number uniquely identifying the record. Used to support a merge replication sample.', 'SCHEMA', N'Person', 'TABLE', N'BusinessEntityAddress', 'COLUMN', N'rowguid'
GO
EXEC sp_addextendedproperty N'MS_Description', N'Default constraint value of GETDATE()', 'SCHEMA', N'Person', 'TABLE', N'BusinessEntityAddress', 'CONSTRAINT', N'DF_BusinessEntityAddress_ModifiedDate'
GO
EXEC sp_addextendedproperty N'MS_Description', N'Default constraint value of NEWID()', 'SCHEMA', N'Person', 'TABLE', N'BusinessEntityAddress', 'CONSTRAINT', N'DF_BusinessEntityAddress_rowguid'
GO
EXEC sp_addextendedproperty N'MS_Description', N'Foreign key constraint referencing Address.AddressID.', 'SCHEMA', N'Person', 'TABLE', N'BusinessEntityAddress', 'CONSTRAINT', N'FK_BusinessEntityAddress_Address_AddressID'
GO
EXEC sp_addextendedproperty N'MS_Description', N'Foreign key constraint referencing AddressType.AddressTypeID.', 'SCHEMA', N'Person', 'TABLE', N'BusinessEntityAddress', 'CONSTRAINT', N'FK_BusinessEntityAddress_AddressType_AddressTypeID'
GO
EXEC sp_addextendedproperty N'MS_Description', N'Foreign key constraint referencing BusinessEntity.BusinessEntityID.', 'SCHEMA', N'Person', 'TABLE', N'BusinessEntityAddress', 'CONSTRAINT', N'FK_BusinessEntityAddress_BusinessEntity_BusinessEntityID'
GO
EXEC sp_addextendedproperty N'MS_Description', N'Primary key (clustered) constraint', 'SCHEMA', N'Person', 'TABLE', N'BusinessEntityAddress', 'CONSTRAINT', N'PK_BusinessEntityAddress_BusinessEntityID_AddressID_AddressTypeID'
GO
EXEC sp_addextendedproperty N'MS_Description', N'Unique nonclustered index. Used to support replication samples.', 'SCHEMA', N'Person', 'TABLE', N'BusinessEntityAddress', 'INDEX', N'AK_BusinessEntityAddress_rowguid'
GO
EXEC sp_addextendedproperty N'MS_Description', N'Nonclustered index.', 'SCHEMA', N'Person', 'TABLE', N'BusinessEntityAddress', 'INDEX', N'IX_BusinessEntityAddress_AddressID'
GO
EXEC sp_addextendedproperty N'MS_Description', N'Nonclustered index.', 'SCHEMA', N'Person', 'TABLE', N'BusinessEntityAddress', 'INDEX', N'IX_BusinessEntityAddress_AddressTypeID'
GO
EXEC sp_addextendedproperty N'MS_Description', N'Clustered index created by a primary key constraint.', 'SCHEMA', N'Person', 'TABLE', N'BusinessEntityAddress', 'INDEX', N'PK_BusinessEntityAddress_BusinessEntityID_AddressID_AddressTypeID'
GO

```


---

## <a name="#uses"></a>Uses

* [Person].[Address]
* [Person].[AddressType]
* [[Person].[BusinessEntity]](Person_BusinessEntity.md)
* [Person]


---

## <a name="#usedby"></a>Used By

* [[HumanResources].[vEmployee]](../Views/HumanResources_vEmployee.md)
* [Purchasing].[vVendorWithAddresses]
* [Sales].[vIndividualCustomer]
* [Sales].[vSalesPerson]
* [Sales].[vStoreWithAddresses]


---

###### Author:  Smith, JC

###### Copyright 2024 - All Rights Reserved

###### Created: Thursday, July 11, 2024 1:50:21 PM

