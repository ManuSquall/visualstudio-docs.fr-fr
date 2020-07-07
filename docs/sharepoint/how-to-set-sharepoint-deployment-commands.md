---
title: 'Procédure : définir des commandes de déploiement SharePoint | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, deploying
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c2329efef64e7d8605f8483ff7dce3107cd702fa
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86015501"
---
# <a name="how-to-set-sharepoint-deployment-commands"></a>Procédure : définir des commandes de déploiement SharePoint
  Vous pouvez personnaliser le processus de déploiement en définissant des commandes de pré-déploiement et de prédéploiement. Ces commandes s’exécutent avant et après d’autres actions de déploiement lorsque vous déboguez des solutions SharePoint à partir de Visual Studio.

### <a name="to-add-a-pre-deployment-command"></a>Pour ajouter une commande de prédéploiement

1. Dans la barre de menus, **Project** choisissez  >  ** \<*ProjectName*> Propriétés**du projet.

2. Choisissez l’onglet **SharePoint** .

3. Dans la zone de texte **ligne de commande de prédéploiement** , entrez les commandes MS-DOS ou MSBuild pour personnaliser cette étape.

     Par exemple, pour répertorier le contenu du répertoire avant la fin du déploiement, entrez **dir**.

### <a name="to-add-a-post-deployment-command"></a>Pour ajouter une commande de publication

1. Dans la barre de menus, **Project** choisissez  >  ** \<*ProjectName*> Propriétés**du projet.

2. Choisissez l’onglet **SharePoint** .

3. Dans la zone de texte **ligne de commande de publication du déploiement** , entrez les commandes MS-DOS ou MSBuild pour personnaliser cette étape.

     Par exemple, pour répertorier le contenu du répertoire une fois le déploiement terminé, entrez **dir**. Pour utiliser une variable MSBuild pour copier l’assembly à partir du répertoire de build, entrez **Copy $ (TargetPath) c:\DeploymentDirectory**.

## <a name="see-also"></a>Voir aussi
- [Empaqueter et déployer des solutions SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
