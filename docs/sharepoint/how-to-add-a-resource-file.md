---
title: 'Comment : ajouter un fichier de ressources | Microsoft Docs'
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
- resource files [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, resource files
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 0091054c0c0d2cfb7f19f2ca46839cfdcf47832b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49861187"
---
# <a name="how-to-add-a-resource-file"></a>Comment : ajouter un fichier de ressources
  Les commandes pour l’ajout de fichiers de ressources se trouve sur le menu contextuel des nœuds de fonctionnalité dans l’Explorateur de solutions et de nœud de la solution. Pour plus d’informations, consultez [solutions SharePoint localisation](../sharepoint/localizing-sharepoint-solutions.md).  
  
### <a name="to-add-a-global-resource-file-to-a-sharepoint-solution"></a>Pour ajouter un fichier de ressources globales à une solution SharePoint  
  
1. Dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], ouvrez une solution SharePoint.  
  
2. Dans **l’Explorateur de solutions**, choisissez un nœud de projet SharePoint, puis, dans la barre de menus, choisissez **projet** > **ajouter un nouvel élément**.  
  
3. Dans le **ajouter un nouvel élément** boîte de dialogue, sélectionnez le **fichier de ressources Global** modèle, puis choisissez le **ajouter** bouton.  
  
   > [!NOTE]  
   >  Le modèle d’élément de projet fichier de ressources Global apparaît uniquement lorsqu’un élément de projet SharePoint est sélectionné.  
  
4. Dans le **ajouter une ressource** boîte de dialogue, sélectionnez une culture pour le fichier de ressources, par exemple l’anglais (États-Unis).  
  
    Cette étape ajoute un fichier de ressources globales à votre solution dans le format, Resource_x_**.** <em>culture</em><strong>.</strong> resx, tel que *Resource1-US.resx*.  
  
5. Lorsque le **éditeur de ressources** s’ouvre dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], ajouter des ressources au fichier de ressources.  
  
### <a name="to-add-a-feature-resource-file-to-a-sharepoint-feature"></a>Pour ajouter un fichier de ressources de fonctionnalité à une fonctionnalité SharePoint  
  
1.  Si la solution SharePoint n’est pas déjà ouverte dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], ouvrez la solution.  
  
2.  Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour le nom d’une fonctionnalité sous le **fonctionnalités** nœud, puis choisissez **ajouter une ressource de fonctionnalité**.  
  
     Cette étape ajoute un fichier de ressources à la fonctionnalité dans le format, _ResourceFileName_**.** _culture_**.resx**, tel que *Feature1.en-us.resx*.  
  
3.  Lorsque le **éditeur de ressources** s’ouvre dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], ajouter des ressources au fichier de ressources.  
  
## <a name="see-also"></a>Voir aussi
 [Développer des solutions SharePoint](../sharepoint/developing-sharepoint-solutions.md)  
  
 
