---
title: 'Comment : déboguer du Code injecté | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.injected
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- assembly language, viewing
- debugging [C++], viewing assembly code
- debugging [C++], injected code
- debugging [C++], enabling source annotation
- injected code
- Show Source Code command [debugger]
- debugging [C++], using attributes
- disassembly code, debugging
ms.assetid: a1b4104d-d49e-451f-a91e-e39ceaf35875
caps.latest.revision: 20
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7ff81b082c877098acec78e56ef9ef211cae8854
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51778148"
---
# <a name="how-to-debug-injected-code"></a>Comment : déboguer du code injecté
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

REMARQUE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, choisissez Importation et exportation de paramètres dans le menu Outils. Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 L'utilisation d'attributs peut simplifier considérablement la programmation en C++. Pour plus d’informations, consultez [Concepts](http://msdn.microsoft.com/library/563e7e7c-65e1-44f4-b0b2-da04a6c1bc9e). Certains attributs sont interprétés directement par le compilateur. D'autres injectent du code dans la source du programme, code qui est ensuite traité par le compilateur. Ce code injecté simplifie la programmation en réduisant la quantité de code à écrire. Parfois, cependant, un bogue peut provoquer un échec de l'application pendant l'exécution du code injecté. Dans ce cas, vous voudrez probablement examiner le code injecté. Visual Studio vous permet de visualiser le code injecté de deux façons :  
  
- Vous pouvez afficher le code injecté dans la **désassemblage** fenêtre.  
  
- À l’aide de [/Fx](http://msdn.microsoft.com/library/14f0e301-3bab-45a3-bbdf-e7ce66f20560), vous pouvez créer un fichier source fusionné contenant le code injecté et d’origine.  
  
  Le **désassemblage** fenêtre affiche les instructions en langage assembleur qui correspondent au code source et le code injecté par des attributs. En outre, le **désassemblage** fenêtre peut afficher l’annotation de code source.  
  
### <a name="to-turn-on-source-annotation"></a>Pour activer l'annotation de la source  
  
-   Avec le bouton droit le **désassemblage** fenêtre, puis choisissez **afficher le Code Source** dans le menu contextuel.  
  
     Si vous connaissez l’emplacement d’un attribut dans une fenêtre source, vous pouvez utiliser le menu contextuel pour rechercher le code injecté dans la **désassemblage** fenêtre.  
  
### <a name="to-view-injected-code"></a>Pour afficher le code injecté  
  
1.  Assurez-vous que le débogueur est en mode arrêt.  
  
2.  Dans une fenêtre de code source, placez le curseur devant l'attribut dont vous voulez afficher le code injecté.  
  
3.  Avec le bouton droit, puis sélectionnez **atteindre le code machine** dans le menu contextuel.  
  
     Si l’attribut se trouve près du point d’exécution en cours, vous pouvez sélectionner le **désassemblage** fenêtre à partir de la **déboguer** menu.  
  
### <a name="to-view-the-disassembly-code-at-the-current-execution-point"></a>Pour afficher le code machine au point d'exécution en cours  
  
1.  Assurez-vous que le débogueur est en mode arrêt.  
  
2.  À partir de la **déboguer** menu, choisissez **Windows**, puis cliquez sur **désassemblage**.  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurité du débogueur](../debugger/debugger-security.md)   
 [Débogage du code natif](../debugger/debugging-native-code.md)



