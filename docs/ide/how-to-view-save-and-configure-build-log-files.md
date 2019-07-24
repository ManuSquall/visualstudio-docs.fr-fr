---
title: 'Procédure : afficher, enregistrer et configurer des fichiers journaux de génération | Microsoft Docs'
ms.date: 11/04/2016
ms.technology: vs-ide-compile
ms.topic: conceptual
ms.assetid: 75d38b76-26d6-4f43-bbe7-cbacd7cc81e7
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0dc172723005b6781a63b3a3956b12152d73bb0f
ms.sourcegitcommit: 59e5758036223ee866f3de5e3c0ab2b6dbae97b6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68415577"
---
# <a name="how-to-view-save-and-configure-build-log-files"></a>Procédure : Afficher, enregistrer et configurer des fichiers journaux de génération

Après avoir généré un projet dans l’IDE de Visual Studio, vous pouvez consulter les informations sur cette génération dans la fenêtre **Sortie**. Grâce à ces informations, vous pouvez déboguer un échec de génération, par exemple. 

- Pour les projets C++, vous pouvez également afficher les mêmes informations dans un fichier *.txt* créé et enregistré automatiquement. 

- Pour les projets de code managé, vous pouvez cliquer dans la fenêtre de sortie de build et appuyer sur **Ctrl**+**S**. Visual Studio vous invite à entrer un emplacement pour enregistrer les informations de la fenêtre **Sortie** dans un fichier *.txt*. 

Vous pouvez également utiliser l’IDE pour spécifier les types d’informations à afficher pour chaque génération.

Si vous générez un projet à l’aide de MSBuild, vous pouvez créer un fichier *.txt* pour y enregistrer les informations de build. Pour plus d’informations, consultez [Obtenir des journaux de génération](../msbuild/obtaining-build-logs-with-msbuild.md).

## <a name="to-view-the-build-log-file-for-a-c-project"></a>Pour afficher le fichier journal de génération d’un projet C++

1. Dans l’**Explorateur Windows** ou l’**Explorateur de fichiers**, ouvrez le fichier suivant : *\\...\Visual Studio \<Version\>\Projects\\<nom_projet\>\\<nom_projet\>\Debug\\<nom_projet\>.txt*

## <a name="to-create-a-build-log-file-for-a-managed-code-project"></a>Pour créer un fichier journal de génération d’un projet de code managé

1. Dans la barre de menus, choisissez **Générer**  >  **Générer la solution**.

2. Dans la fenêtre **Sortie**, cliquez quelque part dans le texte.

3. Appuyez sur **Ctrl**+**Tab**.

   Visual Studio vous invite à entrer un emplacement pour enregistrer la sortie de génération.

## <a name="to-change-the-amount-of-information-included-in-the-build-log"></a>Pour modifier la quantité d’informations contenues dans le journal de génération

1. Dans la barre de menus, choisissez **Outils** > **Options**.

2. Dans la page **Projets et solutions**, choisissez la page **Générer et exécuter**.

3. Dans la liste **Commentaires relatifs à la sortie de génération du projet MSBuild**, choisissez l’une des valeurs suivantes, puis choisissez le bouton **OK**.

    |Niveau de détail|Description|
    | - |-----------------|
    |**Silencieux**|Affiche uniquement un récapitulatif de la génération.|
    |**Minimale**|Affiche un récapitulatif de la génération, ainsi que les erreurs, avertissements et messages qui sont classés comme très importants.|
    |**Normal**|Affiche un récapitulatif de la génération ; les erreurs, avertissements et messages qui sont classés comme très importants ; et les principales étapes de la génération. Ce niveau de détail est celui que vous utiliserez le plus souvent.|
    |**Détaillé**|Affiche un récapitulatif de la génération ; les erreurs, avertissements et messages qui sont classés comme très importants ; toutes les étapes de la génération ; et les messages classés comme d’importance normale.|
    |**Diagnostic**|Affiche toutes les données disponibles sur la génération. Vous pouvez utiliser ce niveau de détail pour faciliter le débogage des problèmes liés aux scripts de génération personnalisée et d’autres problèmes de génération.|

     Pour plus d’informations, consultez [Options (boîte de dialogue), Projets et solutions, Générer et exécuter](../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md) et <xref:Microsoft.Build.Framework.LoggerVerbosity>.

    > [!IMPORTANT]
    > Vous devez regénérer le projet pour que vos modifications soient appliquées dans la fenêtre **Sortie** (tous les projets) et dans le fichier *\<nom_projet>.txt* (projets C++ uniquement).

## <a name="see-also"></a>Voir aussi

- [Obtenir des journaux de génération](../msbuild/obtaining-build-logs-with-msbuild.md)
- [Générer et nettoyer des solutions et des projets dans Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)
- [Compiler et générer](../ide/compiling-and-building-in-visual-studio.md)
