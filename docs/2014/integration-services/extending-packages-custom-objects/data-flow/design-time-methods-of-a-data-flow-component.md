---
title: Méthodes de conception d’un composant de flux de données | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom data flow components [Integration Services], method execution sequence
- ProcessInput method
- method execution sequence [Integration Services]
- PrimeOutput method
- data flow components [Integration Services], method execution sequence
ms.assetid: b5a121a1-b87c-441b-a42c-2cec628dc81c
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 7d7d1a2d3b62578fc2fd627aea32112c218895d3
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62896259"
---
# <a name="design-time-methods-of-a-data-flow-component"></a>Méthodes de conception d'un composant de flux de données
  Avant l'exécution, la tâche de flux de données est dite au moment de la conception, puisqu'elle subit des modifications incrémentielles. Les modifications peuvent inclure l'ajout ou la suppression de composants, l'ajout ou la suppression d'objets de chemin d'accès qui connectent des composants, ainsi que des modifications apportées aux métadonnées des composants. Lorsque des modifications de métadonnées se produisent, le composant peut les surveiller et y réagir. Par exemple, un composant peut rejeter certaines modifications ou apporter des modifications supplémentaires en réponse à une modification. Au moment de la conception, le concepteur interagit avec un composant via l'interface <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSDesigntimeComponent100> du moment de la conception.  
  
## <a name="design-time-implementation"></a>Implémentation au moment de la conception  
 L'interface de conception d'un composant est décrite par l'interface <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSDesigntimeComponent100>. Bien que vous n'implémentiez pas cette interface explicitement, la connaissance des méthodes définies dans cette interface vous aidera à comprendre quelles méthodes de la classe de base <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent> correspondent à l'instance de conception d'un composant.  
  
 Lorsqu'un composant est chargé dans [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)], l'instance de conception du composant est instanciée et les méthodes de l'interface <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSDesigntimeComponent100> sont appelées alors que le composant est modifié. L'implémentation de la classe de base vous permet de remplacer uniquement les méthodes que votre composant requiert. Dans de nombreux cas, vous pouvez remplacer ces méthodes pour empêcher des modifications inappropriées d'un composant. Par exemple, pour empêcher des utilisateurs d'ajouter une sortie à un composant, remplacez la méthode <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.InsertOutput%2A>. Sinon, lorsque l'implémentation de cette méthode par la classe de base est appelée, elle ajoute une sortie au composant.  
  
 Indépendamment de l'objectif ou des fonctionnalités de votre composant, vous devez remplacer les méthodes <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProvideComponentProperties%2A>, <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.Validate%2A> et <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ReinitializeMetaData%2A>. Pour plus d’informations sur <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.Validate%2A> et <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ReinitializeMetaData%2A>, consultez [Validation d’un composant de flux de données](validating-a-data-flow-component.md).  
  
## <a name="providecomponentproperties-method"></a>Méthode ProvideComponentProperties  
 L'initialisation d'un composant se produit dans la méthode <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProvideComponentProperties%2A>. Cette méthode est appelée par le Concepteur [!INCLUDE[ssIS](../../../includes/ssis-md.md)] lorsqu'un composant est ajouté à la tâche de flux de données et qu'il est similaire à un constructeur de classe. Les développeurs de composants doivent créer et initialiser leurs entrées, sorties et propriétés personnalisées pendant cet appel de méthode. La méthode <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProvideComponentProperties%2A> diffère d'un constructeur parce qu'elle n'est pas appelée chaque fois que l'instance de conception ou l'instance d'exécution du composant est instanciée.  
  
 L'implémentation de la classe de base de la méthode ajoute une entrée et une sortie au composant et attribue l'ID de l'entrée à la propriété <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100.SynchronousInputID%2A>. Toutefois, les objets d'entrée et de sortie ajoutés par la classe de base ne sont pas nommés dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Les packages qui contiennent un composant avec des objets d’entrée ou de sortie dont la propriété Name n’est pas définie ne se chargeront pas correctement. Par conséquent, lorsque vous utilisez l’implémentation de base, vous devez attribuer explicitement des valeurs à la propriété Name de l’entrée ou la sortie par défaut.  
  
```csharp  
public override void ProvideComponentProperties()  
{  
    /// TODO: Reset the component.  
    /// TODO: Add custom properties.  
    /// TODO: Add input objects.  
    /// TODO: Add output objects.  
}  
```  
  
```vb  
Public Overrides Sub ProvideComponentProperties()  
    ' TODO: Reset the component.  
    ' TODO: Add custom properties.  
    ' TODO: Add input objects.  
    ' TODO: Add output objects.  
End Sub  
```  
  
### <a name="creating-custom-properties"></a>Création de propriétés personnalisées  
 L'appel de la méthode <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProvideComponentProperties%2A> est l'emplacement auquel les développeurs de composants doivent ajouter des propriétés personnalisées (<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSCustomProperty100>) au composant. Les propriétés personnalisées n'ont pas de propriété de type de données. Le type de données d'une propriété personnalisée est défini par le type de données de la valeur que vous attribuez à sa propriété <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSCustomProperty100.Value%2A>. Toutefois, après avoir attribué une valeur initiale à la propriété personnalisée, vous ne pouvez pas attribuer une valeur dont le type de données est différent.  
  
> [!NOTE]  
>  L'interface <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSCustomProperty100> offre une prise en charge limitée des valeurs de propriétés de type `Object`. Le seul objet que vous pouvez stocker en tant que valeur d'une propriété personnalisée est un tableau de types simples tels que des chaînes ou des entiers.  
  
 Vous pouvez indiquer que votre propriété personnalisée prend en charge des expressions de propriété en définissant la valeur de sa propriété <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSCustomProperty100.ExpressionType%2A> sur `CPET_NOTIFY` à partir de l'énumération <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSCustomPropertyExpressionType>, comme indiqué dans l'exemple suivant. Vous ne devez pas ajouter de code pour gérer ou valider l'expression de propriété entrée par l'utilisateur. Vous pouvez définir une valeur par défaut pour la propriété, validez sa valeur, ainsi que lire et utiliser normalement sa valeur.  
  
```csharp  
IDTSCustomProperty100 myCustomProperty;  
...  
myCustomProperty.ExpressionType = DTSCustomPropertyExpressionType.CPET_NOTIFY;  
```  
  
```vb  
Dim myCustomProperty As IDTSCustomProperty100  
...  
myCustomProperty.ExpressionType = DTSCustomPropertyExpressionType.CPET_NOTIFY  
```  
  
 Vous pouvez limiter les utilisateurs à la sélection d’une valeur de propriété personnalisée à partir d’une énumération à l’aide de la <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSCustomProperty100.TypeConverter%2A> propriété, comme indiqué dans l’exemple suivant, qui suppose que vous avez défini une énumération publique nommée `MyValidValues`.  
  
```csharp  
IDTSCustomProperty100 customProperty = outputColumn.CustomPropertyCollection.New();  
customProperty.Name = "My Custom Property";  
// This line associates the type with the custom property.  
customProperty.TypeConverter = typeof(MyValidValues).AssemblyQualifiedName;  
// Now you can use the enumeration values directly.  
customProperty.Value = MyValidValues.ValueOne;    
```  
  
```vb  
Dim customProperty As IDTSCustomProperty100 = outputColumn.CustomPropertyCollection.New   
customProperty.Name = "My Custom Property"   
' This line associates the type with the custom property.  
customProperty.TypeConverter = GetType(MyValidValues).AssemblyQualifiedName   
' Now you can use the enumeration values directly.  
customProperty.Value = MyValidValues.ValueOne  
```  
  
 Pour plus d’informations, consultez « Conversion de type généralisée » et « Implémentation d’un convertisseur de type » dans la [MSDN Library](https://go.microsoft.com/fwlink/?LinkId=7022).  
  
 Vous pouvez spécifier une boîte de dialogue d'éditeur personnalisée pour la valeur de votre propriété personnalisée en utilisant la propriété <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSCustomProperty100.UITypeEditor%2A>, comme indiqué dans l'exemple suivant. Tout d'abord, vous devez créer un éditeur de type personnalisé qui hérite de `System.Drawing.Design.UITypeEditor`, si vous ne pouvez pas localiser une classe existante d'éditeur de types muni d'une interface utilisateur qui répond à vos besoins.  
  
```csharp  
public class MyCustomTypeEditor : UITypeEditor  
{  
...  
}  
```  
  
```vb  
Public Class MyCustomTypeEditor  
  Inherits UITypeEditor   
  ...  
End Class  
```  
  
 Ensuite, spécifiez cette classe en tant que valeur de la propriété <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSCustomProperty100.UITypeEditor%2A> de votre propriété personnalisée.  
  
```csharp  
IDTSCustomProperty100 customProperty = outputColumn.CustomPropertyCollection.New();  
customProperty.Name = "My Custom Property";  
// This line associates the editor with the custom property.  
customProperty.UITypeEditor = typeof(MyCustomTypeEditor).AssemblyQualifiedName;  
```  
  
```vb  
Dim customProperty As IDTSCustomProperty100 = outputColumn.CustomPropertyCollection.New   
customProperty.Name = "My Custom Property"   
' This line associates the editor with the custom property.  
customProperty.UITypeEditor = GetType(MyCustomTypeEditor).AssemblyQualifiedName  
```  
  
 Pour plus d’informations, consultez « Implémentation d’un éditeur de type d’interface utilisateur » dans [MSDN Library](https://go.microsoft.com/fwlink/?LinkId=7022).  
  
![Icône Integration Services (petite)](../../media/dts-16.gif "icône Integration Services (petite)")**rester jusqu'à la Date avec Integration Services**<br /> Pour obtenir les derniers téléchargements, articles, exemples et vidéos de Microsoft, ainsi que des solutions sélectionnées par la communauté, visitez la page [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] sur MSDN :<br /><br /> [Visitez la page Integration Services sur MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Pour recevoir une notification automatique de ces mises à jour, abonnez-vous aux flux RSS disponibles sur la page.  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes d’exécution d’un composant de flux de données](run-time-methods-of-a-data-flow-component.md)  
  
  
