---
title: 'Explorateur de package : Ajouter & supprimer des fonctionnalités & des éléments du package'
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VS.SharePointTools.RAD.PackagingExplorer
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c3ea7e30737855cbbb9434e8763f4903d80b82da
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "86014559"
---
# <a name="how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer"></a>Comment : ajouter et supprimer des fonctionnalités et des éléments dans un package à l’aide de l’Explorateur de package
  Pour configurer un package en vue de déployer des éléments et des fonctionnalités SharePoint, vous pouvez utiliser l’Explorateur de packages. Vous pouvez ajuster les éléments de projet et les fonctionnalités SharePoint à l’intérieur de votre fichier. wsp.

 Vous pouvez également utiliser le concepteur de package pour afficher et réorganiser les fonctionnalités afin de modifier l’ordre d’activation. Pour plus d’informations, consultez [Comment : ajouter et supprimer des fonctionnalités et des éléments dans un package à l’aide du concepteur de packages](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md).

## <a name="open-the-packaging-explorer"></a>Ouvrir l’Explorateur de packages
 Vous pouvez utiliser la procédure suivante pour ouvrir l’Explorateur de packages, si votre solution Visual Studio a au moins un projet SharePoint. L’Explorateur de package s’ouvre automatiquement lorsque vous affichez un concepteur de fonctionnalités ou de packages. Une fois que vous avez fermé tous les concepteurs de fonctionnalités et de packages, l’Explorateur de packages se ferme également.

#### <a name="to-open-the-packaging-explorer"></a>Pour ouvrir l’Explorateur de package

1. Dans la barre de menus, choisissez **Afficher**  >  **autres**  >  **Explorateur de packages**Windows.

     L' **Explorateur de package** s’affiche dans la **boîte à outils**.

## <a name="adding-a-feature-to-a-package"></a>Ajout d’une fonctionnalité à un package
 Vous pouvez ajouter des fonctionnalités nouvelles et existantes à un package à l’aide de l’Explorateur de package.

#### <a name="to-add-a-sharepoint-feature"></a>Pour ajouter une fonctionnalité SharePoint

1. Ouvrez l' **Explorateur de packages**, ouvrez le menu contextuel du projet, puis choisissez **Ajouter une fonctionnalité**.

#### <a name="to-move-an-existing-sharepoint-feature"></a>Pour déplacer une fonctionnalité SharePoint existante

1. Ouvrez l' **Explorateur de package**, puis effectuez l’une des opérations suivantes :

    - Faites glisser une **fonctionnalité** d’un projet vers un autre projet.

    - Ouvrez le menu contextuel d’une fonctionnalité, choisissez **couper**, ouvrez le menu contextuel du projet vers lequel vous souhaitez déplacer la fonctionnalité, puis choisissez **coller**.

    > [!NOTE]
    > Utilisez cette procédure si vous avez plusieurs projets SharePoint dans votre solution.

## <a name="validate-a-feature-or-package"></a>Valider une fonctionnalité ou un package
 Vous pouvez identifier les problèmes potentiels dans les fonctionnalités et les packages SharePoint en validant les fichiers. Les avertissements et les erreurs s’affichent dans la fenêtre sortie et dans la fenêtre de Liste d’erreurs.

#### <a name="to-validate-a-sharepoint-feature-or-package"></a>Pour valider une fonctionnalité ou un package SharePoint

1. Ouvrez l' **Explorateur de package**.

2. Ouvrez un menu contextuel pour une fonctionnalité ou un package, puis choisissez **valider**.

## <a name="see-also"></a>Voir aussi
- [Empaqueter et déployer des solutions SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
