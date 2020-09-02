---
title: Désinstaller Visual Studio 2015 │ Microsoft Docs
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-install
ms.topic: conceptual
f1_keywords:
- uninstalling
- uninstalling visual studio
- uninstall
- uninstall Visual Studio
ms.assetid: 0e445255-b796-426d-ad93-a4d8e36da2c5
caps.latest.revision: 9
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: ed9d33501644c6fa7252dffa758f92c0919653b1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62546900"
---
# <a name="uninstall-visual-studio"></a>Désinstaller Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pour consulter la documentation à jour sur Visual Studio, voir [Désinstaller Visual Studio](/visualstudio/install/uninstall-visual-studio).

Cette page explique comment désinstaller Visual Studio 2015, une ancienne version de notre suite intégrée d’outils de productivité pour les développeurs.

## <a name="uninstall-visual-studio-by-using-the-standard-uninstallation-method"></a>Désinstaller Visual Studio suivant la méthode de désinstallation « standard »

1. Dans le **Panneau de configuration**, dans la page **Programmes et fonctionnalités**, sélectionnez l’édition du produit que vous souhaitez désinstaller, puis cliquez sur **Modifier**.

2. Dans l’Assistant Installation, sélectionnez **Désinstaller**, choisissez **Oui**, puis suivez les instructions restantes de l’Assistant.

   Cette méthode standard ou par défaut laisse de côté certains éléments de la première installation de Visual Studio (par exemple, Microsoft .NET Framework, Redistributables Microsoft Visual C++, Microsoft SQL Server, etc.).   En effet, de nombreuses applications les utilisent. Si malgré cela vous souhaitez également les supprimer, sélectionnez leur entrée dans **Programmes et fonctionnalités**, puis supprimez-les un par un.

## <a name="uninstall-visual-studio-and-all-other-related-files-that-is-to-uninstall-almost-everything"></a>Désinstaller Visual Studio et tous les fichiers associés (soit presque tout)

1. Recherchez le fichier .exe de Visual Studio (par exemple, « vs_enterprise.exe »).

    > [!NOTE]
    > Le fichier devrait se trouver dans un sous-dossier de « %ProgramData%\Package Cache », par exemple : C:\ProgramData\Package Cache\\{37e19555-e88d-4aed-9d42-82d0784d2b79}\vs_enterprise.exe.

2. Exécutez le fichier .exe à l’aide des paramètres de ligne de commande /uninstall /force.

     Par exemple, exécutez ```vs_enterprise.exe /uninstall /force``` pour supprimer Visual Studio et la plupart des principaux composants laissés de côté dans le cadre d’une désinstallation par défaut. Cela ne supprime pas pour autant tout le contenu supplémentaire que les compléments et les extensions Visual Studio sont susceptibles d’installer (par exemple, les mises à jour de Visual Studio et autres composants facultatifs).

    > [!TIP]
    > Vous pouvez également utiliser l’outil « **Désinstallation complète** » pour supprimer tous les éléments potentiellement installés par Visual Studio ou ses mises à jour, autrement dit toutes les versions de Visual Studio jusqu’à Visual Studio 2013. Pour plus d’informations, voir [Outil de désinstallation de Visual Studio](https://github.com/Microsoft/VisualStudioUninstaller/releases) sur GitHub.

## <a name="uninstall-visual-studio-in-silent-or-passive-modes-that-is-to-uninstall-from-source"></a>Désinstaller Visual Studio en mode silencieux ou passif (autrement dit, à partir de la source)

1. Sur l'ordinateur où Visual Studio est installé, ouvrez l'invite de commandes Windows.

2. Entrez les paramètres suivants :

     *DVDRoot* \\ Fichier d’installation<\> \</quiet&#124;/passive> [/norestart]/Uninstall

## <a name="roll-back-to-a-previous-version-or-release-of--visual-studio"></a>Revenir à une version précédente de Visual Studio

1. Désinstallez Visual Studio en suivant l’une des méthodes de cette rubrique.

   > [!WARNING]
   > Il peut arriver que les résultats obtenus en désinstallant une version actuelle de Visual Studio (ou une mise à jour de Visual Studio) et en installant ensuite une version antérieure ne soient pas optimaux.
   >
   > Ils dépendent de la version installée de Visual Studio et de ses composants, des produits installés susceptibles de présenter des dépendances vis-à-vis de la version de Visual Studio ou de ses composants et, enfin, de la version antérieure de Visual Studio installée ou réinstallée.  Du fait de toutes ces variables, une désinstallation standard laisse souvent de côté des composants, qui risquent de ne pas fonctionner avec les versions antérieures de Visual Studio.
   >
   > Pour obtenir de meilleurs résultats, nous vous recommandons donc d’utiliser [l’outil de désinstallation de Visual Studio](https://github.com/Microsoft/VisualStudioUninstaller/releases).

2. Installez ou réinstallez la version antérieure de Visual Studio de votre choix.

   Même si vous installez une version antérieure de Visual Studio, le programme d’installation pourra essayer d’utiliser une version plus récente s’il en existe une. Pour plus d’informations, voir la rubrique [Guide pratique pour installer une version spécifique de Visual Studio](../install/how-to-install-a-specific-release-of-visual-studio.md).

## <a name="see-also"></a>Voir aussi

- [Installer Visual Studio](https://msdn.microsoft.com/library/e2h7fzkw.aspx)