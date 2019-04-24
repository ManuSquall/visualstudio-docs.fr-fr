---
title: Guide pratique pour modifier le répertoire de sortie de la génération | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- output directory, changing
ms.assetid: a8333c89-afb2-4b1d-b2e2-9146da852402
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: b2e1fd8e54d34d8998158781c9de67d2e3a8cf01
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60104861"
---
# <a name="how-to-change-the-build-output-directory"></a>Guide pratique pour modifier le répertoire de sortie de la génération
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez spécifier l’emplacement de sortie en fonction de la configuration (débogage, version ou les deux) généré par votre projet.  
  
> [!NOTE]
>  Si vous possédez un **projet d’installation** , lisez la remarque à la fin de cet article.  
  
## <a name="changing-the-build-output-directory"></a>Modification du répertoire de sortie de génération  
  
#### <a name="to-change-the-build-output-directory"></a>Pour modifier le répertoire de sortie de génération  
  
1. Dans la barre de menus, choisissez **Projet**, *Propriétés* **nom_application**. Vous pouvez également cliquer avec le bouton droit sur le nœud du projet dans l' **Explorateur de solutions** , puis sélectionner **Propriétés**.  
  
2. Si vous avez un projet Visual Basic, sélectionnez l'onglet **Compiler** . Si vous avez un projet Visual C#, sélectionnez l'onglet **Générer** . Si vous avez un projet C++ ou un projet JavaScript, sélectionnez l'onglet **Général** .  
  
3. Dans la liste déroulante de configuration située dans la partie supérieure, choisissez la configuration pour laquelle vous voulez modifier l’emplacement du fichier de sortie (débogage, version ou tout).  
  
     Recherchez l'entrée de chemin de sortie (**Chemin de sortie de la génération** en Visual Basic, **Répertoire de sortie** en Visual C++, **Chemin de sortie** en JavaScript et C#). Spécifiez un nouveau répertoire de sortie de génération relatif au répertoire du projet.  
  
> [!NOTE]
>  Dans un projet d’installation, la zone **Nom du fichier de sortie** permet uniquement de modifier l’emplacement du fichier Setup.exe, et non l’emplacement des fichiers du projet. Pour plus d'informations, consultez **Build, propriétés de configuration, boîte de dialogue Propriétés du projet de déploiement**.  
  
## <a name="see-also"></a>Voir aussi  
 [Générer, page du Concepteur de projets (C#)](../ide/reference/build-page-project-designer-csharp.md)   
 [Général, page de propriétés (Projet)](http://msdn.microsoft.com/library/593b383c-cd0f-4dcd-ad65-9ec9b4b19c45)   
 [Compilation et génération](../ide/compiling-and-building-in-visual-studio.md)
