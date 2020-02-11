---
title: Configurer un conteneur de boucles for | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- containers [Integration Services], For Loop
- For Loop containers
ms.assetid: b9cd7ea7-b198-4a35-8b16-6acf09611ca5
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: fe51deb631f0c3d794bdce3f05af61b5e030d5e3
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66060828"
---
# <a name="configure-a-for-loop-container"></a>Configurer un conteneur de boucles For
  Cette procédure décrit comment configurer un conteneur de boucles For à l’aide de la boîte de dialogue **Éditeur de boucle For** .  
  
 Pour obtenir un exemple de conteneur de boucles For, consultez [SSIS Loops that do not fail](https://go.microsoft.com/fwlink/?LinkId=240295) sur le site bimonkey.com.  
  
### <a name="to-configure-the-for-loop-container"></a>Pour configurer le conteneur de boucles For  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], double-cliquez sur le conteneur de boucles For pour ouvrir l’ **Éditeur de boucle For**.  
  
2.  Si vous le souhaitez, modifiez le nom et la description du conteneur de boucles For.  
  
3.  Si vous le souhaitez, tapez une expression d’initialisation dans la zone de texte **InitExpression** .  
  
4.  Tapez une expression d’évaluation dans la zone de texte **EvalExpression** .  
  
    > [!NOTE]  
    >  L'expression doit prendre une valeur de type Boolean. Lorsque l'expression correspond à `false`, la boucle cesse de s'exécuter.  
  
5.  Si vous le souhaitez, tapez une expression d’assignation dans la zone de texte **AssignExpression** .  
  
6.  Si vous le souhaitez, cliquez sur **Expressions** et, dans la page **Expressions** , créez des expressions de propriété pour les propriétés du conteneur de boucles For. Pour plus d’informations, consultez [Ajouter ou modifier une Expression de propriété](expressions/add-or-change-a-property-expression.md).  
  
7.  Cliquez sur **OK** pour fermer la boîte de dialogue **Éditeur de boucle For**.  
  
## <a name="see-also"></a>Voir aussi  
 [Conteneur de boucles for](control-flow/for-loop-container.md)   
 [Expressions Integration Services &#40;SSIS&#41;](expressions/integration-services-ssis-expressions.md)   
 [Utilisation d’expressions de propriété dans des packages](expressions/use-property-expressions-in-packages.md)  
  
  
