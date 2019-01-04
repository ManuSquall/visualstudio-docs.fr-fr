---
title: 'Procédure : Ajouter et supprimer des fonctionnalités et des éléments dans un Package à l’aide de l’Explorateur de package | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.RAD.PackagingExplorer
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: b1211b0bdc3625b915221cfafaa5377d371aaa25
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53880859"
---
# <a name="how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer"></a>Procédure : Ajouter et supprimer des fonctionnalités et des éléments dans un Package à l’aide de l’Explorateur de package
  Pour configurer un package pour déployer des fonctionnalités et des éléments de SharePoint, vous pouvez utiliser l’Explorateur de package. Vous pouvez ajuster les éléments de projet SharePoint et les fonctionnalités à l’intérieur de votre fichier .wsp.  
  
 Ou bien, vous pouvez utiliser le Concepteur d’empaquetage pour afficher et réorganiser les fonctionnalités pour modifier l’ordre d’activation. Pour plus d'informations, voir [Procédure : Ajouter et supprimer des fonctionnalités et des éléments dans un package à l’aide du Concepteur de packages](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md).  
  
## <a name="open-the-packaging-explorer"></a>Ouvrez l’Explorateur de package  
 Vous pouvez utiliser la procédure suivante pour ouvrir l’Explorateur de package, si votre solution Visual Studio a au moins un projet SharePoint. Vous pouvez également l’Explorateur de package s’ouvre automatiquement lorsque vous affichez un concepteur de fonctionnalités ou de packages. Une fois que vous fermez tous les concepteurs de fonctionnalités et de packages, l’Explorateur de package se ferme également.  
  
#### <a name="to-open-the-packaging-explorer"></a>Pour ouvrir l’Explorateur de package  
  
1.  Dans la barre de menus, choisissez **vue** > **Windows autres** > **Explorateur de package**.  
  
     Le **Explorateur de package** s’affiche dans le **boîte à outils**.  
  
## <a name="adding-a-feature-to-a-package"></a>Ajout d’une fonctionnalité à un package  
 Vous pouvez ajouter des fonctionnalités nouvelles et existantes à un Package à l’aide de l’Explorateur de package.  
  
#### <a name="to-add-a-sharepoint-feature"></a>Pour ajouter une fonctionnalité SharePoint
  
1.  Ouvrez le **Explorateur de package**, ouvrez le menu contextuel du projet, puis choisissez **ajouter une fonctionnalité**.  
  
#### <a name="to-move-an-existing-sharepoint-feature"></a>Pour déplacer une fonctionnalité SharePoint existante  
  
1.  Ouvrez le **Explorateur de package**, puis effectuez l’une des étapes suivantes :  
  
    -   Faites glisser un **fonctionnalité** d’un projet vers un autre projet.  
  
    -   Ouvrez le menu contextuel pour une fonctionnalité, choisissez **couper**, ouvrez le menu contextuel du projet auquel vous souhaitez déplacer le composant, puis choisissez **coller**.  
  
    > [!NOTE]  
    >  Utilisez cette procédure si vous avez plusieurs projets SharePoint dans votre solution.  
  
## <a name="validate-a-feature-or-package"></a>Valider une fonctionnalité ou un package  
 Vous pouvez identifier les problèmes potentiels dans les fonctionnalités de SharePoint et les packages en validant les fichiers. Avertissements et erreurs sont affichées dans la fenêtre Sortie et la fenêtre liste d’erreurs.  
  
#### <a name="to-validate-a-sharepoint-feature-or-package"></a>Pour valider une fonctionnalité SharePoint ou un package
  
1.  Ouvrez le **Explorateur de package**.  
  
2.  Ouvrez un menu contextuel pour une fonctionnalité ou un package, puis choisissez **Validate**.  
  
## <a name="see-also"></a>Voir aussi
 [Empaqueter et déployer des solutions SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
