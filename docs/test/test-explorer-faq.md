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
ms.openlocfilehash: c9321c90132b026a71733dbbadc19a82db20d981
ms.sourcegitcommit: 401be39a42ffe007593528b5bba62583ca9fcafd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2018
ms.locfileid: "50244383"
---
# <a name="visual-studio-test-explorer-faq"></a>FAQ concernant l’Explorateur de tests Visual Studio

## <a name="dynamic-test-discovery"></a>Découverte de tests dynamique
**L’Explorateur de tests ne découvre pas mes tests qui sont définis dynamiquement (théories, adaptateurs personnalisés, caractéristiques personnalisées, #ifdefs, etc.). Comment puis-je découvrir ces tests ?**

  Générez votre projet et vérifiez que la découverte basée sur les assemblys est activée sous **Outils** > **Options** > **Test**.

  La [découverte de tests en temps réel](https://go.microsoft.com/fwlink/?linkid=862824) correspond à la découverte de tests basée sur les sources. Elle ne peut pas découvrir les tests qui utilisent des théories, des adaptateurs personnalisés, des caractéristiques personnalisées, des instructions `#ifdef`, etc., car ils sont définis au moment de l’exécution. Une build est nécessaire pour découvrir correctement ces tests. Dans Visual Studio 2017 version 15.6 et ultérieure, la découverte basée sur les assemblys (le découvreur traditionnel) s’exécute seulement après les builds. En d’autres termes, la découverte de tests en temps réel découvre autant de tests que possible au fur et à mesure que vous effectuez des modifications, et la découverte basée sur les assemblys permet de faire apparaître les tests définis dynamiquement après une build. La découverte de tests en temps réel améliore la réactivité, tout en vous permettant d’obtenir des résultats complets et précis après une build.

## <a name="test-explorer--plus-symbol"></a>Symbole « + » (plus) de l’Explorateur de tests
**Que signifie le signe plus (+) qui apparaît sur la ligne supérieure l’Explorateur de tests ?**

  Le signe « + » (plus) indique que d’autres tests peuvent être découverts après une build tant que la découverte basée sur les assemblys est activée. Il apparaît si des tests définis dynamiquement sont détectés dans votre projet.

  ![Signe plus sur la ligne de résumé](media/testex-plussymbol.png)

## <a name="assembly-based-discovery"></a>Découverte basée sur les assemblys
**La découverte basée sur les assemblys ne fonctionne plus avec mon projet. Comment puis-je la réactiver ?**

  Accédez à **Outils** > **Options** > **Test** et cochez la case **Découvrez également les tests des assemblys générés après les builds**.

  ![Option basée sur les assemblys](media/testex-toolsoptions.png)

## <a name="real-time-test-discovery"></a>Découverte de tests en temps réel
**Les tests s’affichent désormais automatiquement dans l’Explorateur de tests quand j’écris, sans que j’aie à générer mon projet. Que s’est-il passé ?**

  Cette fonctionnalité s’appelle la [découverte de tests en temps réel](https://go.microsoft.com/fwlink/?linkid=862824). Elle utilise un analyseur Roslyn pour découvrir les tests et renseigner l’Explorateur de tests en temps réel, sans que l’utilisateur ait à générer son projet. Pour plus d’informations sur le comportement de la découverte de tests pour les tests définis dynamiquement tels que les théories ou les caractéristiques personnalisées, consultez le FAQ nº 1.

## <a name="real-time-test-discovery-compatibility"></a>Compatibilité de la découverte de tests en temps réel
**Quels langages et quelles infrastructures de test peuvent utiliser la découverte de tests en temps réel ?**

  La [découverte de tests en temps réel](https://go.microsoft.com/fwlink/?linkid=862824) fonctionne uniquement avec les langages managés (C# et Visual Basic), car elle utilise le compilateur Roslyn. À l’heure actuelle, la découverte de test en temps réel fonctionne uniquement avec les infrastructures xUnit, NUnit et MSTest.

## <a name="test-explorer-logs"></a>Journaux de l’Explorateur de tests
**Comment activer les journaux pour l’Explorateur de tests ?**

  Accédez à **Outils** > **Options** > **Test** et recherchez la section Journalisation.

## <a name="uwp-test-discovery"></a>Découverte de tests UWP
**Pourquoi dois-je d’abord déployer mon application pour que mes tests soient découverts dans des projets UWP ?**

  Les tests UWP ciblent un runtime différent quand l’application est déployée. Pour découvrir de manière précise les tests pour les projets UWP, vous devez donc non seulement générer votre projet, mais aussi le déployer.

## <a name="test-explorer-sorting"></a>Tri dans l’Explorateur de tests
**Comment fonctionne le tri des résultats de tests dans l’affichage des hiérarchies ?**

  L’affichage des hiérarchies trie les tests par ordre alphabétique et non par résultat. Les autres paramètres de regroupement trient normalement les résultats de tests par résultat, puis par ordre alphabétique. Consultez les différentes options de regroupement dans l’image suivante à des fins de comparaison. Vous pouvez fournir des commentaires sur la conception [dans ce problème GitHub](https://github.com/Microsoft/vstest/issues/1425).

  ![SortingExamples](media/testex-sortingex.png)

## <a name="test-explorer-hierarchy-view"></a>Vue de la hiérarchie de l’Explorateur de tests
**La vue de la hiérarchie inclut des icônes passed (réussi), failed (échec), skipped (ignoré) et not run (non exécuté) en regard des regroupements Projet, Espace de noms et Classe. Que signifient ces icônes ?**

  Les icônes en regard des regroupements Projet, Espace de noms et Classe reflètent l’état des tests dans le regroupement. Consultez le tableau suivant.

  ![Icônes de la hiérarchie de l’Explorateur de tests](media/testex-hierarchyicons.png)

## <a name="search-by-file-path"></a>Rechercher par chemin d’accès du fichier
**Il n’y a plus de filtre « Chemin d’accès du fichier » dans la zone de recherche de l’explorateur de tests.**

Le filtre de chemin d’accès du fichier dans la zone de recherche de l’**explorateur de tests** a été supprimé dans Visual Studio 2017, version 15.7, préversion 3. Cette fonctionnalité était très peu utilisée, et l’explorateur de tests peut récupérer des méthodes de test plus rapidement en excluant cette fonctionnalité. Si cette modification interrompt votre flux de développement, faites-le nous savoir en envoyant vos commentaires à la [Communauté des développeurs](https://developercommunity.visualstudio.com/).

## <a name="remove-undocumented-interfaces"></a>Supprimer des interfaces non documentées
**Certaines API liées aux tests ne sont plus présentes dans Visual Studio 2019. Que s’est-il passé ?**
Dans Visual Studio 2019, certaines API de fenêtre de test, qui étaient auparavant dites publiques mais qui n’ont jamais été officiellement documentées, seront retirées. Elles avaient été marquées comme étant « déconseillées » dans Visual Studio 2017 pour avertir à l’avance les personnes chargées de la maintenance des extensions. À notre connaissance, très peu d’extensions avaient trouvé ces API et en dépendaient. Il s’agit notamment de `IGroupByProvider`, `IGroupByProvider<T>`, `KeyComparer`, `ISearchFilter`, `ISearchFilterToken`, `ISearchToken` et `SearchFilterTokenType`. Si ce changement affecte votre extension, faites-le nous savoir en soumettant un rapport de bogue dans la [Communauté des développeurs](https://developercommunity.visualstudio.com).

## <a name="test-adapter-nuget-reference"></a>Référence NuGet sur l’adaptateur de test
**Dans Visual Studio 2017 version 15.8, mes tests sont détectés, mais ne s’exécutent pas.**

Tous les projets de test doivent inclure leur référence d’adaptateur de test .NET NuGet dans leur fichier .csproj. Dans le cas contraire, la sortie de test suivante s’affiche dans le projet si la découverte par une extension de l’adaptateur de test est lancée après une build ou si l’utilisateur tente d’exécuter les tests sélectionnés : 

Le **projet de test{} ne référence aucun adaptateur .NET NuGet. La découverte ou l’exécution de tests risquent de ne pas fonctionner pour ce projet. Il est recommandé de référencer les adaptateurs de test NuGet dans chaque projet de test .NET de la solution.**

Au lieu d’utiliser des extensions d’adaptateur de test, les projets doivent utiliser les packages NuGet de l’adaptateur de test. Cela améliore considérablement les performances et entraîne moins de problèmes avec l’intégration continue. En savoir plus sur la dépréciation de l’Extension de l’adaptateur de Test .NET dans les [notes de version](/visualstudio/releasenotes/vs2017-preview-relnotes#testadapterextension).

> [!NOTE]
> Si vous utilisez l’adaptateur de test NUnit 2 et que vous ne pouvez pas migrer vers l’adaptateur de test NUnit 3, vous pouvez désactiver ce nouveau comportement de la découverte dans Visual Studio version 15.8 dans **Outils** > **Options**  >  **Test**. 

  ![Comportement de l’adaptateur de l’Explorateur de tests dans les options des outils](media/testex-adapterbehavior.png)

## <a name="uwp-testcontainer-was-not-found"></a>TestContainer UWP est introuvable
**Mes tests UWP ne sont plus exécutés dans Visual Studio 2017 version 15.7 et ultérieure.**

Les projets de test UWP récents spécifient une propriété de génération de plateforme de test qui permet de meilleures performances pour identifier les applications de test. Si vous avez un projet de test UWP qui a été initialisé avant Visual Studio version 15.7, vous pouvez voir l’erreur suivante dans **Sortie** > **Tests** :

**System.AggregateException : Une ou plusieurs erreurs se sont produites. ---> System.InvalidOperationException : Le TestContainer suivant est introuvable {} sur Microsoft.VisualStudio.TestWindow.Controller.TestContainerProvider <GetTestContainerAsync>d__61.MoveNext()**
  
Pour résoudre ce problème :
- Mettez à jour votre propriété de génération de projet de test vers ceci :

```XML
<UnitTestPlatformVersion Condition="'$(UnitTestPlatformVersion)' == ''">$(VisualStudioVersion)</UnitTestPlatformVersion>
```

- Mettez à jour la version du SDK TestPlatform vers ceci :

```XML
<SDKReference Include="TestPlatform.Universal, Version=$(UnitTestPlatformVersion)" />
```

## <a name="using-feature-flags"></a>Utiliser les indicateurs de fonctionnalités
**Comment puis-je activer les indicateurs de fonctionnalités pour tester les nouvelles fonctionnalités de test ?**

Les indicateurs de fonctionnalités servent à fournir des parties expérimentales ou inachevées du produit à des utilisateurs passionnés qui souhaitent envoyer des commentaires avant le lancement officiel des fonctionnalités. Ils peuvent affecter votre expérience IDE. Utilisez-les uniquement dans des environnements de développement sécurisés, tels que des machines virtuelles. Les indicateurs de fonctionnalités sont toujours des paramètres que vous utilisez à vos risques et périls. Vous pouvez activer les fonctionnalités expérimentales à l’aide de [l’extension des indicateurs de fonctionnalités](https://marketplace.visualstudio.com/items?itemName=PaulHarrington.FeatureFlagsExtension) ou de l’invite de commandes développeur.

![Extension Feature Flag](media/testex-featureflag.png)

Pour activer un indicateur de fonctionnalité à l’aide de l’invite de commandes développeur Visual Studio, utilisez la commande suivante. Modifiez le chemin d’accès à l’emplacement d’installation de Visual Studio sur votre ordinateur et modifiez la clé de Registre en fonction de l’indicateur de fonctionnalité souhaité.

```shell
vsregedit set “C:\Program Files (x86)\Microsoft Visual Studio\Preview\Enterprise" HKLM FeatureFlags\TestingTools\UnitTesting\HierarchyView Value dword 1
```

> [!NOTE]
> Vous pouvez désactiver l’indicateur à l’aide de la même commande, en utilisant la valeur 0 au lieu de 1 après dword.

## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=fullName>
- [Créer et exécuter des tests unitaires pour le code existant](http://msdn.microsoft.com/e8370b93-085b-41c9-8dec-655bd886f173)
- [Tests unitaires sur votre code](unit-test-your-code.md)
- [Questions fréquentes concernant Live Unit Testing](live-unit-testing-faq.md)
