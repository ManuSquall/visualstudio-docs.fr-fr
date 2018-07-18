---
title: Nouveautés de Live Unit Testing
ms.date: 10-11-2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio ALM
- Live Unit Testing
- Live Unit Testing What's New
author: rpetrusha
ms.author: ronpet
ms.workload:
- dotnet
ms.openlocfilehash: 8e6e0a812839dac9ad8962e12a610a82cb56a1fc
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31974778"
---
# <a name="whats-new-in-live-unit-testing"></a>Nouveautés de Live Unit Testing

Cette rubrique liste les nouvelles fonctionnalités ajoutées à Live Unit Testing dans chaque version de Visual Studio à partir de Visual Studio 2017 version 15.3. Pour une vue d’ensemble de l’utilisation de Live Unit Testing, consultez [Live Unit Testing avec Visual Studio 2017](live-unit-testing.md).

## <a name="whats-new-in-live-unit-testing-for-visual-studio-2017-version-154"></a>Nouveautés de Live Unit Testing dans Visual Studio 2017 version 15.4

À compter de Visual Studio 2017 version 15.4, Live Unit Testing présente des améliorations dans plusieurs domaines :

- **Découvrabilité améliorée** Pour les utilisateurs qui ne connaissent pas l’existence de la fonctionnalité Live Unit Testing, l’IDE Visual Studio affiche une barre jaune qui fait mention de Live Unit Testing quand l’utilisateur ouvre une solution qui inclut des tests unitaires alors que Live Unit Testing n’est pas activé. Les informations présentées dans la barre jaune permettent à l’utilisateur d’en savoir plus sur Live Unit Testing et de l’activer. La barre jaune affiche également des informations quand les prérequis de Live Unit Testing ne sont pas satisfaits. Elles incluent notamment :

   - Des adaptateurs de test sont manquants.
   - Des versions plus anciennes des adaptateurs de test sont présentes.
   - Une restauration des packages NuGet référencés par la solution est nécessaire. 

- **Intégration aux notifications du Centre des tâches**. L’IDE Visual Studio affiche maintenant une notification du traitement en arrière-plan de Live Unit Testing dans le Centre des tâches, afin que les utilisateurs puissent voir facilement ce qui se passe quand Live Unit Testing est activé. Ceci est destiné à résoudre l’important problème du démarrage de Live Unit Testing sur une grande solution. Avant, pendant quelques minutes et jusqu’à ce que les icônes de couverture apparaissent, les utilisateurs ne pouvaient pas déterminer si Live Unit Testing était réellement activé et s’il fonctionnait. Ce n’est plus le cas !

- **Prise en charge du framework MSTest version 1** : Live Unit Testing fonctionne déjà avec trois frameworks de tests unitaires répandus : xUnit, NUnit et MSTest. Avant, Live Unit Testing fonctionnait seulement quand les projets de tests unitaires utilisaient MSTest version 2. À compter de Visual Studio 2017 version 15.4, il prend désormais également en charge MSTest version 1. 

- **Fiabilité et performances** : Live Unit Testing garantit maintenant que le système peut mieux détecter quand les projets ne sont pas complètement chargés et ne se bloque donc plus dans ces circonstances. Des améliorations des performances de la génération évitent aussi la réévaluation des projets MSBuild quand le système détecte que rien n’a changé dans le fichier projet.  

- **Différentes améliorations de l’interface utilisateur** : l’option **Live Test Set – Inclure/Exclure** accessible d’un clic droit prêtait à confusion, elle a donc été renommée **Live Unit Testing Inclure/Exclure**. L’option **Réinitialiser** dans le menu **Test** de **Live Unit Testing** a été supprimée. Elle est désormais accessible en sélectionnant **Outils**, **Options**, **Live Unit Testing** et en sélectionnant **Supprimer les données persistantes**.

## <a name="whats-new-in-live-unit-testing-for-visual-studio-2017-version-153"></a>Nouveautés de Live Unit Testing pour Visual Studio 2017 version 15.3

À compter de Visual Studio 2017 version 15.3, Live Unit Testing présente des améliorations dans deux domaines principaux :

- Prise en charge de .NET Core et de .NET Standard. Vous pouvez utiliser Live Unit Testing sur des solutions .NET Core et .NET Standard écrites en C# ou en Visual Basic.
 
-  Amélioration des performances. Vous remarquerez une nette accélération des performances après la première build complète et l’exécution de tests sous Live Unit Testing, puis lors des démarrages suivants de Live Unit Testing sur la même solution. Nous conservons à présent les données générées par Live Unit Testing et les réutilisons autant que possible avec les vérifications de mise à jour. 
 
En plus de ces ajouts majeurs, Live Unit Testing comprend les améliorations suivantes : 

- Une nouvelle icône de bécher permet désormais de distinguer une méthode de test des méthodes habituelles. Une icône de bécher vide indique que le test associé n’est pas inclus dans Live Unit Testing. 

- Lorsque vous cliquez sur une méthode de test dans la fenêtre indépendante de l’interface utilisateur d’une icône de couverture Live Unit Testing, vous avez la possibilité maintenant de déboguer le test directement à partir de ce contexte, dans la fenêtre de l’interface utilisateur et sans avoir à quitter l’éditeur de code. C’est très pratique, notamment pour examiner un échec de test.  

- Plusieurs options configurables supplémentaires ont été ajoutées à Outils/Options/Live Unit Testing/Général. Vous pouvez limiter la mémoire utilisée pour Live Unit Testing. Vous pouvez également spécifier le chemin d’accès des fichiers de données Live Unit Testing persistantes de votre solution ouverte. 

- Plusieurs éléments de menu supplémentaires ont été ajoutés sous la barre de menus de Test/Live Unit Testing. **Réinitialiser et nettoyer** supprime les données persistantes et les regénère. **Option** permet d’accéder à Outils/Options/Live Unit Testing/Général.
  
- Vous pouvez à présent utiliser les attributs suivants pour spécifier dans le code source que vous souhaitez exclure les méthodes de test ciblées de Live Unit Testing :
   - Pour xUnit : `[Trait("Category", "SkipWhenLiveUnitTesting")]`
   - Pour NUnit : `[Category("SkipWhenLiveUnitTesting")]`
   - Pour MSTest : `[TestCategory("SkipWhenLiveUnitTesting")]`

## <a name="see-also"></a>Voir aussi
[Présentation de Live Unit Testing](live-unit-testing-intro.md)   
[Live Unit Testing avec Visual Studio 2017](live-unit-testing.md)

