---
title: 'Comment : ajouter un fichier de ressources | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- resource files [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, resource files
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 657eb473adcff40a62d2fc9b09518ebe8135eeb4
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86015182"
---
# <a name="how-to-add-a-resource-file"></a>Comment : ajouter un fichier de ressources
  Les commandes permettant d’ajouter des fichiers de ressources se trouvent dans le menu contextuel du nœud de la solution et des nœuds de fonctionnalités dans Explorateur de solutions. Pour plus d’informations, consultez [localisation de solutions SharePoint](../sharepoint/localizing-sharepoint-solutions.md).

### <a name="to-add-a-global-resource-file-to-a-sharepoint-solution"></a>Pour ajouter un fichier de ressources globales à une solution SharePoint

1. Dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , ouvrez une solution SharePoint.

2. Dans **Explorateur de solutions**, choisissez un nœud de projet SharePoint, puis, dans la barre de menus, choisissez **projet**  >  **Ajouter un nouvel élément**.

3. Dans la boîte de dialogue **Ajouter un nouvel élément** , choisissez le modèle de **fichier de ressources globales** , puis cliquez sur le bouton **Ajouter** .

   > [!NOTE]
   > Le modèle d’élément de projet de fichier de ressources global s’affiche uniquement lorsqu’un élément de projet SharePoint est sélectionné.

4. Dans la boîte de dialogue **Ajouter une ressource** , choisissez une culture pour le fichier de ressources, par exemple anglais (États-Unis).

    Cette étape ajoute un fichier de ressources globales à votre solution au format, Resource_x_**.** <em>culture</em><strong>.</strong> resx, tel que *Resource1. en-US. resx*.

5. Lorsque l' **éditeur de ressources** s’ouvre dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , ajoutez des ressources au fichier de ressources.

### <a name="to-add-a-feature-resource-file-to-a-sharepoint-feature"></a>Pour ajouter un fichier de ressources de fonctionnalité à une fonctionnalité SharePoint

1. Si la solution SharePoint n’est pas déjà ouverte dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , ouvrez la solution.

2. Dans **Explorateur de solutions**, ouvrez le menu contextuel du nom d’une fonctionnalité sous le nœud **fonctionnalités** , puis choisissez **Ajouter une ressource de fonctionnalité**.

     Cette étape ajoute un fichier de ressources à la fonctionnalité au format _ResourceFileName_**.** _culture_**. resx**, tel que, *Feature1. fr-US. resx*.

3. Lorsque l' **éditeur de ressources** s’ouvre dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , ajoutez des ressources au fichier de ressources.

## <a name="see-also"></a>Voir aussi
- [Développer des solutions SharePoint](../sharepoint/developing-sharepoint-solutions.md)
