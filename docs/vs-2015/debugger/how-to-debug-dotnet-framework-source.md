---
title: 'Comment : déboguer une Source de .NET Framework | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging, .NET Framework source
ms.assetid: fc12e472-ac6a-4e77-8e22-a769e13a03b8
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 250c2bd633a4f6c6b0580b23d0fbf1bb25094247
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47493321"
---
# <a name="how-to-debug-net-framework-source"></a>Comment : déboguer une source .NET Framework
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [Comment : déboguer une Source de .NET Framework](https://docs.microsoft.com/visualstudio/debugger/how-to-debug-dotnet-framework-source).  
  
La version la plus récente de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] fournit de nouvelles fonctionnalités pour [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] le débogage. Pour déboguer [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] source, vous devez avoir accès aux symboles de débogage pour le code. Vous devez également activer le pas à pas détaillé dans [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] source.  
  
 Vous pouvez activer [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] pas à pas détaillé et le symbole de téléchargement dans le **Options** boîte de dialogue. Lorsque vous activez le téléchargement de symboles, vous avez la possibilité de télécharger des symboles immédiatement ou ultérieurement. Si vous ne les téléchargez pas tout de suite, les symboles seront téléchargés lors du prochain débogage de l'application. Vous pouvez également effectuer un téléchargement manuel à partir de la **Modules** fenêtre ou le **pile des appels** fenêtre.  
  
### <a name="to-enable-net-framework-source-debugging"></a>Pour activer le débogage d'une source .NET Framework  
  
1.  Sur le **outils** menu, cliquez sur **Option**s.  
  
2.  Dans le **Options** boîte de dialogue, cliquez sur le **débogage** catégorie.  
  
3.  Dans le **général** , définissez **activer .NET Framework** pas à pas détaillé de la source.  
  
    1.  Si l'option Uniquement mon code était activée, une boîte de dialogue d'avertissement s'affiche pour signaler que cette option est à présent désactivée. Cliquez sur **OK**.  
  
    2.  Si aucun emplacement du cache de symboles n'est défini, une autre boîte de dialogue d'avertissement s'affiche pour signaler qu'un emplacement du cache de symboles par défaut est à présent défini. Cliquez sur **OK**.  
  
4.  Sous le **débogage** catégorie, cliquez sur **symboles**.  
  
5.  Si vous souhaitez modifier l'emplacement du cache de symboles :  
  
    1.  Ouvrez le **débogage** nœud dans la zone située à gauche.  
  
    2.  Sous le **débogage** nœud, cliquez sur **symboles**.  
  
    3.  Modifier l’emplacement dans **en Cache les symboles à partir des serveurs de symboles dans ce répertoire** ou cliquez sur **Parcourir** à choisir un emplacement.  
  
6.  Si vous souhaitez télécharger des symboles immédiatement, cliquez sur **à l’aide de charger les symboles emplacements ci-dessus**.  
  
     Ce bouton n'est pas disponible en mode Design.  
  
     Si vous ne téléchargez pas les symboles maintenant, ils seront téléchargés automatiquement lors du prochain débogage du programme.  
  
7.  Cliquez sur **OK** pour fermer la boîte de dialogue **Options**.  
  
### <a name="to-load-framework-symbols-using-the-modules-window"></a>Pour charger des symboles Framework à l'aide de la fenêtre Modules  
  
1.  Dans le **Modules** fenêtre, avec le bouton droit un module pour lequel des symboles ne sont pas chargés. Vous pouvez indiquer si les symboles sont chargés ou non en examinant le **état du symbole** colonne.  
  
2.  Pointez sur **charger les symboles depuis** et cliquez sur **serveurs de symboles Microsoft** pour télécharger des symboles à partir du serveur de symboles publics Microsoft ou **chemin des symboles** pour charger à partir d’un répertoire où vous avez stocké des symboles.  
  
### <a name="to-load-framework-symbols-using-the-call-stack-window"></a>Pour charger des symboles Framework à l'aide de la fenêtre Pile des appels  
  
1.  Dans le **pile des appels** fenêtre, avec le bouton droit une frame pour lequel des symboles ne sont pas chargés. La frame est grisée.  
  
2.  Pointez sur **charger les symboles depuis** et cliquez sur **serveurs de symboles Microsoft** ou **chemin des symboles**.  
  
## <a name="see-also"></a>Voir aussi  
 [Débogage du code managé](../debugger/debugging-managed-code.md)   
 [Spécifier les fichiers de symbole (.pdb) et les fichiers sources](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)



