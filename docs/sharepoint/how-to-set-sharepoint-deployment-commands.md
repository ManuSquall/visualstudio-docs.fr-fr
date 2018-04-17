---
title: 'Comment : définir des commandes de déploiement SharePoint | Documents Microsoft'
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
- SharePoint development in Visual Studio, deploying
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 8779ba4ee4cf9803982d9849b3af7c83930d8a5b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-set-sharepoint-deployment-commands"></a>Comment : définir des commandes de déploiement SharePoint
  Vous pouvez personnaliser le processus de déploiement en définissant des commandes de prédéploiement et de post-déploiement. Ces commandes s’exécutent avant et après les autres actions de déploiement lorsque vous déboguez des solutions SharePoint à partir de Visual Studio.  
  
### <a name="to-add-a-pre-deployment-command"></a>Pour ajouter une commande de prédéploiement  
  
1.  Dans la barre de menus, choisissez **projet**, * NomProjet ***propriétés**.  
  
2.  Choisissez le **SharePoint** onglet.  
  
3.  Dans le **ligne de commande de prédéploiement** texte, entrez les commandes MS-DOS ou MSBuild pour personnaliser cette étape.  
  
     Par exemple, pour répertorier le contenu du répertoire avant la fin de déploiement, entrez **dir**.  
  
### <a name="to-add-a-post-deployment-command"></a>Pour ajouter une commande de post-déploiement  
  
1.  Dans la barre de menus, choisissez **projet**, * NomProjet ***propriétés**.  
  
2.  Choisissez le **SharePoint** onglet.  
  
3.  Dans le **ligne de commande de post-déploiement** texte, entrez les commandes MS-DOS ou MSBuild pour personnaliser cette étape.  
  
     Par exemple, pour répertorier le contenu du répertoire une fois le déploiement terminé, entrez **dir**. Pour utiliser une variable de MSBuild pour copier l’assembly à partir du répertoire de build, entrez **copier $ (TargetPath) c:\DeploymentDirectory**.  
  
## <a name="see-also"></a>Voir aussi  
 [Empaquetage et déploiement de solutions SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  