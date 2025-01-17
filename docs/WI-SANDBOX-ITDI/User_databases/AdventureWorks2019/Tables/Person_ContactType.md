#### 

[Project](../../../../index.md) > [WI-SANDBOX-ITDI](../../../index.md) > [User databases](../../index.md) > [AdventureWorks2019](../index.md) > [Tables](Tables.md) > Person.ContactType

# ![Tables](../../../../Images/Table32.png) [Person].[ContactType]

---

## <a name="#description"></a>MS_Description

Lookup table containing the types of business entity contacts.

## <a name="#properties"></a>Properties

| Property | Value |
|---|---|
| Collation | SQL_Latin1_General_CP1_CI_AS |
| Row Count (~) | 20 |
| Created | 12:07:29 PM Monday, May 8, 2023 |
| Last Modified | 12:07:38 PM Monday, May 8, 2023 |


---

## <a name="#columns"></a>Columns

| Key | Name | Data Type | Max Length (Bytes) | Nullability | Identity | Default | Description |
|---|---|---|---|---|---|---|---|
| [![Cluster Primary Key PK_ContactType_ContactTypeID: ContactTypeID](../../../../Images/pkcluster.png)](#indexes) | ContactTypeID | int | 4 | NOT NULL | 1 - 1 |  | _Primary key for ContactType records._ |
| [![Indexes AK_ContactType_Name](../../../../Images/Index.png)](#indexes) | Name | [dbo].[Name] | 100 | NOT NULL |  |  | _Contact type description._ |
|  | ModifiedDate | datetime | 8 | NOT NULL |  | (getdate()) | _Date and time the record was last updated._ |


---

## <a name="#indexes"></a>Indexes

| Key | Name | Key Columns | Unique | Description |
|---|---|---|---|---|
| [![Cluster Primary Key PK_ContactType_ContactTypeID: ContactTypeID](../../../../Images/pkcluster.png)](#indexes) | PK_ContactType_ContactTypeID | ContactTypeID | YES | _Primary key (clustered) constraint_ |
|  | AK_ContactType_Name | Name | YES | _Unique nonclustered index._ |


---

## <a name="#sqlscript"></a>SQL Script

```sql
CREATE TABLE [Person].[ContactType]
(
[ContactTypeID] [int] NOT NULL IDENTITY(1, 1),
[Name] [dbo].[Name] NOT NULL,
[ModifiedDate] [datetime] NOT NULL CONSTRAINT [DF_ContactType_ModifiedDate] DEFAULT (getdate())
) ON [PRIMARY]
GO
ALTER TABLE [Person].[ContactType] ADD CONSTRAINT [PK_ContactType_ContactTypeID] PRIMARY KEY CLUSTERED ([ContactTypeID]) ON [PRIMARY]
GO
CREATE UNIQUE NONCLUSTERED INDEX [AK_ContactType_Name] ON [Person].[ContactType] ([Name]) ON [PRIMARY]
GO
EXEC sp_addextendedproperty N'MS_Description', N'Lookup table containing the types of business entity contacts.', 'SCHEMA', N'Person', 'TABLE', N'ContactType', NULL, NULL
GO
EXEC sp_addextendedproperty N'MS_Description', N'Primary key for ContactType records.', 'SCHEMA', N'Person', 'TABLE', N'ContactType', 'COLUMN', N'ContactTypeID'
GO
EXEC sp_addextendedproperty N'MS_Description', N'Date and time the record was last updated.', 'SCHEMA', N'Person', 'TABLE', N'ContactType', 'COLUMN', N'ModifiedDate'
GO
EXEC sp_addextendedproperty N'MS_Description', N'Contact type description.', 'SCHEMA', N'Person', 'TABLE', N'ContactType', 'COLUMN', N'Name'
GO
EXEC sp_addextendedproperty N'MS_Description', N'Default constraint value of GETDATE()', 'SCHEMA', N'Person', 'TABLE', N'ContactType', 'CONSTRAINT', N'DF_ContactType_ModifiedDate'
GO
EXEC sp_addextendedproperty N'MS_Description', N'Primary key (clustered) constraint', 'SCHEMA', N'Person', 'TABLE', N'ContactType', 'CONSTRAINT', N'PK_ContactType_ContactTypeID'
GO
EXEC sp_addextendedproperty N'MS_Description', N'Unique nonclustered index.', 'SCHEMA', N'Person', 'TABLE', N'ContactType', 'INDEX', N'AK_ContactType_Name'
GO
EXEC sp_addextendedproperty N'MS_Description', N'Clustered index created by a primary key constraint.', 'SCHEMA', N'Person', 'TABLE', N'ContactType', 'INDEX', N'PK_ContactType_ContactTypeID'
GO

```


---

## <a name="#uses"></a>Uses

* [dbo].[Name]
* [Person]


---

## <a name="#usedby"></a>Used By

* [[Person].[BusinessEntityContact]](Person_BusinessEntityContact.md)
* [dbo].[ufnGetContactInformation]
* [Purchasing].[vVendorWithContacts]
* [Sales].[vStoreWithContacts]


---

###### Author:  Smith, JC

###### Copyright 2024 - All Rights Reserved

###### Created: Thursday, July 11, 2024 1:50:21 PM

