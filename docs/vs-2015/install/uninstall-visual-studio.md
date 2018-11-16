---
title: Désinstaller Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- uninstalling
- uninstalling visual studio
- uninstall
- uninstall Visual Studio
ms.assetid: 0e445255-b796-426d-ad93-a4d8e36da2c5
caps.latest.revision: 9
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.openlocfilehash: 81c01e96478ca83c546670897ab63e4eee64033f
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51777823"
---
# <a name="uninstall-visual-studio"></a>Désinstaller Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pour la documentation la plus récente pour Visual Studio 2017, consultez [désinstaller Visual Studio 2017](https://docs.microsoft.com/visualstudio/install/uninstall-visual-studio).

Cette page vous guide tout au long de la désinstallation de Visual Studio 2015, une version antérieure de notre suite intégrée d’outils de productivité pour les développeurs.  
  
##  <a name="uninstalling"></a>   
#### <a name="to-uninstall-visual-studio-by-using-the-standard-uninstallation-method"></a>Pour désinstaller Visual Studio à l’aide de la méthode de désinstallation « standard »  
  
1. Dans **le panneau de configuration**, dans le **programmes et fonctionnalités** page, sélectionnez l’édition du produit que vous souhaitez désinstaller, puis choisissez **modification**.  
  
2. Dans l’Assistant installation, choisissez **désinstallation**, choisissez **Oui**, puis suivez les instructions restantes de l’Assistant.  
  
   Cette méthode standard ou par défaut laisse certains éléments inférieur à celui de votre première installation de Visual Studio installé à l’origine (par exemple, le Microsoft .NET Framework, Microsoft Visual C++ redistribuables, Microsoft SQL Server, etc.).   Nous laissons installés parce que de nombreuses autres applications les utilisent. Toutefois, si vous souhaitez supprimer également, sélectionnez leur entrée dans **programmes et fonctionnalités**, puis supprimez-les individuellement.  
  
#### <a name="to-uninstall-visual-studio-and-all-other-related-files-that-is-to-uninstall-almost-everything"></a>Pour désinstaller Visual Studio et tous les autres fichiers associés (autrement dit, pour désinstaller presque tout)  
  
1.  Recherchez le fichier .exe de Visual Studio (par exemple, recherchez « vs_enterprise.exe »).  
  
    > [!NOTE]
    >  Le fichier doit être dans un sous-dossier de « %ProgramData%\Package Cache », par exemple : C:\ProgramData\Package Cache\\{37e19555-e88d-4aed-9d42-82d0784d2b79} \vs_enterprise.exe  
  
2.  Exécutez le fichier .exe à l’aide de la désinstaller /force des paramètres de ligne de commande.  
  
     Par exemple, exécutez ```vs_enterprise.exe /uninstall /force```, ce qui supprimera Visual Studio et la plupart des principaux composants qui sont conservés dans une désinstallation par défaut. Toutefois, il ne supprimera pas tout le contenu supplémentaire que les modules complémentaires de Visual Studio et extensions peuvent installer (par exemple, les mises à jour de Visual Studio et les autres composants facultatifs).  
  
    > [!TIP]
    > Vous pouvez également utiliser le «**désinstallation complète**» de l’outil pour supprimer tous les éléments que Visual Studio ou de mises à jour de Visual Studio a installé. Autrement dit, n’importe quelle version de Visual Studio 2013 ou version ultérieure. Pour plus d’informations, consultez le [outil de désinstallation de Visual Studio](https://github.com/Microsoft/VisualStudioUninstaller/releases) sur GitHub.  
  
#### <a name="to-uninstall-visual-studio-in-silent-or-passive-modes-that-is-to-uninstall-from-source"></a>Pour désinstaller Visual Studio en mode silencieux ou passif (autrement dit, pour désinstaller à partir de la source)  
  
1.  Sur l'ordinateur où Visual Studio est installé, ouvrez l'invite de commandes Windows.  
  
2.  Entrez les paramètres suivants :  
  
     *DVDRoot* \\< fichier d’Installation\> \</quiet/&#124;/passive > [/norestart] /Uninstall  
  
#### <a name="to-roll-back-to-a-previous-version-or-release-of--visual-studio"></a>Pour revenir à une version précédente ou la version de Visual Studio  
  
1. Désinstaller Visual Studio à l’aide des méthodes répertoriées dans cette rubrique.  
  
   > [!WARNING]
   >  Désinstallation d’une version actuelle de Visual Studio (ou un Visual Studio Update) et puis en installant une version précédente peuvent ne pas fonctionner comme prévu.  
   >   
   >  Le résultat dépend de la version ou la version de Visual Studio que vous avez installé, les versions de ses composants sont installées, des produits installés qui pourraient présenter des dépendances soit la version de Visual Studio ou ses composants, et enfin, sur quelle version antérieure de Visual Studio que vous souhaitez installer ou réinstaller.  En raison de toutes ces variables, une désinstallation standard est souvent des composants de laisser derrière qui peut ne pas fonctionnent avec les versions ou des versions antérieures de Visual Studio.  
   >   
   >  Par conséquent, pour de meilleurs résultats, nous vous recommandons d’utiliser le [outil de désinstallation de Visual Studio](https://github.com/Microsoft/VisualStudioUninstaller/releases).  
  
2. Installez ou réinstallez la version antérieure de Visual Studio que vous souhaitez utiliser.  
  
   Même si vous installez une version antérieure de Visual Studio, le programme d’installation peut toujours essayer à utiliser une version plus récente ou release si celle-ci est disponible. Pour plus d’informations, consultez le [Comment : installer une version spécifique de Visual Studio](../install/how-to-install-a-specific-release-of-visual-studio.md) rubrique.  
  
## <a name="see-also"></a>Voir aussi  
 [Installer Visual Studio](https://msdn.microsoft.com/library/e2h7fzkw.aspx)