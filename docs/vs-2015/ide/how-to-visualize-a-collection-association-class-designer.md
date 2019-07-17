---
title: 'Procédure : Visualiser une Association de collections (Concepteur de classes) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.collectionassociationline
- vs.classdesigner.ShowAssociationException
helpviewer_keywords:
- collection associations
- collections, collection associations
- Class Designer [Visual Studio], collection associations
ms.assetid: 54e39838-2fc9-4dc2-85b6-7e88a743108e
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 490ee064903a0e2d119da891681da719e237acec
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68178784"
---
# <a name="how-to-visualize-a-collection-association-class-designer"></a>Procédure : Visualiser une association de collections (Concepteur de classes)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Les propriétés et les champs qui sont des collections d’autres types peuvent être affichés sur le diagramme de classes en tant qu’association de collection. Contrairement à une association normale, qui affiche un champ ou une propriété sous la forme d’une ligne reliant la classe propriétaire au type du champ, une association de collection s’affiche sous la forme d’une ligne reliant la classe propriétaire au type collecté.  
  
### <a name="to-create-a-collection-association"></a>Pour créer une association de collection  
  
1. Dans le code, créez une propriété ou un champ dont le type est lui-même une collection fortement typée.  
  
2. Dans le diagramme de classes, développez la classe afin que les champs et propriétés soient affichés.  
  
3. Dans la classe, cliquez avec le bouton droit sur le champ ou la propriété, puis choisissez **Afficher en tant qu’association de collection**.  
  
     La propriété ou le champ s’affiche sous la forme d’une ligne reliée au type collecté.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique : Créer des Associations entre Types (Concepteur de classes)](../ide/how-to-create-associations-between-types-class-designer.md)   
 [Conception des classes et des types (Concepteur de classes)](../ide/designing-classes-and-types-class-designer.md)   
 [Affichage des types et relations (Concepteur de classes)](../ide/viewing-types-and-relationships-class-designer.md)
