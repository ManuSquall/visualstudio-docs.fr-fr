---
title: "Comment : définir une Instance de méthode | Documents Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], method instance
- BDC [SharePoint development in Visual Studio], method instance
- BDC [SharePoint development in Visual Studio], method
- Business Data Connectivity service [SharePoint development in Visual Studio], method
ms.assetid: f0c8a686-c0de-414e-8de9-f228f59d1eb3
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9316eaa48b11342891584e448f8bb67bdce6f682
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-define-a-method-instance"></a>Comment : définir une instance de méthode
  Vous devez définir au moins une instance de méthode pour chaque méthode dans votre modèle.  
  
 Ajouter une instance de méthode à l’aide de la **détails de méthode BDC** fenêtre. Lorsque vous ajoutez l’instance de méthode, Visual Studio ajoute un `<MethodInstance>` élément pour le code XML du fichier de modèle dans votre projet. Pour plus d’informations sur les attributs d’un `<MethodInstance>` élément, consultez [MethodInstance](http://go.microsoft.com/fwlink/?LinkID=169282).  
  
### <a name="to-define-a-method-instance"></a>Pour définir une instance de méthode  
  
1.  Dans le **détails de méthode BDC** fenêtre, développez le nœud d’une méthode, puis développez le **Instances** nœud.  
  
2.  Dans le **ajouter une Instance de méthode** , choisissez **créer une Instance de recherche**.  
  
     Une nouvelle instance de méthode s’affiche sous le **Instances** nœud.  
  
3.  Dans la barre de menus, choisissez **vue**, choisissez **fenêtre Propriétés**.  
  
4.  Dans le **propriétés** fenêtre, définissez les propriétés de l’instance de méthode. Pour plus d’informations sur chaque propriété, consultez [MethodInstance](http://go.microsoft.com/fwlink/?LinkID=169282).  
  
## <a name="see-also"></a>Voir aussi  
 [Présentation des outils de conception modèle BDC](../sharepoint/bdc-model-design-tools-overview.md)   
 [Comment : ajouter une entité à un modèle](../sharepoint/how-to-add-an-entity-to-a-model.md)   
 [Comment : ajouter un paramètre à une méthode](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Comment : définir le descripteur de Type d’un paramètre](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)   
 [Conception d’un modèle de connectivité de données métiers](../sharepoint/designing-a-business-data-connectivity-model.md)  
  
  