#### 

[Project](../../../../index.md) > [WI-SANDBOX-ITDI](../../../index.md) > [User databases](../../index.md) > [AdventureWorks2019](../index.md) > [Views](Views.md) > HumanResources.vEmployee

# ![Views](../../../../Images/View32.png) [HumanResources].[vEmployee]

---

## <a name="#description"></a>MS_Description

Employee names and addresses.

## <a name="#properties"></a>Properties

| Property | Value |
|---|---|
| Collation | SQL_Latin1_General_CP1_CI_AS |
| ANSI Nulls On | YES |
| Quoted Identifier On | YES |
| Created | 12:07:39 PM Monday, May 8, 2023 |
| Last Modified | 11:44:23 AM Tuesday, February 27, 2024 |


---

## <a name="#columns"></a>Columns

| Name | Data Type | Max Length (Bytes) | Description |
|---|---|---|---|
| BusinessEntityID | int | 4 | _The unique identifier for a business entity._ |
| Title | nvarchar(8) | 16 | _The title for a employee. ['Mr.', 'Mrs.', 'Sr.', 'Jr.', 'Sra.']_ |
| FirstName | [dbo].[Name] | 100 | _The employee's first name._ |
| MiddleName | [dbo].[Name] | 100 | _The employee's middle name._ |
| LastName | [dbo].[Name] | 100 | _The employee's middle name._ |
| Suffix | nvarchar(10) | 20 | _The suffix for a employee._ |
| JobTitle | nvarchar(50) | 100 | _The job title of an employee._ |
| PhoneNumber | [dbo].[Phone] | 50 | _An employee's phone number._ |
| PhoneNumberType | [dbo].[Name] | 100 | _The phone number type._ |
| EmailAddress | nvarchar(50) | 100 | _Employee's work email address._ |
| EmailPromotion | int | 4 | _Binary value for whether the employee receives an email promotion._ |
| AddressLine1 | nvarchar(60) | 120 | _Number and street name part of address._ |
| AddressLine2 | nvarchar(60) | 120 | _Unit number/ PO part of address._ |
| City | nvarchar(30) | 60 | _City of employee._ |
| StateProvinceName | [dbo].[Name] | 100 | _State of employee._ |
| PostalCode | nvarchar(15) | 30 | _Postal code._ |
| CountryRegionName | [dbo].[Name] | 100 | _Country name of address._ |
| AdditionalContactInfo | xml | max | _Semi structured additional contact info._ |


---

## <a name="#sqlscript"></a>SQL Script

```sql

CREATE VIEW [HumanResources].[vEmployee] 
AS 
SELECT 
    e.[BusinessEntityID]
    ,p.[Title]
    ,p.[FirstName]
    ,p.[MiddleName]
    ,p.[LastName]
    ,p.[Suffix]
    ,e.[JobTitle]  
    ,pp.[PhoneNumber]
    ,pnt.[Name] AS [PhoneNumberType]
    ,ea.[EmailAddress]
    ,p.[EmailPromotion]
    ,a.[AddressLine1]
    ,a.[AddressLine2]
    ,a.[City]
    ,sp.[Name] AS [StateProvinceName] 
    ,a.[PostalCode]
    ,cr.[Name] AS [CountryRegionName] 
    ,p.[AdditionalContactInfo]
FROM [HumanResources].[Employee] e
	INNER JOIN [Person].[Person] p
	ON p.[BusinessEntityID] = e.[BusinessEntityID]
    INNER JOIN [Person].[BusinessEntityAddress] bea 
    ON bea.[BusinessEntityID] = e.[BusinessEntityID] 
    INNER JOIN [Person].[Address] a 
    ON a.[AddressID] = bea.[AddressID]
    INNER JOIN [Person].[StateProvince] sp 
    ON sp.[StateProvinceID] = a.[StateProvinceID]
    INNER JOIN [Person].[CountryRegion] cr 
    ON cr.[CountryRegionCode] = sp.[CountryRegionCode]
    LEFT OUTER JOIN [Person].[PersonPhone] pp
    ON pp.BusinessEntityID = p.[BusinessEntityID]
    LEFT OUTER JOIN [Person].[PhoneNumberType] pnt
    ON pp.[PhoneNumberTypeID] = pnt.[PhoneNumberTypeID]
    LEFT OUTER JOIN [Person].[EmailAddress] ea
    ON p.[BusinessEntityID] = ea.[BusinessEntityID];
GO
EXEC sp_addextendedproperty N'MS_Description', N'Employee names and addresses.', 'SCHEMA', N'HumanResources', 'VIEW', N'vEmployee', NULL, NULL
GO
EXEC sp_addextendedproperty N'MS_Description', N'Semi structured additional contact info.', 'SCHEMA', N'HumanResources', 'VIEW', N'vEmployee', 'COLUMN', N'AdditionalContactInfo'
GO
EXEC sp_addextendedproperty N'MS_Description', N'Number and street name part of address.', 'SCHEMA', N'HumanResources', 'VIEW', N'vEmployee', 'COLUMN', N'AddressLine1'
GO
EXEC sp_addextendedproperty N'MS_Description', N'Unit number/ PO part of address.', 'SCHEMA', N'HumanResources', 'VIEW', N'vEmployee', 'COLUMN', N'AddressLine2'
GO
EXEC sp_addextendedproperty N'MS_Description', N'The unique identifier for a business entity.', 'SCHEMA', N'HumanResources', 'VIEW', N'vEmployee', 'COLUMN', N'BusinessEntityID'
GO
EXEC sp_addextendedproperty N'MS_Description', N'City of employee.', 'SCHEMA', N'HumanResources', 'VIEW', N'vEmployee', 'COLUMN', N'City'
GO
EXEC sp_addextendedproperty N'MS_Description', N'Country name of address.', 'SCHEMA', N'HumanResources', 'VIEW', N'vEmployee', 'COLUMN', N'CountryRegionName'
GO
EXEC sp_addextendedproperty N'MS_Description', N'Employee''s work email address.', 'SCHEMA', N'HumanResources', 'VIEW', N'vEmployee', 'COLUMN', N'EmailAddress'
GO
EXEC sp_addextendedproperty N'MS_Description', N'Binary value for whether the employee receives an email promotion.', 'SCHEMA', N'HumanResources', 'VIEW', N'vEmployee', 'COLUMN', N'EmailPromotion'
GO
EXEC sp_addextendedproperty N'MS_Description', N'The employee''s first name.', 'SCHEMA', N'HumanResources', 'VIEW', N'vEmployee', 'COLUMN', N'FirstName'
GO
EXEC sp_addextendedproperty N'MS_Description', N'The job title of an employee.', 'SCHEMA', N'HumanResources', 'VIEW', N'vEmployee', 'COLUMN', N'JobTitle'
GO
EXEC sp_addextendedproperty N'MS_Description', N'The employee''s middle name.', 'SCHEMA', N'HumanResources', 'VIEW', N'vEmployee', 'COLUMN', N'LastName'
GO
EXEC sp_addextendedproperty N'MS_Description', N'The employee''s middle name.', 'SCHEMA', N'HumanResources', 'VIEW', N'vEmployee', 'COLUMN', N'MiddleName'
GO
EXEC sp_addextendedproperty N'MS_Description', N'An employee''s phone number.', 'SCHEMA', N'HumanResources', 'VIEW', N'vEmployee', 'COLUMN', N'PhoneNumber'
GO
EXEC sp_addextendedproperty N'MS_Description', N'The phone number type.', 'SCHEMA', N'HumanResources', 'VIEW', N'vEmployee', 'COLUMN', N'PhoneNumberType'
GO
EXEC sp_addextendedproperty N'MS_Description', N'Postal code.', 'SCHEMA', N'HumanResources', 'VIEW', N'vEmployee', 'COLUMN', N'PostalCode'
GO
EXEC sp_addextendedproperty N'MS_Description', N'State of employee.', 'SCHEMA', N'HumanResources', 'VIEW', N'vEmployee', 'COLUMN', N'StateProvinceName'
GO
EXEC sp_addextendedproperty N'MS_Description', N'The suffix for a employee.', 'SCHEMA', N'HumanResources', 'VIEW', N'vEmployee', 'COLUMN', N'Suffix'
GO
EXEC sp_addextendedproperty N'MS_Description', N'The title for a employee. [''Mr.'', ''Mrs.'', ''Sr.'', ''Jr.'', ''Sra.'']', 'SCHEMA', N'HumanResources', 'VIEW', N'vEmployee', 'COLUMN', N'Title'
GO

```


---

## <a name="#uses"></a>Uses

* [[Person].[BusinessEntityAddress]](../Tables/Person_BusinessEntityAddress.md)
* [[Person].[CountryRegion]](../Tables/Person_CountryRegion.md)
* [[Person].[EmailAddress]](../Tables/Person_EmailAddress.md)
* [[Person].[Person]](../Tables/Person_Person.md)
* [dbo].[Name]
* [dbo].[Phone]
* [HumanResources]
* [HumanResources].[Employee]
* [Person].[Address]
* [Person].[PersonPhone]
* [Person].[PhoneNumberType]
* [Person].[StateProvince]


---

###### Author:  Smith, JC

###### Copyright 2024 - All Rights Reserved

###### Created: Thursday, July 11, 2024 10:33:41 AM

