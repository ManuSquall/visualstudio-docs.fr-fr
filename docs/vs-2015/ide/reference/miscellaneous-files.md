---
title: Fichiers divers | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.newfile
- VS.OpenWith
- MiscellaneousFilesProject
helpviewer_keywords:
- solutions, miscellaneous files
- builds [Visual Studio], miscellaneous files
- standalone files
- Solution Explorer, miscellaneous files
- Miscellaneous Files folder
- files [Visual Studio], outside of containers
- files [Visual Studio], Miscellaneous Files folder
ms.assetid: 5b96640b-8efe-48a4-8d0a-1ae3f9587e44
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: cb9c7fb46517ff2d6dffdeb0cedfc4982c1f3366
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49258479"
---
# <a name="miscellaneous-files"></a>Fichiers divers
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Vous pouvez utiliser les éditeurs [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] pour utiliser indépendamment les fichiers d’un projet ou d’une solution. Dans une solution ouverte, vous pouvez ouvrir et modifier des fichiers sans les ajouter à une solution ou un projet. Les fichiers que vous voulez utiliser indépendamment des conteneurs sont appelés fichiers divers. Les fichiers divers sont externes aux solutions et projets, et ne sont pas inclus dans les générations. Ils ne peuvent pas être inclus dans une solution sous contrôle de code source.  
  
 L’ouverture de fichiers indépendamment d’un conteneur est utile pour diverses raisons. Par exemple, vous voulez afficher un fichier pendant le développement d’une solution basée sur un projet, qui ne fait pas partie du développement de la solution. Il s’agit souvent de remarques ou d’instructions concernant le développement, de schéma de base de données et d’extraits de code. Autre exemple, vous voulez créer un fichier autonome.  
  
 ![Projets de solutions](../../ide/reference/media/projects-solutions-misc.gif "Projects_Solutions_Misc")  
  
 L’Explorateur de solutions peut afficher un dossier Fichiers divers si les options du dossier sont activées. Les options peuvent être définies dans [Documents, Environnement, boîte de dialogue Options](../../ide/reference/documents-environment-options-dialog-box.md). Une fois que vous fermez un fichier divers, il n’est associé à aucune solution ou projet particulier, sauf si une option est activée dans ce but.  
  
 Le dossier Fichiers divers représente les fichiers sous forme de liens. Bien que ce dossier ne fasse pas partie d’une solution, quand vous ouvrez une solution, tout ou partie des fichiers divers qui étaient ouverts lors de la dernière fermeture de la solution sont rouverts, selon les paramètres définis pour le dossier.  
  
> [!NOTE]
>  Certains fichiers qui n’apparaissent pas dans le dossier Fichiers divers sont ceux que vous ne pouvez pas modifier dans l’IDE, comme les fichiers .zip et les fichiers .doc. L’IDE n’effectue pas le suivi des fichiers qui ne peuvent être modifiés par un éditeur externe.  
  
## <a name="commands-available-in-the-ide"></a>Commandes disponibles dans l’IDE  
 Les menus, les barres d’outils et les commandes qu’ils contiennent changent selon le format du fichier que vous ouvrez. Quand vous ouvrez un fichier texte, par exemple, la barre d’outils Éditeur de texte apparaît et ses commandes sont disponibles. Si vous ouvrez un fichier de schéma XML, la barre d’outils du schéma XML s’affiche. Quand vous modifiez votre schéma XML, les commandes de la barre d’outils Éditeur de texte (ou la barre d’outils elle-même) ne sont pas disponibles. Le schéma XML est la fenêtre active. De ce fait, il hérite du contexte de sélection actuel. Quand vous passez d’un fichier projet à un fichier divers, toutes les commandes associées au projet disparaissent et seules celles directement associées au fichier divers s’affichent.  
  
## <a name="folder-display-options"></a>Options d’affichage du dossier  
 Vous pouvez définir les options d’affichage du dossier divers pour qu’il s’affiche même si vous n’avez pas ouvert de fichier divers. Le fichier solution ne gère pas la liste des fichiers divers de façon permanente. Il utilise une fonctionnalité facultative qui lui permet de se rappeler la liste des fichiers récemment utilisés par l’utilisateur.  
  
## <a name="see-also"></a>Voir aussi  
 [Projets et solutions](../../ide/solutions-and-projects-in-visual-studio.md)   
 [Documents, Environnement, boîte de dialogue Options](../../ide/reference/documents-environment-options-dialog-box.md)



