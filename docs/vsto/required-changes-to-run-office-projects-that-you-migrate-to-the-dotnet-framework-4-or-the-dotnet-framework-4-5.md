---
title: Modifications requises pour les projets Office migrés vers .NET 4,5
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office projects [Office development in Visual Studio], migrating to .NET Framework 4
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 40db3cd629f2c3a2ced37a781dea3244a3f19957
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91584462"
---
# <a name="changes-required-for-office-projects-migrated-to-net-45"></a>Modifications requises pour les projets Office migrés vers .NET 4,5

  Si la version cible du .NET Framework d’un projet Office est remplacée par la [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] version ou ultérieure d’une version antérieure du .NET Framework, vous devez effectuer les tâches suivantes pour vous assurer que la solution peut s’exécuter sur l’ordinateur de développement et sur les ordinateurs des utilisateurs finaux :

- Supprimez l'élément <xref:System.Security.SecurityTransparentAttribute> du projet si vous avez effectué une mise à niveau à partir de Visual Studio 2008.

- Exécutez une commande **Clean** dans Visual Studio pour être en mesure d’exécuter ou de déboguer le projet sur l’ordinateur de développement.

- Mettez à jour le composant requis .NET Framework du projet.

- Les utilisateurs finaux doivent également réinstaller la solution si vous l'avez précédemment déployée à l'aide de ClickOnce avant d'avoir changé la version cible de .NET Framework.

  Pour plus d'informations sur chacune de ces tâches, consultez les sections correspondantes ci-dessous.

## <a name="remove-the-securitytransparent-attribute-from-projects-that-you-upgrade-from-visual-studio-2008"></a>Supprimer l’attribut SecurityTransparent des projets que vous mettez à niveau à partir de Visual Studio 2008
 Si vous mettez à niveau un projet Office à partir de Visual Studio 2008 et que la version cible de .Net Framework du projet est ensuite remplacée par [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou une version ultérieure, vous devez supprimer <xref:System.Security.SecurityTransparentAttribute> du projet. Visual Studio ne supprime pas automatiquement cet attribut. Si vous ne supprimez pas cet attribut, un message d'erreur s'affiche lorsque vous compilez le projet.

 Pour plus d’informations sur les conditions dans lesquelles Visual Studio peut modifier la version cible du .NET Framework d’un projet mis à niveau vers [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] , consultez [mettre à niveau et migrer des solutions Office](../vsto/upgrading-and-migrating-office-solutions.md).

#### <a name="to-remove-the-securitytransparentattribute"></a>Pour supprimer l'attribut SecurityTransparentAttribute

1. Le projet étant ouvert dans Visual Studio, ouvrez l' **Explorateur de solutions**.

2. Sous le nœud **Propriétés** (pour C#) ou le nœud **My Project** (pour Visual Basic), double-cliquez sur le fichier de code AssemblyInfo pour l'ouvrir dans l'éditeur de code.

    > [!NOTE]
    > Dans les projets Visual Basic, vous devez cliquer sur le bouton **Afficher tous les fichiers** de l' **Explorateur de solutions** pour afficher le fichier de code AssemblyInfo.

3. Recherchez le <xref:System.Security.SecurityTransparentAttribute> et supprimez-le du fichier ou commentez-le.

    ```vb
    <Assembly: SecurityTransparent()>
    ```

    ```csharp
    [assembly: SecurityTransparent()]
    ```

## <a name="perform-the-clean-command-to-debug-or-run-a-project-on-the-development-computer"></a>Exécuter la commande nettoyer pour déboguer ou exécuter un projet sur l’ordinateur de développement
 Si un projet Office a été généré avant la modification de la version cible du .NET Framework du projet [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] , vous devez exécuter une commande **Clean** , puis régénérer le projet après la modification du Framework cible. Si vous n’exécutez pas une commande **Clean** , vous recevrez un <xref:System.Runtime.InteropServices.COMException> lorsque vous essaierez de déboguer ou d’exécuter le projet reciblé.

 Pour plus d’informations sur la commande **Clean** , consultez [créer des solutions Office](../vsto/building-office-solutions.md).

## <a name="update-the-prerequisites-for-deployment"></a>Mettre à jour les conditions préalables pour le déploiement
 Lorsque vous reciblez un projet Office vers [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou version ultérieure, vous devez également mettre à jour la condition préalable .NET Framework correspondante dans la boîte de dialogue **composants requis** . Sinon, le déploiement ClickOnce ou le projet InstallShield Limited Edition recherche et installe une version antérieure du .NET Framework.

 Pour plus d’informations sur la mise à jour des composants requis pour le déploiement sur les ordinateurs des utilisateurs finaux, consultez [procédure : installer les composants requis sur les ordinateurs des utilisateurs finaux pour exécuter des solutions Office](/previous-versions/bb608608(v=vs.110)).

## <a name="reinstall-solutions-on-end-user-computers"></a>Réinstaller des solutions sur les ordinateurs des utilisateurs finaux
 Si vous utilisez ClickOnce pour déployer une solution Office qui cible .NET Framework 3.5, puis que vous reciblez le projet vers [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou une version ultérieure, les utilisateurs finaux doivent désinstaller la solution puis la réinstaller une fois que vous l'avez republiée. Si vous republiez la solution reciblée et que la solution est mise à jour sur les ordinateurs des utilisateurs finaux, les utilisateurs finaux recevront un <xref:System.Runtime.InteropServices.COMException> lorsqu’ils exécuteront la solution mise à jour.

## <a name="see-also"></a>Voir aussi
- [Migrer des solutions Office vers le .NET Framework 4 ou version ultérieure](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)