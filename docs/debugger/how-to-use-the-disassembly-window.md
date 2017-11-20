---
title: "Afficher le Code machine dans le débogueur dans Visual Studio | Documents Microsoft"
ms.custom: H1Hack27Feb2017
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.disassembly
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- assembly language, debugging inline assembly code
- breakpoints, Disassembly window
- Disassembly window
- machine code
ms.assetid: eaf84dd0-c82d-481b-af51-690b74e7794c
caps.latest.revision: "29"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2c72de947262cd87e4920d87c2d4d54664e02cc0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="view-disassembly-code-in-the-visual-studio-debugger"></a>Afficher le Code machine dans le débogueur Visual Studio
Cette fonctionnalité est disponible uniquement si le débogage au niveau des adresses est activé le **Options** boîte de dialogue, **débogage** nœud. Elle n'est pas disponible pour le débogage de script ni le débogage SQL.  
  
 Le **code machine** fenêtre affiche le code assembleur correspondant aux instructions créées par le compilateur. Si vous déboguez du code managé, ces instructions assembleur correspondent au code natif créé par le compilateur juste-à-temps (JIT), et non au langage intermédiaire de Microsoft (MSIL) généré par le compilateur Visual Studio.  
  
 Outre les instructions assembleur, la **code machine** fenêtre peut afficher les informations facultatives suivantes :  
  
-   L'adresse mémoire de chaque instruction. Pour les applications natives, il s'agit effectivement de l'adresse mémoire. Pour Visual Basic, C# ou le code managé, il s'agit d'un offset à partir du début de la fonction.  
  
-   Le code source dont est tiré le code assembleur.  
  
-   Octets du code (représentation sous forme d'octets des instructions machine réelles ou MSIL).  
  
-   Les noms des symboles pour les adresses mémoire.  
  
-   Les numéros de ligne correspondant au code source.  
  
 Les instructions en langage assembleur sont constituées de mnémoniques, qui sont des abréviations des noms d'instructions, et de symboles représentant des variables, des registres et des constantes. Chaque instruction en langage machine est représentée par un mnémonique en langage assembleur, généralement suivi d'une ou plusieurs variables, registres ou constantes.  
  
 Si vous ne savez pas lire le langage assembleur et souhaitez pourtant profiter pleinement de la fenêtre Code Machine, consultez un ouvrage sur la programmation en langage assembleur. La programmation en langage assembleur va bien au-delà de l'objet de cette brève introduction sur la fenêtre Code Machine.  
  
 Dans la mesure où le code assembleur dépend beaucoup des registres du processeur ou, dans le cas du code managé, des registres du Common Language Runtime. Il est souvent plus judicieux d'utiliser la fenêtre Code Machine en même temps que la fenêtre Registres car cela vous permet d'examiner le contenu des registres.  
  
 Vous n'aurez probablement jamais le désir ni le besoin de consulter les instructions du code machine dans leur format numérique brut, plutôt qu'en langage assembleur. Néanmoins, si vous le souhaitez, vous pouvez les consulter dans la fenêtre Mémoire ou en sélectionnant Octets du code dans le menu contextuel de la fenêtre Code Machine.  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
### <a name="to-display-the-disassembly-window"></a>Pour afficher la fenêtre Code Machine  
  
-   Pendant le débogage, sélectionnez **Déboguer > Windows** puis cliquez sur **code machine**.
  
### <a name="to-turn-optional-information-on-or-off"></a>Pour activer ou désactiver les informations facultatives  
  
-   Avec le bouton droit le **code machine** fenêtre, puis activez ou désactivez les options souhaitées dans le menu contextuel.  
  
     Dans la marge de gauche, une flèche jaune marque l'emplacement du point d'exécution en cours. Pour le code natif, il correspond au compteur programme de la CPU. Cet emplacement montre l'instruction suivante qui sera exécutée dans votre programme.  
  
     Pour plus d’informations, consultez [vers le haut ou vers le bas dans la mémoire](../debugger/how-to-page-up-or-down-in-memory.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Affichage des données dans le débogueur](../debugger/viewing-data-in-the-debugger.md)   
 [Guide pratique pour utiliser la fenêtre Registres](../debugger/how-to-use-the-registers-window.md)