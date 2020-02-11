---
title: 'Leçon 3 : renommer des colonnes | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 5fc8ba1a-2b30-4775-9b3b-c09dee711b3e
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 80d9cae6deae4059327084f531f6a6d958a39ec6
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66070317"
---
# <a name="lesson-3-rename-columns"></a>Leçon 3 : Renommer des colonnes
  Dans cette leçon, vous allez renommer plusieurs colonnes dans chaque table que vous avez importée. En renommant les colonnes, elles seront plus faciles à identifier et à parcourir dans le concepteur de modèles mais aussi via les champs de sélection dans une application cliente. Pour plus d’informations, consultez [Renommer une table ou une colonne &#40;SSAS Tabulaire&#41;](tabular-models/rename-a-table-or-column-ssas-tabular.md).  
  
> [!IMPORTANT]  
>  Renommer des colonnes n'est pas nécessaire pour effectuer ce didacticiel ; toutefois, les leçons restantes, en particulier celles qui incluent la création de relations et la création de colonnes calculées et de mesures à l'aide de formules DAX, font référence aux noms conviviaux de colonnes décrits dans cette leçon. Si vous choisissez de ne pas renommer les colonnes, vous devez modifier les formules DAX dans les leçons 5, 6, et 7 pour utiliser les noms de colonne source d'origine fournis dans cette leçon.  
  
 Durée estimée pour suivre cette leçon : **20 minutes**  
  
## <a name="prerequisites"></a>Conditions préalables requises  
 Cette rubrique fait partie d’un didacticiel de modélisation tabulaire, qui doit être suivi dans l’ordre prévu. Avant d’effectuer les tâches de cette leçon, vous devez avoir terminé la leçon précédente : [Leçon 2 : Ajouter des données](lesson-2-add-data.md).  
  
## <a name="rename-columns"></a>Renommer des colonnes  
  
#### <a name="to-rename-columns"></a>Pour renommer des colonnes  
  
1.  Dans le concepteur de modèles, cliquez sur la table (onglet) **Customer** .  
  
     Quand vous cliquez sur un onglet, la table correspondante devient active dans la fenêtre du concepteur de modèles.  
  
2.  Double-cliquez **** sur le nom de la colonne `Customer  Id`CustomerKey, tapez, puis appuyez sur entrée.  
  
    > [!TIP]  
    >  Vous pouvez également renommer une colonne dans la propriété nom de la **colonne** dans la fenêtre **Propriétés** de la colonne, ou dans la vue de diagramme.  
  
3.  Renommez les colonnes restantes dans la table **Customer** , ainsi que les colonnes dans les autres tables, en remplaçant le nom de la source par le nom convivial :  
  
     **Table Customer**  
  
    |Nom de la source|Nom convivial|  
    |-----------------|-------------------|  
    |GeographyKey|Geography Id|  
    |CustomerAlternateKey|Customer Alternate Id|  
    |FirstName|Prénom|  
    |MiddleName|Middle Name|  
    |LastName|Nom|  
    |NameStyle|Name Style|  
    |BirthDate|Birth Date|  
    |MaritalStatus|Marital Status|  
    |EmailAddress|Adresse de messagerie|  
    |YearlyIncome|Yearly Income|  
    |TotalChildren|Total Children|  
    |NumberChildrenAtHome|Number of Children At Home|  
    |EnglishEducation|Formation|  
    |EnglishOccupation|Occupation|  
    |HouseOwnerFlag|Owns House|  
    |NumberCarsOwned|Number of Cars Owned|  
    |AddressLine1|Address Line 1|  
    |AddressLine2|Address Line 2|  
    |Téléphone|Numéro de téléphone|  
    |DateFirstPurchase|Date of First Purchase|  
    |CommuteDistance|Commute Distance|  
  
     **Date**  
  
    |Nom de la source|Nom convivial|  
    |-----------------|-------------------|  
    |FullDateAlternateKey|Date|  
    |DayNumberOfWeek|Day Number of Week|  
    |EnglishDayNameOfWeek|Day Name|  
    |DayNumberOfMonth|Day of Month|  
    |DayNumberOfYear|Day of Year|  
    |WeekNumberOfYear|Week Number of Year|  
    |EnglishMonthName|Month Name|  
    |MonthNumberOfYear|Month|  
    |CalendarQuarter|Calendar Quarter|  
    |CalendarYear|Calendar Year|  
    |CalendarSemester|Calendar Semester|  
    |FiscalQuarter|Fiscal Quarter|  
    |FiscalYear|Fiscal Year|  
    |FiscalSemester|Fiscal Semester|  
  
     **Région**  
  
    |Nom de la source|Nom convivial|  
    |-----------------|-------------------|  
    |GeographyKey|Geography Id|  
    |StateProvinceCode|State Province Code|  
    |StateProvinceName|State Province Name|  
    |CountryRegionCode|Country Region Code|  
    |EnglishCountryRegionName|Country Region Name|  
    |PostalCode|Code postal|  
    |SalesTerritoryKey|Sales Territory Id|  
  
     **Produit**  
  
    |Nom de la source|Nom convivial|  
    |-----------------|-------------------|  
    |ProductKey|Product Id|  
    |ProductAlternateKey|Product Alternate Id|  
    |ProductSubcategoryKey|Product Subcategory Id|  
    |WeightUnitMeasureCode|Weight Unit Code|  
    |SizeUnitMeasureCode|Size Unit Code|  
    |EnglishProductName|Nom du produit|  
    |CoûtStandard|Standard Cost|  
    |FinishedGoodsFlag|Is Finished Product|  
    |SafetyStockLevel|Safety Stock Level|  
    |ReorderPoint|Reorder Point|  
    |ListPrice|List Price|  
    |SizeRange|Size Range|  
    |DaysToManufacture|Days to Manufacture|  
    |ProductLine|Product Line|  
    |Dealer Price|Dealer Price|  
    |ModelName|Nom du modèle|  
    |LargePhoto|Large Photo|  
    |EnglishDescription|Description|  
    |StartDate|Product Start Date|  
    |EndDate|Product End Date|  
    |Statut|Product Status|  
  
     **Catégorie de produit**  
  
    |Nom de la source|Nom convivial|  
    |-----------------|-------------------|  
    |ProductCategoryKey|Product Category Id|  
    |ProductCategoryAlternateKey|Product Category Alternate Id|  
    |EnglishProductCategoryName|Product Category Name|  
  
     **Product Subcategory**  
  
    |Nom de la source|Nom convivial|  
    |-----------------|-------------------|  
    |ProductSubcategoryKey|Product Subcategory Id|  
    |ProductSubcategoryAlternateKey|Product Subcategory Alternate Id|  
    |EnglishProductSubcategoryName|Product Subcategory Name|  
    |ProductCategoryKey|Product Category Id|  
  
     **Ventes sur Internet**  
  
    |Nom de la source|Nom convivial|  
    |-----------------|-------------------|  
    |ProductKey|Product Id|  
    |CustomerKey|Customer Id|  
    |PromotionKey|Promotion Id|  
    |CurrencyKey|Currency Id|  
    |SalesTerritoryKey|Sales Territory Id|  
    |SalesOrderNumber|Sales Order Number|  
    |SalesOrderLineNumber|Sales Order Line Number|  
    |RevisionNumber|Revision Number|  
    |OrderQuantity|Order Quantity|  
    |UnitPrice|Unit Price|  
    |ExtendedAmount|Extended Amount|  
    |UnitPriceDiscountPct|Unit Price Discount Pct|  
    |DiscountAmount|Discount Amount|  
    |ProductStandardCost|Product Standard Cost|  
    |TotalProductCost|Total Product Cost|  
    |SalesAmount|Sales Amount|  
    |TaxAmt|Tax Amt|  
    |CarrierTrackingNumber|Carrier Tracking Number|  
    |CustomerPONumber|Customer PO Number|  
    |OrderDate|Order Date|  
    |DueDate|Due Date|  
    |ShipDate|Ship Date|  
  
## <a name="next-step"></a>étape suivante  
 Pour poursuivre l’étude de ce didacticiel, passez à la [Leçon 4 : Marquer en tant que table de dates](lesson-3-mark-as-date-table.md).  
  
  
