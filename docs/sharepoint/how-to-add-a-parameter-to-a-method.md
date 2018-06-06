---
title: 'Comment : ajouter un paramètre à une méthode | Documents Microsoft'
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
ms.openlocfilehash: 9268fd0deb463a29c8e6d19e98ad63c86b965292
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2018
ms.locfileid: "34767086"
---
# <a name="how-to-add-a-parameter-to-a-method"></a>Comment : ajouter un paramètre à une méthode
  Utiliser un paramètre pour transmettre des informations dans la méthode ou pour retourner des informations à partir d’une méthode. Toutes les méthodes doivent avoir au moins un paramètre. Pour plus d’informations sur la conception d’un paramètre pour prendre en charge le type de méthode que vous souhaitez créer, consultez [vous concevez un modèle de connectivité de données métiers](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
 Lorsque vous ajoutez un paramètre à une méthode, Visual Studio ajoute l’élément de paramètre pour le code XML du fichier de modèle dans votre projet. Pour plus d’informations sur les attributs d’un élément de paramètre, consultez [paramètre](http://go.microsoft.com/fwlink/?LinkId=169284).  
  
### <a name="to-add-a-parameter-to-a-method"></a>Pour ajouter un paramètre à une méthode  
  
1.  Ajoutez une méthode à une entité.  
  
2.  Dans la barre de menus, choisissez **vue** > **autres fenêtres** > **détails de méthode BDC**.  
  
     Le **détails de méthode BDC** fenêtre s’ouvre. Pour plus d’informations, consultez [vue d’ensemble des outils de conception modèle BDC](../sharepoint/bdc-model-design-tools-overview.md).  
  
3.  Dans le **détails de méthode BDC** fenêtre, développez le nœud de la méthode, puis développez le **paramètres** nœud.  
  
4.  Dans le **ajouter un paramètre** , choisissez **créer paramètre**.  
  
     Un nouveau paramètre s’affiche sous le **paramètres** nœud.  
  
5.  Dans la barre de menus, choisissez **vue** > **fenêtre Propriétés**.  
  
6.  Dans le **propriétés** , configurez la **nom** propriété à n’importe quel nom logique. Par exemple, si la méthode retourne des clients, vous pouvez nommer la méthode **GetCustomers**.  
  
7.  Dans le **détails de méthode BDC** fenêtre, ouvrez la liste qui s’affiche pour la direction du paramètre, puis choisissez **dans**, **InOut**, **Out**, ou **retourner**.  
  
     Pour plus d’informations sur la direction à choisir pour la méthode de type que vous créez, consultez [vous concevez un modèle de connectivité de données métiers](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
8.  Modifier le descripteur de type du paramètre. Pour plus d’informations, consultez [Comment : définir le descripteur de Type d’un paramètre](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).  
  
## <a name="see-also"></a>Voir aussi
 [Présentation des outils de conception modèle BDC](../sharepoint/bdc-model-design-tools-overview.md)   
 [Comment : ajouter une entité à un modèle](../sharepoint/how-to-add-an-entity-to-a-model.md)   
 [Comment : définir le descripteur de Type d’un paramètre](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)   
 [Comment : définir une Instance de méthode](../sharepoint/how-to-define-a-method-instance.md)   
 [Conception d’un modèle de connectivité de données métiers](../sharepoint/designing-a-business-data-connectivity-model.md)  
  
