---
title: Comment installer le profileur autonome | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- performance tools, installing stand-alone profiler
- profiling tools, stand-alone profiler
ms.assetid: cae81c95-83cd-4ab6-8a98-84ef977a2f6d
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 950927510d4c7acd77db22e80dff59946c0d6c20
ms.sourcegitcommit: 57d96de120e0574e506dfd80bb7adfbac73f96be
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85330137"
---
# <a name="how-to-install-the-stand-alone-profiler"></a>Guide pratique pour installer le profileur autonome
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] fournit un profileur autonome basé sur la ligne de commande qui peut être exécuté sans installer l’IDE [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Cette situation se produit quand un environnement de développement n’est pas ou ne peut pas être installé sur un ordinateur. Par exemple, vous ne devez pas installer un environnement de développement sur un serveur web de production.

> [!NOTE]
> Quand vous utilisez le profileur autonome pour collecter des données de performances pour un site web ASP.NET, l’outil en ligne de commande [VSPerfASPNetCmd](../profiling/vsperfaspnetcmd.md) est préférable à l’outil [VSPerfCmd](../profiling/vsperfcmd.md).

### <a name="to-install-the-stand-alone-profiler"></a>Pour installer le profileur autonome

1. Téléchargez les [Outils d’analyse des performances pour Visual Studio](https://visualstudio.microsoft.com/downloads/?q=performance+tools#performance-tools-for-visual-studio).

1. Recherchez le programme d’installation de profil autonome (*vs_standaloneprofiler.exe*) où vous avez téléchargé les outils d’analyse des performances et exécutez-le.

2. Ajoutez le chemin d’accès pour *vsinstr.exe* au chemin d’accès système.

   > [!NOTE]
   > Pour obtenir le chemin des outils de profilage, consultez [Spécifier le chemin des outils en ligne de commande](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Les versions 64 bits et 32 bits des outils sont disponibles sur les ordinateurs 64 bits. Pour utiliser les outils en ligne de commande du profileur, vous devez ajouter le chemin des outils à la variable d’environnement PATH dans la fenêtre d’invite de commandes, ou l’ajouter à la commande.

3. À l’invite de commandes, entrez **VSInstr**.

   > [!NOTE]
   > Si les informations d’utilisation pour vsinstr.exe s’affichent, c’est que tout est configuré correctement. Si vous voyez une erreur indiquant que vsinstr.exe ou une de ses dépendances est introuvable, vérifiez que vos chemins sont correctement configurés, comme décrit à l’étape 2.

4. Configurez le serveur de symboles en affectant à votre variable **_NT_SYMBOL_PATH** la valeur **symsrv\*symsrv.dll\*c:\localcache\*https://msdl.microsoft.com/download/symbols**

5. Après avoir configuré votre serveur de symboles avec les variables d’environnement système, exécutez les outils du profileur en ligne de commande à une nouvelle invite de commandes. Les nouvelles variables d’environnement sont ainsi prises en compte. Dans la fenêtre d’invite de commandes, tapez la commande suivante :

    **start %COMSPEC%**

   > [!NOTE]
   > Pour obtenir des instructions détaillées sur la façon de configurer le package du serveur de symboles, consultez [Guide pratique pour référencer les informations de symboles Windows](../profiling/how-to-reference-windows-symbol-information.md).

6. Utilisez l’outil [VSPerfReport](../profiling/vsperfreport.md) pour sérialiser vos symboles dans le fichier de profilage de données (.vsp). Utilisez les commutateurs **VSPerfReport /summary:all /packsymbols**. Si aucun symbole n’est inséré dans votre fichier de données, vérifiez que la variable d’environnement _NT_SYMBOL_PATH est définie.

## <a name="see-also"></a>Voir aussi
- [Profiler à partir de la ligne de commande](../profiling/using-the-profiling-tools-from-the-command-line.md)
- [Procédure pas à pas : profilage à partir de la ligne de commande à l’aide d’instrumentation](command-line-profiling-of-stand-alone-applications.md)
- [Comment : référencer les informations de symboles Windows](../profiling/how-to-reference-windows-symbol-information.md)
- [VSPerfReport](../profiling/vsperfreport.md)
