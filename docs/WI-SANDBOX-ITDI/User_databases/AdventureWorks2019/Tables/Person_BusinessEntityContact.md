#### 

[Project](../../../../index.md) > [WI-SANDBOX-ITDI](../../../index.md) > [User databases](../../index.md) > [AdventureWorks2019](../index.md) > [Tables](Tables.md) > Person.BusinessEntityContact

# ![Tables](../../../../Images/Table32.png) [Person].[BusinessEntityContact]

---

## <a name="#description"></a>MS_Description

Cross-reference table mapping stores, vendors, and employees to people

## <a name="#properties"></a>Properties

| Property | Value |
|---|---|
| Row Count (~) | 909 |
| Created | 12:07:29 PM Monday, May 8, 2023 |
| Last Modified | 12:07:38 PM Monday, May 8, 2023 |


---

## <a name="#columns"></a>Columns

| Key | Name | Data Type | Max Length (Bytes) | Nullability | Default | Description |
|---|---|---|---|---|---|---|
| [![Cluster Primary Key PK_BusinessEntityContact_BusinessEntityID_PersonID_ContactTypeID: BusinessEntityID\PersonID\ContactTypeID](../../../../Images/pkcluster.png)](#indexes)[![Foreign Keys FK_BusinessEntityContact_BusinessEntity_BusinessEntityID: [Person].[BusinessEntity].BusinessEntityID](../../../../Images/fk.png)](#foreignkeys) | BusinessEntityID | int | 4 | NOT NULL |  | _Primary key. Foreign key to BusinessEntity.BusinessEntityID._ |
| [![Cluster Primary Key PK_BusinessEntityContact_BusinessEntityID_PersonID_ContactTypeID: BusinessEntityID\PersonID\ContactTypeID](../../../../Images/pkcluster.png)](#indexes)[![Indexes IX_BusinessEntityContact_PersonID](../../../../Images/Index.png)](#indexes)[![Foreign Keys FK_BusinessEntityContact_Person_PersonID: [Person].[Person].PersonID](../../../../Images/fk.png)](#foreignkeys) | PersonID | int | 4 | NOT NULL |  | _Primary key. Foreign key to Person.BusinessEntityID._ |
| [![Cluster Primary Key PK_BusinessEntityContact_BusinessEntityID_PersonID_ContactTypeID: BusinessEntityID\PersonID\ContactTypeID](../../../../Images/pkcluster.png)](#indexes)[![Indexes IX_BusinessEntityContact_ContactTypeID](../../../../Images/Index.png)](#indexes)[![Foreign Keys FK_BusinessEntityContact_ContactType_ContactTypeID: [Person].[ContactType].ContactTypeID](../../../../Images/fk.png)](#foreignkeys) | ContactTypeID | int | 4 | NOT NULL |  | _Primary key.  Foreign key to ContactType.ContactTypeID._ |
| [![Indexes AK_BusinessEntityContact_rowguid](../../../../Images/Index.png)](#indexes) | rowguid | uniqueidentifier | 16 | NOT NULL | (newid()) | _ROWGUIDCOL number uniquely identifying the record. Used to support a merge replication sample._ |
|  | ModifiedDate | datetime | 8 | NOT NULL | (getdate()) | _Date and time the record was last updated._ |


---

## <a name="#indexes"></a>Indexes

| Key | Name | Key Columns | Unique | Description |
|---|---|---|---|---|
| [![Cluster Primary Key PK_BusinessEntityContact_BusinessEntityID_PersonID_ContactTypeID: BusinessEntityID\PersonID\ContactTypeID](../../../../Images/pkcluster.png)](#indexes) | PK_BusinessEntityContact_BusinessEntityID_PersonID_ContactTypeID | BusinessEntityID, PersonID, ContactTypeID | YES | _Primary key (clustered) constraint_ |
|  | AK_BusinessEntityContact_rowguid | rowguid | YES | _Unique nonclustered index. Used to support replication samples._ |
|  | IX_BusinessEntityContact_ContactTypeID | ContactTypeID |  | _Nonclustered index._ |
|  | IX_BusinessEntityContact_PersonID | PersonID |  | _Nonclustered index._ |


---

## <a name="#foreignkeys"></a>Foreign Keys

| Name | Columns | Description |
|---|---|---|
| FK_BusinessEntityContact_BusinessEntity_BusinessEntityID | BusinessEntityID->[[Person].[BusinessEntity].[BusinessEntityID]](Person_BusinessEntity.md) | _Foreign key constraint referencing BusinessEntity.BusinessEntityID._ |
| FK_BusinessEntityContact_ContactType_ContactTypeID | ContactTypeID->[[Person].[ContactType].[ContactTypeID]](Person_ContactType.md) | _Foreign key constraint referencing ContactType.ContactTypeID._ |
| FK_BusinessEntityContact_Person_PersonID | PersonID->[[Person].[Person].[BusinessEntityID]](Person_Person.md) | _Foreign key constraint referencing Person.BusinessEntityID._ |


---

## <a name="#sqlscript"></a>SQL Script

```sql
CREATE TABLE [Person].[BusinessEntityContact]
(
[BusinessEntityID] [int] NOT NULL,
[PersonID] [int] NOT NULL,
[ContactTypeID] [int] NOT NULL,
[rowguid] [uniqueidentifier] NOT NULL ROWGUIDCOL CONSTRAINT [DF_BusinessEntityContact_rowguid] DEFAULT (newid()),
[ModifiedDate] [datetime] NOT NULL CONSTRAINT [DF_BusinessEntityContact_ModifiedDate] DEFAULT (getdate())
) ON [PRIMARY]
GO
ALTER TABLE [Person].[BusinessEntityContact] ADD CONSTRAINT [PK_BusinessEntityContact_BusinessEntityID_PersonID_ContactTypeID] PRIMARY KEY CLUSTERED ([BusinessEntityID], [PersonID], [ContactTypeID]) ON [PRIMARY]
GO
CREATE NONCLUSTERED INDEX [IX_BusinessEntityContact_ContactTypeID] ON [Person].[BusinessEntityContact] ([ContactTypeID]) ON [PRIMARY]
GO
CREATE NONCLUSTERED INDEX [IX_BusinessEntityContact_PersonID] ON [Person].[BusinessEntityContact] ([PersonID]) ON [PRIMARY]
GO
CREATE UNIQUE NONCLUSTERED INDEX [AK_BusinessEntityContact_rowguid] ON [Person].[BusinessEntityContact] ([rowguid]) ON [PRIMARY]
GO
ALTER TABLE [Person].[BusinessEntityContact] ADD CONSTRAINT [FK_BusinessEntityContact_BusinessEntity_BusinessEntityID] FOREIGN KEY ([BusinessEntityID]) REFERENCES [Person].[BusinessEntity] ([BusinessEntityID])
GO
ALTER TABLE [Person].[BusinessEntityContact] ADD CONSTRAINT [FK_BusinessEntityContact_ContactType_ContactTypeID] FOREIGN KEY ([ContactTypeID]) REFERENCES [Person].[ContactType] ([ContactTypeID])
GO
ALTER TABLE [Person].[BusinessEntityContact] ADD CONSTRAINT [FK_BusinessEntityContact_Person_PersonID] FOREIGN KEY ([PersonID]) REFERENCES [Person].[Person] ([BusinessEntityID])
GO
EXEC sp_addextendedproperty N'MS_Description', N'Cross-reference table mapping stores, vendors, and employees to people', 'SCHEMA', N'Person', 'TABLE', N'BusinessEntityContact', NULL, NULL
GO
EXEC sp_addextendedproperty N'MS_Description', N'Primary key. Foreign key to BusinessEntity.BusinessEntityID.', 'SCHEMA', N'Person', 'TABLE', N'BusinessEntityContact', 'COLUMN', N'BusinessEntityID'
GO
EXEC sp_addextendedproperty N'MS_Description', N'Primary key.  Foreign key to ContactType.ContactTypeID.', 'SCHEMA', N'Person', 'TABLE', N'BusinessEntityContact', 'COLUMN', N'ContactTypeID'
GO
EXEC sp_addextendedproperty N'MS_Description', N'Date and time the record was last updated.', 'SCHEMA', N'Person', 'TABLE', N'BusinessEntityContact', 'COLUMN', N'ModifiedDate'
GO
EXEC sp_addextendedproperty N'MS_Description', N'Primary key. Foreign key to Person.BusinessEntityID.', 'SCHEMA', N'Person', 'TABLE', N'BusinessEntityContact', 'COLUMN', N'PersonID'
GO
EXEC sp_addextendedproperty N'MS_Description', N'ROWGUIDCOL number uniquely identifying the record. Used to support a merge replication sample.', 'SCHEMA', N'Person', 'TABLE', N'BusinessEntityContact', 'COLUMN', N'rowguid'
GO
EXEC sp_addextendedproperty N'MS_Description', N'Default constraint value of GETDATE()', 'SCHEMA', N'Person', 'TABLE', N'BusinessEntityContact', 'CONSTRAINT', N'DF_BusinessEntityContact_ModifiedDate'
GO
EXEC sp_addextendedproperty N'MS_Description', N'Default constraint value of NEWID()', 'SCHEMA', N'Person', 'TABLE', N'BusinessEntityContact', 'CONSTRAINT', N'DF_BusinessEntityContact_rowguid'
GO
EXEC sp_addextendedproperty N'MS_Description', N'Foreign key constraint referencing BusinessEntity.BusinessEntityID.', 'SCHEMA', N'Person', 'TABLE', N'BusinessEntityContact', 'CONSTRAINT', N'FK_BusinessEntityContact_BusinessEntity_BusinessEntityID'
GO
EXEC sp_addextendedproperty N'MS_Description', N'Foreign key constraint referencing ContactType.ContactTypeID.', 'SCHEMA', N'Person', 'TABLE', N'BusinessEntityContact', 'CONSTRAINT', N'FK_BusinessEntityContact_ContactType_ContactTypeID'
GO
EXEC sp_addextendedproperty N'MS_Description', N'Foreign key constraint referencing Person.BusinessEntityID.', 'SCHEMA', N'Person', 'TABLE', N'BusinessEntityContact', 'CONSTRAINT', N'FK_BusinessEntityContact_Person_PersonID'
GO
EXEC sp_addextendedproperty N'MS_Description', N'Primary key (clustered) constraint', 'SCHEMA', N'Person', 'TABLE', N'BusinessEntityContact', 'CONSTRAINT', N'PK_BusinessEntityContact_BusinessEntityID_PersonID_ContactTypeID'
GO
EXEC sp_addextendedproperty N'MS_Description', N'Unique nonclustered index. Used to support replication samples.', 'SCHEMA', N'Person', 'TABLE', N'BusinessEntityContact', 'INDEX', N'AK_BusinessEntityContact_rowguid'
GO
EXEC sp_addextendedproperty N'MS_Description', N'Nonclustered index.', 'SCHEMA', N'Person', 'TABLE', N'BusinessEntityContact', 'INDEX', N'IX_BusinessEntityContact_ContactTypeID'
GO
EXEC sp_addextendedproperty N'MS_Description', N'Nonclustered index.', 'SCHEMA', N'Person', 'TABLE', N'BusinessEntityContact', 'INDEX', N'IX_BusinessEntityContact_PersonID'
GO
EXEC sp_addextendedproperty N'MS_Description', N'Clustered index created by a primary key constraint.', 'SCHEMA', N'Person', 'TABLE', N'BusinessEntityContact', 'INDEX', N'PK_BusinessEntityContact_BusinessEntityID_PersonID_ContactTypeID'
GO

```


---

## <a name="#uses"></a>Uses

* [[Person].[BusinessEntity]](Person_BusinessEntity.md)
* [[Person].[ContactType]](Person_ContactType.md)
* [[Person].[Person]](Person_Person.md)
* [Person]


---

## <a name="#usedby"></a>Used By

* [dbo].[ufnGetContactInformation]
* [Purchasing].[vVendorWithContacts]
* [Sales].[vStoreWithContacts]


---

###### Author:  Smith, JC

###### Copyright 2024 - All Rights Reserved

###### Created: Thursday, July 11, 2024 10:33:41 AM

