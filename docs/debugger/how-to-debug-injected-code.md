---
title: 'Comment : déboguer du Code injecté | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.injected
dev_langs:
- CSharp
- VB
- FSharp
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 44f52a1353d0e2575ea8e207d3e96187228acffd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-debug-injected-code"></a>Comment : déboguer du code injecté
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, choisissez Importation et exportation de paramètres dans le menu Outils. Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
 L'utilisation d'attributs peut simplifier considérablement la programmation en C++. Pour plus d’informations, consultez [Concepts](/cpp/windows/attributed-programming-concepts). Certains attributs sont interprétés directement par le compilateur. D'autres injectent du code dans la source du programme, code qui est ensuite traité par le compilateur. Ce code injecté simplifie la programmation en réduisant la quantité de code à écrire. Parfois, cependant, un bogue peut provoquer un échec de l'application pendant l'exécution du code injecté. Dans ce cas, vous voudrez probablement examiner le code injecté. Visual Studio vous permet de visualiser le code injecté de deux façons :  
  
-   Vous pouvez afficher le code injecté dans le **code machine** fenêtre.  
  
-   À l’aide de [/Fx](/cpp/build/reference/fx-merge-injected-code), vous pouvez créer un fichier source fusionné contenant le code injecté et d’origine.  
  
 Le **code machine** fenêtre affiche les instructions en langage assembleur qui correspondent au code source et le code injecté par des attributs. En outre, le **code machine** fenêtre peut afficher l’annotation de code source.  
  
### <a name="to-turn-on-source-annotation"></a>Pour activer l'annotation de la source  
  
-   Avec le bouton droit le **code machine** fenêtre, puis choisissez **afficher le Code Source** dans le menu contextuel.  
  
     Si vous connaissez l’emplacement d’un attribut dans une fenêtre source, vous pouvez utiliser le menu contextuel pour rechercher le code injecté dans le **code machine** fenêtre.  
  
### <a name="to-view-injected-code"></a>Pour afficher le code injecté  
  
1.  Assurez-vous que le débogueur est en mode arrêt.  
  
2.  Dans une fenêtre de code source, placez le curseur devant l'attribut dont vous voulez afficher le code injecté.  
  
3.  Avec le bouton droit, puis sélectionnez **atteindre le code machine** dans le menu contextuel.  
  
     Si l’attribut d’emplacement est presque le point d’exécution en cours, vous pouvez sélectionner le **code machine** fenêtre à partir de la **déboguer** menu.  
  
### <a name="to-view-the-disassembly-code-at-the-current-execution-point"></a>Pour afficher le code machine au point d'exécution en cours  
  
1.  Assurez-vous que le débogueur est en mode arrêt.  
  
2.  À partir de la **déboguer** menu, choisissez **Windows**, puis cliquez sur **code machine**.  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurité du débogueur](../debugger/debugger-security.md)   
 [Débogage du code natif](../debugger/debugging-native-code.md)