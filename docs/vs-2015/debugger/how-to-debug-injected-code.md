---
title: 'Procédure : Déboguer du Code injecté | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: b7b411574dcf65bdd1ec64c1fc51bd1813f09abb
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63432336"
---
# <a name="how-to-debug-injected-code"></a>Procédure : Déboguer du code injecté
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

REMARQUE]
> Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, choisissez Importation et exportation de paramètres dans le menu Outils. Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 L'utilisation d'attributs peut simplifier considérablement la programmation en C++. Pour plus d’informations, consultez [Concepts](http://msdn.microsoft.com/library/563e7e7c-65e1-44f4-b0b2-da04a6c1bc9e). Certains attributs sont interprétés directement par le compilateur. D'autres injectent du code dans la source du programme, code qui est ensuite traité par le compilateur. Ce code injecté simplifie la programmation en réduisant la quantité de code à écrire. Parfois, cependant, un bogue peut provoquer un échec de l'application pendant l'exécution du code injecté. Dans ce cas, vous voudrez probablement examiner le code injecté. Visual Studio vous permet de visualiser le code injecté de deux façons :  
  
- Vous pouvez l’afficher dans la fenêtre **Code Machine**.  
  
- Avec [/Fx](http://msdn.microsoft.com/library/14f0e301-3bab-45a3-bbdf-e7ce66f20560), vous pouvez créer un fichier source fusionné contenant le code d’origine et le code injecté.  
  
  La fenêtre **Code Machine** affiche les instructions en langage assembleur qui correspondent au code source et au code injecté par des attributs. En outre, **cette** fenêtre peut afficher l’annotation du code source.  
  
### <a name="to-turn-on-source-annotation"></a>Pour activer l'annotation de la source  
  
- Cliquez avec le bouton droit sur la fenêtre **Code Machine** puis, dans le menu contextuel, cliquez sur **Afficher le code source**.  
  
     Si vous connaissez l’emplacement d’un attribut dans une fenêtre source, vous pouvez utiliser le menu contextuel pour rechercher le code injecté dans la fenêtre **Code Machine**.  
  
### <a name="to-view-injected-code"></a>Pour afficher le code injecté  
  
1. Assurez-vous que le débogueur est en mode arrêt.  
  
2. Dans une fenêtre de code source, placez le curseur devant l'attribut dont vous voulez afficher le code injecté.  
  
3. Cliquez avec le bouton droit puis, dans le menu contextuel, cliquez sur **Atteindre le code Machine**.  
  
     Si l’emplacement de l’attribut est situé à proximité du point d’exécution en cours, vous pouvez sélectionner la fenêtre **Code Machine** dans le menu **Déboguer**.  
  
### <a name="to-view-the-disassembly-code-at-the-current-execution-point"></a>Pour afficher le code machine au point d'exécution en cours  
  
1. Assurez-vous que le débogueur est en mode arrêt.  
  
2. Dans le menu **Déboguer**, choisissez **Fenêtres**, puis cliquez sur **Code Machine**.  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurité du débogueur](../debugger/debugger-security.md)   
 [Débogage du code natif](../debugger/debugging-native-code.md)
