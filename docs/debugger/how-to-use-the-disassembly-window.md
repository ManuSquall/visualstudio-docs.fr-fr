---
title: Afficher le Code machine dans le débogueur dans Visual Studio | Microsoft Docs
ms.custom: H1Hack27Feb2017
ms.date: 10/30/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.disassembly
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9733569c3fa53d2c5a5905b5b893d16b4eeaf10b
ms.sourcegitcommit: a7de99f36e9ead7ea9e9bac23c88d05ddfc38b00
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52257041"
---
# <a name="view-disassembly-code-in-the-visual-studio-debugger-c-c-visual-basic-f"></a>Afficher le code machine dans le débogueur Visual Studio (C#, C++, Visual Basic, F#)

Le **désassemblage** fenêtre montre le code assembleur correspondant aux instructions créées par le compilateur. Si vous déboguez du code managé, ces instructions assembleur correspondent au code natif créé par le compilateur juste-à-temps (JIT), pas le Microsoft intermediate langage MSIL () créé par le compilateur de Visual Studio.  
  
> [!NOTE]
> Pour tirer pleinement parti de la **désassemblage** fenêtre, comprendre ou Découvrez les principes fondamentaux de [programmation en langage assembleur](https://wikipedia.org/wiki/Assembly_language).
  
Cette fonctionnalité est disponible uniquement si le débogage au niveau des adresses est activé. Il n’est pas disponible pour le script ou le débogage SQL. 

Outre les instructions assembleur, la **désassemblage** fenêtre peut afficher les informations facultatives suivantes :  
  
- L'adresse mémoire de chaque instruction. Pour les applications natives, il est l’adresse réelle de la mémoire. Pour Visual Basic ou C#, il est un décalage à partir du début de la fonction.  
  
- Le code source dont est tiré le code assembleur.  
  
- Code les octets, autrement dit, les représentations d’octets de la machine réelles ou des instructions MSIL.  
  
- Les noms des symboles pour les adresses mémoire.  
  
- Les numéros de ligne correspondant au code source.  
  
Instructions en langage assembleur sont constituées de *mnémoniques*, qui sont des abréviations des noms d’instructions, et *symboles* des variables, des registres et des constantes. Chaque instruction en langage machine est représentée par un mnémonique en langage assembleur éventuellement suivie d’un ou plusieurs symboles.  
  
Code assembleur dépend des registres du processeur ou, pour le code managé, le common language runtime enregistre. Vous pouvez utiliser la **désassemblage** fenêtre avec le **inscrit** fenêtre, ce qui vous permet d’examiner le contenu du Registre.  
  
Pour afficher les instructions du code machine dans leur format numérique brut, plutôt que comme langage d’assembly, utilisez le **mémoire** fenêtre ou sélectionnez **octets de Code** dans le menu contextuel dans le **code machine**  fenêtre.  
  
## <a name="use-the-disassembly-window"></a>La fenêtre code machine

Pour activer la **désassemblage** fenêtre, sous **outils** > **Options** (ou **outils**  >  **Options**) > **débogage**, sélectionnez **activer le débogage au niveau des adresses**.

Pour ouvrir le **désassemblage** fenêtre pendant le débogage, sélectionnez **Windows** > **désassemblage** ou appuyez sur **Alt** + **8**.

> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
Pour activer ou désactiver les informations facultatives, cliquez sur le **désassemblage** fenêtre, puis activez ou désactivez les options souhaitées dans le menu contextuel.  

Une flèche jaune dans la marge gauche marque le point d’exécution actuel. Pour le code natif, le point d’exécution correspond au compteur de programme de l’UC. Cet emplacement montre l'instruction suivante qui sera exécutée dans votre programme.  

## <a name="see-also"></a>Voir aussi  

* [Pagination vers le haut ou vers le bas dans la mémoire](../debugger/how-to-page-up-or-down-in-memory.md)
* [Affichage des données dans le débogueur](../debugger/viewing-data-in-the-debugger.md)
* [Comment : utiliser la fenêtre Registres](../debugger/how-to-use-the-registers-window.md)
