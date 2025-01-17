#### 

[Project](../../../../index.md) > [WI-SANDBOX-ITDI](../../../index.md) > [User databases](../../index.md) > [AdventureWorks2019](../index.md) > [Tables](Tables.md) > Person.BusinessEntity

# ![Tables](../../../../Images/Table32.png) [Person].[BusinessEntity]

---

## <a name="#description"></a>MS_Description

Source of the ID that connects vendors, customers, and employees with address and contact information.

## <a name="#properties"></a>Properties

| Property | Value |
|---|---|
| Row Count (~) | 20777 |
| Created | 12:07:29 PM Monday, May 8, 2023 |
| Last Modified | 12:07:39 PM Monday, May 8, 2023 |


---

## <a name="#columns"></a>Columns

| Key | Name | Data Type | Max Length (Bytes) | Nullability | Identity | Identity Replication | Default | Description |
|---|---|---|---|---|---|---|---|---|
| [![Cluster Primary Key PK_BusinessEntity_BusinessEntityID: BusinessEntityID](../../../../Images/pkcluster.png)](#indexes) | BusinessEntityID | int | 4 | NOT NULL | 1 - 1 | NO |  | _Primary key for all customers, vendors, and employees._ |
| [![Indexes AK_BusinessEntity_rowguid](../../../../Images/Index.png)](#indexes) | rowguid | uniqueidentifier | 16 | NOT NULL |  |  | (newid()) | _ROWGUIDCOL number uniquely identifying the record. Used to support a merge replication sample._ |
|  | ModifiedDate | datetime | 8 | NOT NULL |  |  | (getdate()) | _Date and time the record was last updated._ |


---

## <a name="#indexes"></a>Indexes

| Key | Name | Key Columns | Unique | Description |
|---|---|---|---|---|
| [![Cluster Primary Key PK_BusinessEntity_BusinessEntityID: BusinessEntityID](../../../../Images/pkcluster.png)](#indexes) | PK_BusinessEntity_BusinessEntityID | BusinessEntityID | YES | _Primary key (clustered) constraint_ |
|  | AK_BusinessEntity_rowguid | rowguid | YES | _Unique nonclustered index. Used to support replication samples._ |


---

## <a name="#sqlscript"></a>SQL Script

```sql
CREATE TABLE [Person].[BusinessEntity]
(
[BusinessEntityID] [int] NOT NULL IDENTITY(1, 1) NOT FOR REPLICATION,
[rowguid] [uniqueidentifier] NOT NULL ROWGUIDCOL CONSTRAINT [DF_BusinessEntity_rowguid] DEFAULT (newid()),
[ModifiedDate] [datetime] NOT NULL CONSTRAINT [DF_BusinessEntity_ModifiedDate] DEFAULT (getdate())
) ON [PRIMARY]
GO
ALTER TABLE [Person].[BusinessEntity] ADD CONSTRAINT [PK_BusinessEntity_BusinessEntityID] PRIMARY KEY CLUSTERED ([BusinessEntityID]) ON [PRIMARY]
GO
CREATE UNIQUE NONCLUSTERED INDEX [AK_BusinessEntity_rowguid] ON [Person].[BusinessEntity] ([rowguid]) ON [PRIMARY]
GO
EXEC sp_addextendedproperty N'MS_Description', N'Source of the ID that connects vendors, customers, and employees with address and contact information.', 'SCHEMA', N'Person', 'TABLE', N'BusinessEntity', NULL, NULL
GO
EXEC sp_addextendedproperty N'MS_Description', N'Primary key for all customers, vendors, and employees.', 'SCHEMA', N'Person', 'TABLE', N'BusinessEntity', 'COLUMN', N'BusinessEntityID'
GO
EXEC sp_addextendedproperty N'MS_Description', N'Date and time the record was last updated.', 'SCHEMA', N'Person', 'TABLE', N'BusinessEntity', 'COLUMN', N'ModifiedDate'
GO
EXEC sp_addextendedproperty N'MS_Description', N'ROWGUIDCOL number uniquely identifying the record. Used to support a merge replication sample.', 'SCHEMA', N'Person', 'TABLE', N'BusinessEntity', 'COLUMN', N'rowguid'
GO
EXEC sp_addextendedproperty N'MS_Description', N'Default constraint value of GETDATE()', 'SCHEMA', N'Person', 'TABLE', N'BusinessEntity', 'CONSTRAINT', N'DF_BusinessEntity_ModifiedDate'
GO
EXEC sp_addextendedproperty N'MS_Description', N'Default constraint value of NEWID()', 'SCHEMA', N'Person', 'TABLE', N'BusinessEntity', 'CONSTRAINT', N'DF_BusinessEntity_rowguid'
GO
EXEC sp_addextendedproperty N'MS_Description', N'Primary key (clustered) constraint', 'SCHEMA', N'Person', 'TABLE', N'BusinessEntity', 'CONSTRAINT', N'PK_BusinessEntity_BusinessEntityID'
GO
EXEC sp_addextendedproperty N'MS_Description', N'Unique nonclustered index. Used to support replication samples.', 'SCHEMA', N'Person', 'TABLE', N'BusinessEntity', 'INDEX', N'AK_BusinessEntity_rowguid'
GO
EXEC sp_addextendedproperty N'MS_Description', N'Clustered index created by a primary key constraint.', 'SCHEMA', N'Person', 'TABLE', N'BusinessEntity', 'INDEX', N'PK_BusinessEntity_BusinessEntityID'
GO

```


---

## <a name="#uses"></a>Uses

* [Person]


---

## <a name="#usedby"></a>Used By

* [[Person].[BusinessEntityAddress]](Person_BusinessEntityAddress.md)
* [[Person].[BusinessEntityContact]](Person_BusinessEntityContact.md)
* [[Person].[Person]](Person_Person.md)
* [Purchasing].[Vendor]
* [Sales].[Store]


---

###### Author:  Smith, JC

###### Copyright 2024 - All Rights Reserved

###### Created: Thursday, July 11, 2024 1:50:21 PM

