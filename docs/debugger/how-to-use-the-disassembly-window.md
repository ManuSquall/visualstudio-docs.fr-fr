---
title: Afficher le code machine dans le débogueur | Microsoft Docs
description: Utilisez la fenêtre Code machine dans Visual Studio pour afficher le code assembleur correspondant aux instructions créées par le compilateur.
ms.custom: SEO-VS-2020
ms.date: 10/30/2018
ms.topic: how-to
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c8cc67b2f8136ea426eb56c25fb3c345198701f1
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112387461"
---
# <a name="view-disassembly-code-in-the-visual-studio-debugger-c-c-visual-basic-f"></a>Afficher le code machine dans le débogueur Visual Studio (C#, C++, Visual Basic, F #)

La fenêtre **Code Machine** affiche le code assembleur correspondant aux instructions créées par le compilateur. Si vous déboguez du code managé, ces instructions d’assembly correspondent au code natif créé par le compilateur juste-à-temps (JIT), et non au langage MSIL (Microsoft Intermediate Language) créé par le compilateur Visual Studio.

> [!NOTE]
> Pour tirer pleinement parti de la **fenêtre** code machine, comprenez ou apprenez les principes fondamentaux de la [programmation en langage assembleur](https://wikipedia.org/wiki/Assembly_language).

Cette fonctionnalité n’est disponible que si le débogage au niveau de l’adresse est activé. Elle n’est pas disponible pour le débogage de script ou SQL.

Outre les instructions en assembleur, la fenêtre **Code Machine** peut afficher les informations facultatives suivantes :

- L'adresse mémoire de chaque instruction. Pour les applications natives, il s’agit de l’adresse mémoire réelle. Pour Visual Basic ou C#, il s’agit d’un offset à partir du début de la fonction.

- Le code source dont est tiré le code assembleur.

- Octets de code, autrement dit, les représentations d’octets de l’ordinateur réel ou les instructions MSIL.

- Les noms des symboles pour les adresses mémoire.

- Les numéros de ligne correspondant au code source.

Les instructions en langage assembleur consistent en des *mnémoniques*, qui sont des abréviations pour les noms d’instruction et des *symboles* pour les variables, les registres et les constantes. Chaque instruction de langage machine est représentée par un mnémonique en langage assembleur, éventuellement suivi d’un ou de plusieurs symboles.

Le code assembleur s’appuie fortement sur les registres du processeur ou, pour le code managé, common language runtime registres. Vous pouvez utiliser la fenêtre **code machine** avec la fenêtre **registres** , qui vous permet d’examiner le contenu du Registre.

Pour afficher les instructions de code machine sous leur forme numérique brute, plutôt qu’en tant que langage assembleur, utilisez la fenêtre **mémoire** ou sélectionnez **octets de code** dans le menu contextuel de **la fenêtre Code machine.**

## <a name="use-the-disassembly-window"></a>Utiliser la fenêtre Code Machine

Pour activer la fenêtre **code machine** , sous **Outils**  >  **options**  >  **débogage**, sélectionnez **activer le débogage au niveau de l’adresse**.

Pour ouvrir la fenêtre **code machine** pendant le débogage, sélectionnez **Windows**  >  **code machine** ou appuyez sur **ALT** + **8**.

> [!NOTE]
> Les boîtes de dialogue et les commandes de menu affichées peuvent différer de celles décrites dans l'Aide selon les paramètres actifs ou le mode d'édition. Pour modifier vos paramètres, choisissez **Paramètres d'importation et d'exportation** dans le menu **Outils** . Pour plus d’informations, consultez [Réinitialiser les paramètres](../ide/environment-settings.md#reset-settings).

Pour activer ou désactiver des informations facultatives, cliquez avec le bouton droit dans la fenêtre **code machine** , puis définissez ou désactivez les options souhaitées dans le menu contextuel.

Une flèche jaune dans la marge de gauche marque le point d’exécution actuel. Pour le code natif, le point d’exécution correspond au compteur de programme de l’UC. Cet emplacement montre l'instruction suivante qui sera exécutée dans votre programme.

## <a name="see-also"></a>Voir aussi

* [Déplacement d’une page vers le haut ou vers le bas dans la mémoire](../debugger/how-to-page-up-or-down-in-memory.md)
* [Affichage des données dans le débogueur](../debugger/viewing-data-in-the-debugger.md)
* [Comment : utiliser la fenêtre registres](../debugger/how-to-use-the-registers-window.md)