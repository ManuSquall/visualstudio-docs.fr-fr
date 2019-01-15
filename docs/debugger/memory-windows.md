---
title: Afficher la mémoire pour les variables dans le débogueur | Microsoft Docs
ms.custom: H1Hack27Feb2017
ms.date: 10/04/2018
ms.topic: conceptual
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3e56ad2c36e4b7a22cfb74e020c31e93f4846872
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53837223"
---
# <a name="use-the-memory-windows-in-the-visual-studio-debugger-c-c-visual-basic-f"></a>Utiliser les fenêtres de mémoire dans le débogueur Visual Studio (C#, C++, Visual Basic, F#)

Pendant le débogage, le **mémoire** fenêtre affiche l’espace de mémoire à l’aide de votre application. 

Débogueur windows comme **espion**, **automatique**, **variables locales**et le **Espion express** boîte de dialogue vous afficher les variables, lesquelles sont stockées à spécifiques emplacements de mémoire. Le **mémoire** fenêtre vous montre la vue d’ensemble. La vue de la mémoire est pratique pour l’examen de grands fragments de données (mémoires tampons ou longues chaînes, par exemple) qui ne s’affichent pas correctement dans les autres fenêtres. 

Le **mémoire** fenêtre n’est pas tenu d’afficher des données. Il affiche tous les éléments dans l’espace de mémoire, y compris des données, le code et les bits aléatoires de garbage dans la mémoire non assignée.  

Le **mémoire** fenêtre n’est pas disponible pour le script ou le débogage SQL. Ces langues ne reconnaissent pas le concept de mémoire.  
  
## <a name="open-a-memory-window"></a>Ouvrez une fenêtre mémoire  
  
Comme les autres fenêtres du débogueur, le **mémoire** windows sont disponibles uniquement pendant une session de débogage. 

>[!IMPORTANT]
>Pour activer la **mémoire** windows, **activer le débogage au niveau des adresses** doit être sélectionnée dans **outils** > **Options** (ou **Déboguer** > **Options**) > **débogage** > **général**. 

**Pour ouvrir une fenêtre Mémoire**
  
1. Assurez-vous que **activer le débogage au niveau des adresses** est sélectionné dans **outils** > **Options** (ou **déboguer**  >  **Options**) > **débogage** > **général**. 
   
1. Démarrer le débogage en sélectionnant la flèche verte, en appuyant sur **F5**, ou en sélectionnant **déboguer** > **démarrer le débogage**.  
   
2. Sous **déboguer** > **Windows** > **mémoire**, sélectionnez **mémoire 1**, **mémoire 2**, **Mémoire 3**, ou **mémoire 4**. (Certaines éditions de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] n'offrent qu’un seul **mémoire** fenêtre.)  

## <a name="move-around-in-the-memory-window"></a>Déplacer dans la fenêtre mémoire  

L’espace d’adressage d’un ordinateur est volumineux, et vous pouvez facilement perdre votre place en faisant défiler le **mémoire** fenêtre. 

Les adresses mémoire supérieures s'affichent au bas de la fenêtre. Pour afficher une adresse supérieure, faites défiler vers le bas. Pour afficher une adresse inférieure, faites défiler vers le haut.  

Vous pouvez accéder instantanément à une adresse spécifiée dans le **mémoire** fenêtre à l’aide de glisser-déplacer, ou en entrant l’adresse dans le **adresse** champ. Le **adresse** champ accepte les adresses d’alphanumériques et des expressions qui correspondent à des adresses, tel que `e.User.NonroamableId`. 

Pour forcer la réévaluation immédiate d’une expression dans le **adresse** , sélectionnez la flèche arrondie **réévaluer automatiquement** icône. 

Par défaut, le **mémoire** traite de la fenêtre **adresse** expressions comme expressions dynamiques, qui sont réévaluées en tant que l’exécution de l’application. Expressions dynamiques peuvent être utiles, par exemple, pour afficher la mémoire survolée par une variable de pointeur.  

**Pour utiliser la fonction glisser-déplacer pour déplacer vers un emplacement de mémoire :**  
   
1. Dans la fenêtre de débogueur, sélectionnez une adresse mémoire ou une variable pointeur qui contient une adresse mémoire.  
   
2. Glissez -déplacez l’adresse ou le pointeur dans la **mémoire** fenêtre. Cette adresse apparaît alors dans le **adresse** champ et le **mémoire** fenêtre s’ajuste pour afficher cette adresse en haut. 
  
**Pour déplacer vers un emplacement de mémoire en le saisissant dans le champ adresse :**
  
- Tapez ou collez l’adresse ou une expression dans le **adresse** champ et appuyez sur **entrée**, ou choisissez-le dans la liste déroulante dans le **adresse** champ. Le **mémoire** fenêtre s’ajuste pour afficher cette adresse en haut.
  
## <a name="customize-the-memory-window"></a>Personnaliser la fenêtre mémoire 

Par défaut, contenu de la mémoire apparaître sous forme d’entiers de 1 octet au format hexadécimal, et la largeur de fenêtre détermine le nombre de colonnes affichées. Vous pouvez personnaliser la façon dont la fenêtre **Mémoire** affiche le contenu de la mémoire.  
  
**Pour changer le format du contenu mémoire :**  
  
-  Avec le bouton droit dans le **mémoire** fenêtre, puis choisissez les formats que vous souhaitez dans le menu contextuel.  
  
**Pour modifier le nombre de colonnes affichées dans la fenêtre Mémoire :**
  
- Sélectionnez la flèche déroulante en regard du **colonnes** champ, puis sélectionnez le nombre de colonnes à afficher, ou sélectionnez **automatique** pour l’ajustement automatique en fonction de la largeur de la fenêtre.  
  
Si vous ne souhaitez pas que le contenu de la **mémoire** fenêtre Modifier en tant que votre application s’exécute, vous pouvez désactiver l’évaluation dynamique des expressions. 

**Pour activer ou désactiver l’évaluation dynamique :**  
  
- Avec le bouton droit dans le **mémoire** , puis sélectionnez **réévaluer automatiquement** dans le menu contextuel. 

  >[!NOTE]
  >Live expression d’évaluation est un bouton bascule et est activé par défaut, par conséquent, en sélectionnant **réévaluer automatiquement** est désactivée. En sélectionnant **réévaluer automatiquement** à nouveau rallume automatiquement. 
  
Vous pouvez masquer ou afficher la barre d’outils en haut de la fenêtre **Mémoire**. Vous n’aurez pas d’accès à la **adresse** champ ou autres outils lorsque la barre d’outils est masquée.  
  
**Pour activer/désactiver l’affichage de la barre d’outils :**  
  
- Avec le bouton droit dans le **mémoire** , puis sélectionnez **afficher la barre d’outils** dans le menu contextuel. La barre d'outils disparaît ou apparaît, selon son état précédent.  
  
## <a name="follow-a-pointer-through-memory"></a>Suivre un pointeur dans la mémoire  

Dans les applications en code natif, vous pouvez utiliser des noms de registres comme expressions dynamiques. Par exemple, vous pouvez utiliser le pointeur de pile pour suivre la pile.  
  
**Pour suivre un pointeur dans la mémoire :**
  
1. Dans le **mémoire** fenêtre **adresse** , entrez une expression de pointeur qui se trouve dans la portée actuelle. Vous devrez la déréférencer en fonction du langage.  
  
2. Appuyez sur **Entrée**.  
   
   Lorsque vous utilisez une commande de débogage telles que **étape**, l’adresse mémoire affichée dans le **adresse** champ et en haut de la **mémoire** fenêtre change automatiquement en tant que le pointeur modifications.  
  
## <a name="see-also"></a>Voir aussi  
 [Afficher les données dans le débogueur](../debugger/viewing-data-in-the-debugger.md)