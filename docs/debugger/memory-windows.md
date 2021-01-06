---
title: Afficher la mémoire pour les variables dans le débogueur | Microsoft Docs
description: Apprenez à utiliser la mémoire Windows au fur et à mesure du débogage pour voir l’espace mémoire utilisé par votre application. D’autres fenêtres affichent des variables et où elles résident en mémoire.
ms.custom: SEO-VS-2020
ms.date: 10/04/2018
ms.topic: how-to
f1_keywords:
- vs.debug.memory
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- Memory window
- strings [Visual Studio], viewing
- debugger [Visual Studio], Memory window
- memory [Visual Studio], debugging
- debugging [Visual Studio], Memory window
- buffers, viewing
ms.assetid: 7f7a0439-10e4-4966-bb2d-51f04cda4fe2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0c39024e32c899310b88c1b0583d5b292b063937
ms.sourcegitcommit: 620d30c60da8f9805fce524fe4951cf40f28297d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/05/2021
ms.locfileid: "97903106"
---
# <a name="use-the-memory-windows-in-the-visual-studio-debugger-c-c-visual-basic-f"></a>Utiliser les fenêtres mémoire dans le débogueur Visual Studio (C#, C++, Visual Basic, F #)

Pendant le débogage, la fenêtre **mémoire** affiche l’espace mémoire utilisé par votre application.

Les fenêtres du débogueur, telles que **Espion**, **automatique**, **variables locales** et la boîte de dialogue **Espion express** , affichent des variables qui sont stockées à des emplacements spécifiques en mémoire. La fenêtre **mémoire** vous montre l’image globale. La vue mémoire est pratique pour examiner de grands éléments de données (mémoires tampons ou chaînes volumineuses, par exemple) qui ne s’affichent pas correctement dans les autres fenêtres.

La fenêtre **mémoire** n’est pas limitée à l’affichage des données. Il affiche tout ce qui se trouve dans l’espace mémoire, y compris les données, le code et les bits aléatoires du garbage dans la mémoire non assignée.

La fenêtre **mémoire** n’est pas disponible pour le débogage de script ou SQL. Ces langages ne reconnaissent pas le concept de mémoire.

## <a name="open-a-memory-window"></a>Ouvrir une fenêtre mémoire

Comme les autres fenêtres du débogueur, les fenêtres de **mémoire** sont disponibles uniquement pendant une session de débogage.

>[!IMPORTANT]
>Pour activer les fenêtres de **mémoire** , **activez le débogage au niveau** de l’adresse dans **Outils**  >  **options** (ou options de **débogage**  >  ) > **débogage**  >  **général**.

**Pour ouvrir une fenêtre Mémoire**

1. Assurez-vous que l’option **activer le débogage au niveau** de l’adresse est sélectionnée dans **Outils**  >  **options** (ou options de **débogage**  >  ) > **débogage**  >  **général**.

1. Démarrez le débogage en sélectionnant la flèche verte, en appuyant sur **F5** ou **en sélectionnant déboguer**  >  **Démarrer le débogage**.

2. Sous **Déboguer** la  >    >  **mémoire** Windows, sélectionnez **mémoire 1**, **mémoire 2**, **mémoire 3** ou **mémoire 4**. (Certaines éditions de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] offrent une seule fenêtre de **mémoire** .)

## <a name="move-around-in-the-memory-window"></a>Se déplacer dans la fenêtre mémoire

L’espace d’adressage d’un ordinateur est important et vous pouvez facilement perdre votre place en faisant défiler la fenêtre **mémoire** .

Les adresses mémoire supérieures s'affichent au bas de la fenêtre. Pour afficher une adresse plus élevée, faites défiler vers le haut. Pour afficher une adresse inférieure, faites défiler vers le haut.

Vous pouvez accéder instantanément à une adresse spécifiée dans la fenêtre **mémoire** à l’aide du glisser-déplacer, ou en entrant l’adresse dans le champ **adresse** . Le champ **adresse** accepte les adresses alphanumériques et les expressions qui correspondent à des adresses, telles que `e.User.NonroamableId` .

Pour forcer la réévaluation immédiate d’une expression dans le champ d' **adresse** , sélectionnez l’icône de réévaluation de la flèche arrondie **automatiquement** .

Par défaut, la fenêtre **mémoire** traite les expressions d' **adresse** en tant qu’expressions dynamiques, qui sont réévaluées au fur et à mesure de l’exécution de l’application. Les expressions dynamiques peuvent être utiles, par exemple, pour afficher la mémoire affectée par une variable pointeur.

**Pour utiliser le glisser-déplacer pour déplacer vers un emplacement de mémoire :**

1. Dans une fenêtre du débogueur, sélectionnez une adresse mémoire ou une variable pointeur qui contient une adresse mémoire.

2. Glissez-déposez l’adresse ou le pointeur dans la fenêtre **mémoire** . Cette adresse apparaît alors dans le champ **adresse** , et la fenêtre **mémoire** s’ajuste pour afficher cette adresse en haut.

**Pour passer à un emplacement de mémoire, entrez-le dans le champ adresse :**

- Tapez ou collez l’adresse ou l’expression dans le champ **adresse** et appuyez sur **entrée**, ou choisissez-la dans la liste déroulante du champ **adresse** . La fenêtre **mémoire** s’ajuste pour afficher cette adresse en haut.

## <a name="customize-the-memory-window"></a>Personnaliser la fenêtre mémoire

Par défaut, le contenu de la mémoire apparaît sous la forme d’entiers de 1 octet au format hexadécimal, et la largeur de la fenêtre détermine le nombre de colonnes affichées. Vous pouvez personnaliser la façon dont la fenêtre **Mémoire** affiche le contenu de la mémoire.

**Pour modifier le format du contenu de la mémoire :**

- Cliquez avec le bouton droit dans la fenêtre **mémoire** , puis choisissez les formats souhaités dans le menu contextuel.

**Pour modifier le nombre de colonnes dans la fenêtre mémoire :**

- Sélectionnez la flèche déroulante en regard du champ **colonnes** , sélectionnez le nombre de colonnes à afficher ou sélectionnez **auto** pour un ajustement automatique en fonction de la largeur de la fenêtre.

Si vous ne souhaitez pas que le contenu de la fenêtre de **mémoire** change au fur et à mesure de l’exécution de votre application, vous pouvez désactiver l’évaluation de l’expression dynamique.

**Pour activer/désactiver l’évaluation dynamique :**

- Cliquez avec le bouton droit dans la fenêtre **mémoire** , puis sélectionnez **réévaluer automatiquement** dans le menu contextuel.

  >[!NOTE]
  >L’évaluation de l’expression dynamique est une bascule et est activée par défaut. par conséquent, la sélection de **réévaluer automatiquement** la désactive. Si vous sélectionnez **réévaluer automatiquement** , la réactiver.

Vous pouvez masquer ou afficher la barre d’outils en haut de la fenêtre **Mémoire**. Vous n’avez pas accès au champ **adresse** ou à d’autres outils lorsque la barre d’outils est masquée.

**Pour activer/désactiver l’affichage de la barre d’outils :**

- Cliquez avec le bouton droit dans la fenêtre **mémoire** , puis sélectionnez **afficher la barre d’outils** dans le menu contextuel. La barre d'outils disparaît ou apparaît, selon son état précédent.

## <a name="follow-a-pointer-through-memory"></a>Suivre un pointeur dans la mémoire

Dans les applications en code natif, vous pouvez utiliser des noms de registres comme expressions dynamiques. Par exemple, vous pouvez utiliser le pointeur de pile pour suivre la pile.

**Pour suivre un pointeur dans la mémoire :**

1. Dans le champ **adresse** de la fenêtre **mémoire** , entrez une expression de pointeur qui se trouve dans l’étendue actuelle. Vous devrez la déréférencer en fonction du langage.

2. Appuyez sur **Entrée**.

   Lorsque vous utilisez une commande de débogage telle que l' **étape**, l’adresse mémoire affichée dans le champ **adresse** et en haut de la fenêtre **mémoire** change automatiquement à mesure que le pointeur change.

## <a name="see-also"></a>Voir aussi
- [Afficher les données dans le débogueur](../debugger/viewing-data-in-the-debugger.md)