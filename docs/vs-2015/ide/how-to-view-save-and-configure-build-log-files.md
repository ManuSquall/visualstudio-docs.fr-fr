---
title: Guide pratique pour afficher, enregistrer et configurer des fichiers journaux de génération | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 75d38b76-26d6-4f43-bbe7-cbacd7cc81e7
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 496fcdf28f8ce9b0809988949d435c064734b508
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60053560"
---
# <a name="how-to-view-save-and-configure-build-log-files"></a>Comment : afficher, enregistrer et configurer des fichiers journaux de génération
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Après avoir généré un projet dans l’IDE de Visual Studio, vous pouvez consulter les informations sur cette génération dans la fenêtre **Sortie**. Grâce à ces informations, vous pouvez déboguer un échec de génération, par exemple. Pour les projets C++, vous pouvez également afficher les mêmes informations dans un fichier .txt qui est créé et enregistré automatiquement. Pour les projets de code managé, vous pouvez copier et coller les informations de la fenêtre **Sortie** dans un fichier .txt que vous enregistrez vous-même. Vous pouvez également utiliser l’IDE pour spécifier les types d’informations à afficher pour chaque génération.  
  
 Si vous générez tout type de projet à l’aide de MSBuild, vous pouvez créer un fichier .txt pour y enregistrer les informations de génération. Pour plus d’informations, consultez [Obtention de journaux de génération avec MSBuild](../msbuild/obtaining-build-logs-with-msbuild.md).  
  
### <a name="to-view-the-build-log-file-for-a-c-project"></a>Pour afficher le fichier journal de génération d’un projet C++  
  
1. Dans **l’Explorateur Windows** ou **l’Explorateur de fichiers**, ouvrez le fichier suivant : \\...\Visual Studio *Version*\Projects\\*nom_projet*\\*nom_projet*\Debug\\*nom_projet*.txt  
  
### <a name="to-create-a-build-log-file-for-a-managed-code-project"></a>Pour créer un fichier journal de génération d’un projet de code managé  
  
1. Dans la barre de menus, choisissez **Générer**, puis **Générer la solution**.  
  
2. Dans la fenêtre **Sortie**, mettez en surbrillance les informations de la génération, puis copiez-les dans le Presse-papiers.  
  
3. Ouvrez un éditeur de texte, tel que le bloc-notes, collez les informations dans le fichier, puis enregistrez le fichier.  
  
### <a name="to-change-the-amount-of-information-included-in-the-build-log"></a>Pour modifier la quantité d’informations contenues dans le journal de génération  
  
1. Dans la barre de menus, sélectionnez **Outils**, **Options**.  
  
2. Dans la page **Projets et solutions**, choisissez la page **Générer et exécuter**.  
  
3. Dans la liste **Commentaires relatifs à la sortie de génération du projet MSBuild**, choisissez l’une des valeurs suivantes, puis choisissez le bouton **OK**.  
  
    |Niveau de détail|Description|  
    |---------------------|-----------------|  
    |Quiet|Affiche uniquement un récapitulatif de la génération.|  
    |Minimal|Affiche un récapitulatif de la génération, ainsi que les erreurs, avertissements et messages qui sont classés comme très importants.|  
    |Normale|Affiche un récapitulatif de la génération ; les erreurs, avertissements et messages qui sont classés comme très importants ; et les principales étapes de la génération. Ce niveau de détail est celui que vous utiliserez le plus souvent.|  
    |Détaillé|Affiche un récapitulatif de la génération ; les erreurs, avertissements et messages qui sont classés comme très importants ; toutes les étapes de la génération ; et les messages classés comme d’importance normale.|  
    |Diagnostic|Affiche toutes les données disponibles sur la génération. Vous pouvez utiliser ce niveau de détail pour faciliter le débogage des problèmes liés aux scripts de génération personnalisée et d’autres problèmes de génération.|  
  
     Pour plus d’informations, consultez [Options (boîte de dialogue), Projets et solutions, Générer et exécuter](../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md) et <xref:Microsoft.Build.Framework.LoggerVerbosity>.  
  
    > [!IMPORTANT]
    >  Vous devez regénérer le projet pour que vos modifications soient appliquées dans la fenêtre **Sortie** (tous les projets) et le fichier *nom_projet*.txt (projets C++ uniquement).  
  
## <a name="see-also"></a>Voir aussi  
 [Obtention de journaux de génération](../msbuild/obtaining-build-logs-with-msbuild.md)   
 [Génération et nettoyage de solutions et de projets dans Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)   
 [Compilation et génération](../ide/compiling-and-building-in-visual-studio.md)
