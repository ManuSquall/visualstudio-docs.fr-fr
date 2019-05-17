---
title: 'Procédure : Ajouter un fichier de ressources | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: e7b8394d0c21ed5a45639e4dad5fe3695aaccc27
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63440005"
---
# <a name="how-to-add-a-resource-file"></a>Procédure : Ajouter un fichier de ressources
  Les commandes pour l’ajout de fichiers de ressources se trouve sur le menu contextuel des nœuds de fonctionnalité dans l’Explorateur de solutions et de nœud de la solution. Pour plus d’informations, consultez [solutions SharePoint localisation](../sharepoint/localizing-sharepoint-solutions.md).

### <a name="to-add-a-global-resource-file-to-a-sharepoint-solution"></a>Pour ajouter un fichier de ressources globales à une solution SharePoint

1. Dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], ouvrez une solution SharePoint.

2. Dans **l’Explorateur de solutions**, choisissez un nœud de projet SharePoint, puis, dans la barre de menus, choisissez **projet** > **ajouter un nouvel élément**.

3. Dans le **ajouter un nouvel élément** boîte de dialogue, sélectionnez le **fichier de ressources Global** modèle, puis choisissez le **ajouter** bouton.

   > [!NOTE]
   > Le modèle d’élément de projet fichier de ressources Global apparaît uniquement lorsqu’un élément de projet SharePoint est sélectionné.

4. Dans le **ajouter une ressource** boîte de dialogue, sélectionnez une culture pour le fichier de ressources, par exemple l’anglais (États-Unis).

    Cette étape ajoute un fichier de ressources globales à votre solution dans le format, Resource_x_**.** <em>culture</em><strong>.</strong> resx, tel que *Resource1-US.resx*.

5. Lorsque le **éditeur de ressources** s’ouvre dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], ajouter des ressources au fichier de ressources.

### <a name="to-add-a-feature-resource-file-to-a-sharepoint-feature"></a>Pour ajouter un fichier de ressources de fonctionnalité à une fonctionnalité SharePoint

1. Si la solution SharePoint n’est pas déjà ouverte dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], ouvrez la solution.

2. Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour le nom d’une fonctionnalité sous le **fonctionnalités** nœud, puis choisissez **ajouter une ressource de fonctionnalité**.

     Cette étape ajoute un fichier de ressources à la fonctionnalité dans le format, _ResourceFileName_**.** _culture_**.resx**, tel que *Feature1.en-us.resx*.

3. Lorsque le **éditeur de ressources** s’ouvre dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], ajouter des ressources au fichier de ressources.

## <a name="see-also"></a>Voir aussi
- [Développer des solutions SharePoint](../sharepoint/developing-sharepoint-solutions.md)
