---
title: 'Comment : ajouter un paramètre à une méthode | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], adding a method to a parameter
- Business Data Connectivity service [SharePoint development in Visual Studio], parameter
- BDC [SharePoint development in Visual Studio], adding a method to a parameter
- BDC [SharePoint development in Visual Studio], parameter
- Business Data Connectivity service [SharePoint development in Visual Studio], method parameters
- BDC [SharePoint development in Visual Studio], method parameters
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 196ac37cc9bc4f53cfa886b92c62c7a301c3451a
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36756309"
---
# <a name="how-to-add-a-parameter-to-a-method"></a>Comment : ajouter un paramètre à une méthode
  Utiliser un paramètre pour transmettre des informations dans la méthode ou pour retourner des informations à partir d’une méthode. Toutes les méthodes doivent avoir au moins un paramètre. Pour plus d’informations sur la conception d’un paramètre pour prendre en charge le type de méthode que vous souhaitez créer, consultez [conception d’un modèle de connectivité de données métiers](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
 Lorsque vous ajoutez un paramètre à une méthode, Visual Studio ajoute l’élément de paramètre pour le code XML du fichier de modèle dans votre projet. Pour plus d’informations sur les attributs d’un élément de paramètre, consultez [paramètre](http://go.microsoft.com/fwlink/?LinkId=169284).  
  
### <a name="to-add-a-parameter-to-a-method"></a>Pour ajouter un paramètre à une méthode  
  
1.  Ajouter une méthode à une entité.  
  
2.  Dans la barre de menus, choisissez **vue** > **Windows autres** > **détails de méthode BDC**.  
  
     Le **détails de méthode BDC** fenêtre s’ouvre. Pour plus d’informations, consultez [vue d’ensemble des outils de conception modèle BDC](../sharepoint/bdc-model-design-tools-overview.md).  
  
3.  Dans le **détails de méthode BDC** fenêtre, développez le nœud de la méthode, puis développez le **paramètres** nœud.  
  
4.  Dans le **ajouter un paramètre** , choisissez **créer un paramètre**.  
  
     Un nouveau paramètre apparaît sous le **paramètres** nœud.  
  
5.  Dans la barre de menus, choisissez **vue** > **fenêtre Propriétés**.  
  
6.  Dans le **propriétés** fenêtre, définissez la **nom** propriété à n’importe quel nom qui a du sens. Par exemple, si la méthode retourne des clients, vous pouvez nommer la méthode **GetCustomers**.  
  
7.  Dans le **détails de méthode BDC** fenêtre, ouvrez la liste qui s’affiche pour la direction du paramètre, puis choisissez **dans**, **InOut**, **Out**, ou **retourner**.  
  
     Pour plus d’informations sur la direction à choisir pour la méthode de type que vous créez, consultez [concevoir un modèle de connectivité de données métiers](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
8.  Modifier le descripteur de type du paramètre. Pour plus d’informations, consultez [Comment : définir le descripteur de type d’un paramètre](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).  
  
## <a name="see-also"></a>Voir aussi
 [Vue d’ensemble des outils de conception de modèle BDC](../sharepoint/bdc-model-design-tools-overview.md)   
 [Comment : ajouter une entité à un modèle](../sharepoint/how-to-add-an-entity-to-a-model.md)   
 [Comment : définir le descripteur de type d’un paramètre](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)   
 [Comment : définir une instance de méthode](../sharepoint/how-to-define-a-method-instance.md)   
 [Concevoir un modèle de connectivité de données métiers](../sharepoint/designing-a-business-data-connectivity-model.md)  
  
