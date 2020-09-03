---
title: 'Comment : déboguer .NET Framework source | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging, .NET Framework source
ms.assetid: fc12e472-ac6a-4e77-8e22-a769e13a03b8
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 49b13b8406dc96e8e7ebe5e79e26c5da02e8a53a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68205447"
---
# <a name="how-to-debug-net-framework-source"></a>Comment : déboguer une source .NET Framework
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La version la plus récente de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] fournit de nouvelles fonctionnalités pour le [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] débogage. Pour déboguer [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] la source, vous devez avoir accès aux symboles de débogage pour le code. Vous devez également activer le pas à pas détaillé dans la [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] source.  
  
 Vous pouvez activer [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] le téléchargement de symboles et d’exécution pas à pas dans la boîte de dialogue **options** . Lorsque vous activez le téléchargement de symboles, vous avez la possibilité de télécharger des symboles immédiatement ou ultérieurement. Si vous ne les téléchargez pas tout de suite, les symboles seront téléchargés lors du prochain débogage de l'application. Vous pouvez également effectuer un téléchargement manuel à partir de la fenêtre **modules** ou de la fenêtre **pile des appels** .  
  
### <a name="to-enable-net-framework-source-debugging"></a>Pour activer le débogage d'une source .NET Framework  
  
1. Dans le menu **Outils** , cliquez sur **Options**.  
  
2. Dans la boîte de dialogue **options** , cliquez sur la catégorie **débogage** .  
  
3. Dans la zone **général** , définissez **activer** l’exécution pas à pas de la source .NET Framework.  
  
    1. Si l'option Uniquement mon code était activée, une boîte de dialogue d'avertissement s'affiche pour signaler que cette option est à présent désactivée. Cliquez sur **OK**.  
  
    2. Si aucun emplacement du cache de symboles n'est défini, une autre boîte de dialogue d'avertissement s'affiche pour signaler qu'un emplacement du cache de symboles par défaut est à présent défini. Cliquez sur **OK**.  
  
4. Sous la catégorie **débogage** , cliquez sur **symboles**.  
  
5. Si vous souhaitez modifier l'emplacement du cache de symboles :  
  
    1. Ouvrez le nœud **débogage** dans la zone à gauche.  
  
    2. Sous le nœud **débogage** , cliquez sur **symboles**.  
  
    3. Modifiez l’emplacement dans le **cache symboles des serveurs de symboles vers ce répertoire** ou cliquez sur **Parcourir** pour choisir un emplacement.  
  
6. Si vous souhaitez télécharger des symboles immédiatement, cliquez sur **charger les symboles à l’aide des emplacements ci-dessus**.  
  
     Ce bouton n'est pas disponible en mode Design.  
  
     Si vous ne téléchargez pas les symboles maintenant, ils seront téléchargés automatiquement lors du prochain débogage du programme.  
  
7. Cliquez sur **OK** pour fermer la boîte de dialogue **Options** .  
  
### <a name="to-load-framework-symbols-using-the-modules-window"></a>Pour charger des symboles Framework à l'aide de la fenêtre Modules  
  
1. Dans la fenêtre **modules** , cliquez avec le bouton droit sur un module pour lequel des symboles ne sont pas chargés. Vous pouvez déterminer si les symboles sont chargés ou non en consultant la colonne **État des symboles** .  
  
2. Pointez sur **charger les symboles à partir de** , puis cliquez sur serveurs de symboles **Microsoft** pour télécharger des symboles à partir du serveur de symboles publics Microsoft ou du chemin d' **accès** aux symboles pour charger à partir d’un répertoire dans lequel vous avez déjà stocké des symboles.  
  
### <a name="to-load-framework-symbols-using-the-call-stack-window"></a>Pour charger des symboles Framework à l'aide de la fenêtre Pile des appels  
  
1. Dans la fenêtre **pile des appels** , cliquez avec le bouton droit sur un frame pour lequel des symboles ne sont pas chargés. La frame est grisée.  
  
2. Pointez sur **charger les symboles à partir de** , puis cliquez sur **serveurs de symboles Microsoft** ou **chemin d’accès**aux symboles.  
  
## <a name="see-also"></a>Voir aussi  
 [Débogage de code managé](../debugger/debugging-managed-code.md)   
 [Spécifier les fichiers de symboles (.pdb) et les fichiers source](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
