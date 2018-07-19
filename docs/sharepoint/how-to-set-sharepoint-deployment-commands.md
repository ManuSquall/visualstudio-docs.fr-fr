---
title: 'Comment : définir des commandes de déploiement SharePoint | Microsoft Docs'
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
ms.openlocfilehash: 060acd0164ff7819d2abfb8d92f2394b4bcc0672
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37119247"
---
# <a name="how-to-set-sharepoint-deployment-commands"></a>Comment : commandes de déploiement SharePoint de jeu
  Vous pouvez personnaliser le processus de déploiement en définissant des commandes de prédéploiement et de post-déploiement. Ces commandes s’exécutent avant et après les autres actions de déploiement lorsque vous déboguez des solutions SharePoint à partir de Visual Studio.  
  
### <a name="to-add-a-pre-deployment-command"></a>Pour ajouter une commande de prédéploiement  
  
1.  Dans la barre de menus, choisissez **projet** > **\<*nom_projet*> Propriétés**.  
  
2.  Choisissez le **SharePoint** onglet.  
  
3.  Dans le **ligne de commande de prédéploiement** texte, entrez les commandes MS-DOS ou MSBuild pour personnaliser cette étape.  
  
     Par exemple, pour répertorier le contenu du répertoire avant la fin de déploiement, entrez **dir**.  
  
### <a name="to-add-a-post-deployment-command"></a>Pour ajouter une commande de post-déploiement  
  
1.  Dans la barre de menus, choisissez **projet** > **\<*nom_projet*> Propriétés**.  
  
2.  Choisissez le **SharePoint** onglet.  
  
3.  Dans le **ligne de commande de post-déploiement** texte, entrez les commandes MS-DOS ou MSBuild pour personnaliser cette étape.  
  
     Par exemple, pour répertorier le contenu du répertoire une fois le déploiement terminé, entrez **dir**. Pour utiliser une variable MSBuild pour copier l’assembly à partir du répertoire de build, entrez **copier $ (TargetPath) c:\DeploymentDirectory**.  
  
## <a name="see-also"></a>Voir aussi
 [Empaqueter et déployer des solutions SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
