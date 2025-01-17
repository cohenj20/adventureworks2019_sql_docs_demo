#### 

[Project](../../../../index.md) > [WI-SANDBOX-ITDI](../../../index.md) > [User databases](../../index.md) > [AdventureWorks2019](../index.md) > [Tables](Tables.md) > Person.EmailAddress

# ![Tables](../../../../Images/Table32.png) [Person].[EmailAddress]

---

## <a name="#description"></a>MS_Description

Where to send a person email.

## <a name="#properties"></a>Properties

| Property | Value |
|---|---|
| Collation | SQL_Latin1_General_CP1_CI_AS |
| Row Count (~) | 19972 |
| Created | 12:07:29 PM Monday, May 8, 2023 |
| Last Modified | 12:07:38 PM Monday, May 8, 2023 |


---

## <a name="#columns"></a>Columns

| Key | Name | Data Type | Max Length (Bytes) | Nullability | Identity | Default | Description |
|---|---|---|---|---|---|---|---|
| [![Cluster Primary Key PK_EmailAddress_BusinessEntityID_EmailAddressID: BusinessEntityID\EmailAddressID](../../../../Images/pkcluster.png)](#indexes)[![Foreign Keys FK_EmailAddress_Person_BusinessEntityID: [Person].[Person].BusinessEntityID](../../../../Images/fk.png)](#foreignkeys) | BusinessEntityID | int | 4 | NOT NULL |  |  | _Primary key. Person associated with this email address.  Foreign key to Person.BusinessEntityID_ |
| [![Cluster Primary Key PK_EmailAddress_BusinessEntityID_EmailAddressID: BusinessEntityID\EmailAddressID](../../../../Images/pkcluster.png)](#indexes) | EmailAddressID | int | 4 | NOT NULL | 1 - 1 |  | _Primary key. ID of this email address._ |
| [![Indexes IX_EmailAddress_EmailAddress](../../../../Images/Index.png)](#indexes) | EmailAddress | nvarchar(50) | 100 | NULL allowed |  |  | _E-mail address for the person._ |
|  | rowguid | uniqueidentifier | 16 | NOT NULL |  | (newid()) | _ROWGUIDCOL number uniquely identifying the record. Used to support a merge replication sample._ |
|  | ModifiedDate | datetime | 8 | NOT NULL |  | (getdate()) | _Date and time the record was last updated._ |


---

## <a name="#indexes"></a>Indexes

| Key | Name | Key Columns | Unique | Description |
|---|---|---|---|---|
| [![Cluster Primary Key PK_EmailAddress_BusinessEntityID_EmailAddressID: BusinessEntityID\EmailAddressID](../../../../Images/pkcluster.png)](#indexes) | PK_EmailAddress_BusinessEntityID_EmailAddressID | BusinessEntityID, EmailAddressID | YES | _Primary key (clustered) constraint_ |
|  | IX_EmailAddress_EmailAddress | EmailAddress |  | _Nonclustered index._ |


---

## <a name="#foreignkeys"></a>Foreign Keys

| Name | Columns | Description |
|---|---|---|
| FK_EmailAddress_Person_BusinessEntityID | BusinessEntityID->[[Person].[Person].[BusinessEntityID]](Person_Person.md) | _Foreign key constraint referencing Person.BusinessEntityID._ |


---

## <a name="#sqlscript"></a>SQL Script

```sql
CREATE TABLE [Person].[EmailAddress]
(
[BusinessEntityID] [int] NOT NULL,
[EmailAddressID] [int] NOT NULL IDENTITY(1, 1),
[EmailAddress] [nvarchar] (50) COLLATE SQL_Latin1_General_CP1_CI_AS NULL,
[rowguid] [uniqueidentifier] NOT NULL ROWGUIDCOL CONSTRAINT [DF_EmailAddress_rowguid] DEFAULT (newid()),
[ModifiedDate] [datetime] NOT NULL CONSTRAINT [DF_EmailAddress_ModifiedDate] DEFAULT (getdate())
) ON [PRIMARY]
GO
ALTER TABLE [Person].[EmailAddress] ADD CONSTRAINT [PK_EmailAddress_BusinessEntityID_EmailAddressID] PRIMARY KEY CLUSTERED ([BusinessEntityID], [EmailAddressID]) ON [PRIMARY]
GO
CREATE NONCLUSTERED INDEX [IX_EmailAddress_EmailAddress] ON [Person].[EmailAddress] ([EmailAddress]) ON [PRIMARY]
GO
ALTER TABLE [Person].[EmailAddress] ADD CONSTRAINT [FK_EmailAddress_Person_BusinessEntityID] FOREIGN KEY ([BusinessEntityID]) REFERENCES [Person].[Person] ([BusinessEntityID])
GO
EXEC sp_addextendedproperty N'MS_Description', N'Where to send a person email.', 'SCHEMA', N'Person', 'TABLE', N'EmailAddress', NULL, NULL
GO
EXEC sp_addextendedproperty N'MS_Description', N'Primary key. Person associated with this email address.  Foreign key to Person.BusinessEntityID', 'SCHEMA', N'Person', 'TABLE', N'EmailAddress', 'COLUMN', N'BusinessEntityID'
GO
EXEC sp_addextendedproperty N'MS_Description', N'E-mail address for the person.', 'SCHEMA', N'Person', 'TABLE', N'EmailAddress', 'COLUMN', N'EmailAddress'
GO
EXEC sp_addextendedproperty N'MS_Description', N'Primary key. ID of this email address.', 'SCHEMA', N'Person', 'TABLE', N'EmailAddress', 'COLUMN', N'EmailAddressID'
GO
EXEC sp_addextendedproperty N'MS_Description', N'Date and time the record was last updated.', 'SCHEMA', N'Person', 'TABLE', N'EmailAddress', 'COLUMN', N'ModifiedDate'
GO
EXEC sp_addextendedproperty N'MS_Description', N'ROWGUIDCOL number uniquely identifying the record. Used to support a merge replication sample.', 'SCHEMA', N'Person', 'TABLE', N'EmailAddress', 'COLUMN', N'rowguid'
GO
EXEC sp_addextendedproperty N'MS_Description', N'Default constraint value of GETDATE()', 'SCHEMA', N'Person', 'TABLE', N'EmailAddress', 'CONSTRAINT', N'DF_EmailAddress_ModifiedDate'
GO
EXEC sp_addextendedproperty N'MS_Description', N'Default constraint value of NEWID()', 'SCHEMA', N'Person', 'TABLE', N'EmailAddress', 'CONSTRAINT', N'DF_EmailAddress_rowguid'
GO
EXEC sp_addextendedproperty N'MS_Description', N'Foreign key constraint referencing Person.BusinessEntityID.', 'SCHEMA', N'Person', 'TABLE', N'EmailAddress', 'CONSTRAINT', N'FK_EmailAddress_Person_BusinessEntityID'
GO
EXEC sp_addextendedproperty N'MS_Description', N'Primary key (clustered) constraint', 'SCHEMA', N'Person', 'TABLE', N'EmailAddress', 'CONSTRAINT', N'PK_EmailAddress_BusinessEntityID_EmailAddressID'
GO
EXEC sp_addextendedproperty N'MS_Description', N'Nonclustered index.', 'SCHEMA', N'Person', 'TABLE', N'EmailAddress', 'INDEX', N'IX_EmailAddress_EmailAddress'
GO
EXEC sp_addextendedproperty N'MS_Description', N'Clustered index created by a primary key constraint.', 'SCHEMA', N'Person', 'TABLE', N'EmailAddress', 'INDEX', N'PK_EmailAddress_BusinessEntityID_EmailAddressID'
GO

```


---

## <a name="#uses"></a>Uses

* [[Person].[Person]](Person_Person.md)
* [Person]


---

## <a name="#usedby"></a>Used By

* [[HumanResources].[vEmployee]](../Views/HumanResources_vEmployee.md)
* [Purchasing].[vVendorWithContacts]
* [Sales].[vIndividualCustomer]
* [Sales].[vSalesPerson]
* [Sales].[vStoreWithContacts]


---

###### Author:  Smith, JC

###### Copyright 2024 - All Rights Reserved

###### Created: Thursday, July 11, 2024 1:50:21 PM

