---
title: Modifications requises pour exécuter les projets Office que vous migrez vers le .NET Framework 4 ou .NET Framework 4.5
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
ms.openlocfilehash: 0f4add2a01a9fd26fe5479bbf6ba54f25e8b2e14
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56625697"
---
# <a name="required-changes-to-run-office-projects-that-you-migrate-to-the-net-framework-4-or-the-net-framework-45"></a>Modifications requises pour exécuter les projets Office que vous migrez vers le .NET Framework 4 ou .NET Framework 4.5
  Si le framework cible d’un projet Office est remplacé par la [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou version ultérieure à partir d’une version antérieure du .NET Framework, vous devez effectuer les tâches suivantes pour vous assurer que la solution puisse s’exécuter sur l’ordinateur de développement et sur les ordinateurs des utilisateurs finaux :

- Supprimez l'élément <xref:System.Security.SecurityTransparentAttribute> du projet si vous avez effectué une mise à niveau à partir de Visual Studio 2008.

- Effectuer un **Clean** commande dans Visual Studio pour être en mesure d’exécuter ou déboguer le projet sur l’ordinateur de développement.

- Mettez à jour le composant requis .NET Framework du projet.

- Les utilisateurs finaux doivent également réinstaller la solution si vous l'avez précédemment déployée à l'aide de ClickOnce avant d'avoir changé la version cible de .NET Framework.

  Pour plus d’informations sur chacune de ces tâches, consultez les sections correspondantes ci-dessous.

## <a name="remove-the-securitytransparent-attribute-from-projects-that-you-upgrade-from-visual-studio-2008"></a>Supprimer l’attribut SecurityTransparent des projets que vous mettez à niveau à partir de Visual Studio 2008
 Si vous mettez à niveau un projet Office à partir de Visual Studio 2008 et que la version cible de .Net Framework du projet est ensuite remplacée par [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou une version ultérieure, vous devez supprimer <xref:System.Security.SecurityTransparentAttribute> du projet. Visual Studio ne supprime pas automatiquement cet attribut. Si vous ne supprimez pas cet attribut, un message d'erreur s'affiche lorsque vous compilez le projet.

 Pour plus d’informations sur les conditions dans lesquelles Visual Studio peut modifier le framework cible d’un projet mis à niveau vers la [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], consultez [mise à niveau et migrer des solutions Office](../vsto/upgrading-and-migrating-office-solutions.md).

#### <a name="to-remove-the-securitytransparentattribute"></a>Pour supprimer l'attribut SecurityTransparentAttribute

1.  Le projet étant ouvert dans Visual Studio, ouvrez l' **Explorateur de solutions**.

2.  Sous le nœud **Propriétés** (pour C#) ou le nœud **My Project** (pour Visual Basic), double-cliquez sur le fichier de code AssemblyInfo pour l'ouvrir dans l'éditeur de code.

    > [!NOTE]
    >  Dans les projets Visual Basic, vous devez cliquer sur le bouton **Afficher tous les fichiers** de l' **Explorateur de solutions** pour afficher le fichier de code AssemblyInfo.

3.  Recherchez le <xref:System.Security.SecurityTransparentAttribute> et supprimez-le du fichier ou commentez-le.

    ```vb
    <Assembly: SecurityTransparent()>
    ```

    ```csharp
    [assembly: SecurityTransparent()]
    ```

## <a name="perform-the-clean-command-to-debug-or-run-a-project-on-the-development-computer"></a>Exécuter la commande clean pour déboguer ou exécuter un projet sur l’ordinateur de développement
 Si un projet Office a été créé avant que le framework cible du projet est modifié en le [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou version ultérieure, vous devez effectuer un **Clean** commande, puis régénérez le projet après la modification du framework cible. Si n’effectuent pas un **Clean** commande, vous recevrez un <xref:System.Runtime.InteropServices.COMException> lorsque vous essayez de déboguer ou exécuter le projet reciblé.

 Pour plus d’informations sur la **Clean** de commande, consultez [solutions Office Build](../vsto/building-office-solutions.md).

## <a name="update-the-prerequisites-for-deployment"></a>Mettre à jour les conditions préalables pour le déploiement
 Lorsque vous reciblez un projet Office vers [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou une version ultérieure, vous devez également mettre à jour les composants requis .NET Framework correspondants dans le **conditions préalables** boîte de dialogue. Sinon, le déploiement ClickOnce ou le projet InstallShield Limited Edition recherche et installe une version antérieure du .NET Framework.

 Pour plus d’informations sur la mise à jour de la configuration requise pour le déploiement pour les ordinateurs des utilisateurs finaux, consultez [Comment : Installer les composants requis sur les ordinateurs des utilisateurs finaux pour exécuter des solutions Office](https://msdn.microsoft.com/74dd2c52-838f-4abf-b2b4-4d7b0c2a0a98).

## <a name="reinstall-solutions-on-end-user-computers"></a>Réinstallation de solutions sur les ordinateurs des utilisateurs finaux
 Si vous utilisez ClickOnce pour déployer une solution Office qui cible .NET Framework 3.5, puis que vous reciblez le projet vers [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou une version ultérieure, les utilisateurs finaux doivent désinstaller la solution puis la réinstaller une fois que vous l'avez republiée. Si vous republiez la solution reciblée et si la solution est mis à jour sur les ordinateurs des utilisateurs finaux, les utilisateurs finaux recevront un <xref:System.Runtime.InteropServices.COMException> lorsqu’ils exécutent la solution mise à jour.

## <a name="see-also"></a>Voir aussi
- [Migrer des solutions Office vers .NET Framework 4 ou version ultérieure](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)
