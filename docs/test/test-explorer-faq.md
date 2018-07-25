---
title: FAQ concernant l’Explorateur de tests Visual Studio
ms.date: 1/15/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- Test Explorer
- Test window
- Visual Studio Test Explorer
- summary line
- unit tests
- Test Explorer FAQ
ms.author: kehavens
ms.workload:
- multiple
author: kendrahavens
manager: douge
ms.openlocfilehash: d774a0daa9cc503bde91009b9c78288a6f043721
ms.sourcegitcommit: 498e39e89a89ad7bf9dcb0617424fff999b1c3b2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/21/2018
ms.locfileid: "36303281"
---
# <a name="visual-studio-test-explorer-faq"></a>FAQ concernant l’Explorateur de tests Visual Studio

## <a name="test-discovery"></a>Découverte de tests

### <a name="1-the-test-explorer-is-not-discovering-my-tests-that-are-dynamically-defined-for-example-theories-custom-adapters-custom-traits-ifdefs-etc-how-can-i-discover-these-tests"></a>1. L’Explorateur de tests ne découvre pas mes tests qui sont définis dynamiquement (théories, adaptateurs personnalisés, caractéristiques personnalisées, #ifdefs, etc.). Comment puis-je découvrir ces tests ?

  Générez votre projet et vérifiez que la découverte basée sur les assemblys est activée sous **Outils > Options > Test**.

  La [découverte de tests en temps réel](https://go.microsoft.com/fwlink/?linkid=862824) correspond à la découverte de tests basée sur les sources. Elle ne peut pas découvrir les tests qui utilisent des théories, des adaptateurs personnalisés, des caractéristiques personnalisés, des instructions `#ifdef`, etc. car ils sont définis au moment de l’exécution. Une build est nécessaire pour découvrir correctement ces tests. Dans les préversions 15.6, la découverte basée sur les assemblys (le découvreur traditionnel) s’exécute uniquement après les builds. En d’autres termes, la découverte de tests en temps réel découvre autant de tests que possible au fur et à mesure que vous effectuez des modifications, et la découverte basée sur les assemblys permet de faire apparaître les tests définis dynamiquement après une build. La découverte de tests en temps réel améliore la réactivité, tout en vous permettant d’obtenir des résultats complets et précis après une build.

### <a name="2-what-does-the--plus-symbol-that-appears-in-the-top-line-of-test-explorer-mean"></a>2. Que signifie le signe plus (+) qui apparaît sur la ligne supérieure l’Explorateur de tests ?

  Le signe « + » (plus) indique que d’autres tests peuvent être découverts après une build tant que la découverte basée sur les assemblys est activée. Il apparaît si des tests définis dynamiquement sont détectés dans votre projet.

  ![Signe plus sur la ligne de résumé](media/testex-plussymbol.png)

### <a name="3-assembly-based-discovery-is-no-longer-working-for-my-project-how-do-i-turn-it-back-on"></a>3. La découverte basée sur les assemblys ne fonctionne plus avec mon projet. Comment puis-je la réactiver ?

  Accédez à **Outils > Options > Test** et cochez la case **Découvrez également les tests des assemblys générés après les builds**.

  ![Option basée sur les assemblys](media/testex-toolsoptions.png)

### <a name="4-tests-now-appear-in-test-explorer-while-i-type-without-having-to-build-my-project-what-changed"></a>4. Les tests s’affichent désormais automatiquement dans l’Explorateur de tests quand j’écris, sans que j’aie à générer mon projet. Que s’est-il passé ?

  Cette fonctionnalité s’appelle la [découverte de tests en temps réel](https://go.microsoft.com/fwlink/?linkid=862824). Elle utilise un analyseur Roslyn pour découvrir les tests et renseigner l’Explorateur de tests en temps réel, sans que l’utilisateur ait à générer son projet. Pour plus d’informations sur le comportement de la découverte de tests pour les tests définis dynamiquement tels que les théories ou les caractéristiques personnalisées, consultez le FAQ nº 1.

### <a name="5-what-languages-and-test-frameworks-can-use-real-time-test-discovery"></a>5. Quels langages et quelles infrastructures de test peuvent utiliser la découverte de tests en temps réel ?

  La [découverte de tests en temps réel](https://go.microsoft.com/fwlink/?linkid=862824) fonctionne uniquement avec les langages managés (C# et Visual Basic), car elle utilise le compilateur Roslyn. À l’heure actuelle, la découverte de test en temps réel fonctionne uniquement avec les infrastructures xUnit, NUnit et MSTest.

### <a name="6-how-can-i-turn-on-logs-for-the-test-explorer"></a>6. Comment activer les journaux pour l’Explorateur de tests ?

  Accédez à **Outils > Options > Test** et recherchez la section Journalisation.

### <a name="7-why-are-my-tests-in-uwp-projects-not-discovered-until-i-deploy-my-app"></a>7. Pourquoi dois-je d’abord déployer mon application pour que mes tests soient découverts dans des projets UWP ?

  Les tests UWP ciblent un runtime différent quand l’application est déployée. Pour découvrir de manière précise les tests pour les projets UWP, vous devez donc non seulement générer votre projet, mais aussi le déployer.

### <a name="8-how-does-sorting-test-results-work-in-the-hierarchy-view"></a>8. Comment fonctionne le tri des résultats de tests dans l’affichage des hiérarchies ?

  L’affichage des hiérarchies trie les tests par ordre alphabétique et non par résultat. Les autres paramètres de regroupement trient normalement les résultats de tests par résultat, puis par ordre alphabétique. Consultez les différentes options de regroupement dans l’image suivante à des fins de comparaison. Vous pouvez fournir des commentaires sur la conception [dans ce problème GitHub](https://github.com/Microsoft/vstest/issues/1425).

  ![SortingExamples](media/testex-sortingex.png)

### <a name="9-in-the-hierarchy-view-there-are-passed-failed-skipped-and-not-run-icons-next-to-the-project-namespace-and-class-groupings-what-do-these-icons-mean"></a>9. La vue de la hiérarchie inclut des icônes passed (réussi), failed (échec), skipped (ignoré) et not run (non exécuté) en regard des regroupements Projet, Espace de noms et Classe. Que signifient ces icônes ?

  Les icônes en regard des regroupements Projet, Espace de noms et Classe reflètent l’état des tests dans le regroupement. Consultez le tableau suivant.

  ![Icônes de la hiérarchie de l’Explorateur de tests](media/testex-hierarchyicons.png)

### <a name="10-there-is-no-longer-a-file-path-filter-in-the-test-explorer-search-box"></a>10. Il n’y a plus de filtre « Chemin d’accès du fichier » dans la zone de recherche de l’explorateur de tests.

Le filtre de chemin d’accès du fichier dans la zone de recherche de l’**explorateur de tests** a été supprimé dans Visual Studio 2017, version 15.7, préversion 3. Cette fonctionnalité était très peu utilisée, et l’explorateur de tests peut récupérer des méthodes de test plus rapidement en excluant cette fonctionnalité. Si cette modification interrompt votre flux de développement, faites-le nous savoir en envoyant vos commentaires à la [Communauté des développeurs](https://developercommunity.visualstudio.com/).

## <a name="features"></a>Fonctionnalités

### <a name="how-can-i-turn-on-feature-flags-to-try-out-new-testing-features"></a>Comment puis-je activer les indicateurs de fonctionnalités pour tester les nouvelles fonctionnalités de test ?

Les indicateurs de fonctionnalités servent à fournir des parties expérimentales ou inachevées du produit à des utilisateurs passionnés qui souhaitent envoyer des commentaires avant le lancement officiel des fonctionnalités. Ils peuvent affecter votre expérience IDE. Utilisez-les uniquement dans des environnements de développement sécurisés, tels que des machines virtuelles. Les indicateurs de fonctionnalités sont toujours des paramètres que vous utilisez à vos risques et périls. Vous pouvez activer les fonctionnalités expérimentales à l’aide de l’[extension Feature Flags](https://marketplace.visualstudio.com/items?itemName=PaulHarrington.FeatureFlagsExtension) ou de l’invite de commandes développeur.

![Extension Feature Flag](media/testex-featureflag.png)

Pour activer un indicateur de fonctionnalité à l’aide de l’invite de commandes développeur Visual Studio, utilisez la commande suivante. Modifiez le chemin d’accès à l’emplacement d’installation de Visual Studio sur votre ordinateur et modifiez la clé de Registre en fonction de l’indicateur de fonctionnalité souhaité.

```shell
vsregedit set “C:\Program Files (x86)\Microsoft Visual Studio\Preview\Enterprise" HKLM FeatureFlags\TestingTools\UnitTesting\HierarchyView Value dword 1
```

> [!NOTE]
> Vous pouvez désactiver l’indicateur à l’aide de la même commande, en utilisant la valeur 0 au lieu de 1 après dword.

## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=fullName>
- [Création et exécution de tests unitaires pour le code existant](http://msdn.microsoft.com/e8370b93-085b-41c9-8dec-655bd886f173)
- [Tests unitaires sur votre code](unit-test-your-code.md)
- [FAQ Live Unit Testing](live-unit-testing-faq.md)
