---
title: Questions fréquentes (FAQ) sur l’Explorateur de tests
description: Reportez-vous à ces questions fréquemment posées sur l’Explorateur de tests Visual Studio, qui incluent un dépannage courant.
ms.custom: SEO-VS-2020
ms.date: 06/25/2020
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
manager: jmartens
ms.openlocfilehash: 22ac969ba2ad918fcbeb7c53e04cd3f2b03a0431
ms.sourcegitcommit: d4887ef2ca97c55e2dad9f179eec2c9631d91c95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/06/2021
ms.locfileid: "108798568"
---
# <a name="visual-studio-test-explorer-faq"></a>FAQ concernant l’Explorateur de tests Visual Studio

## <a name="dynamic-test-discovery"></a>Découverte de tests dynamique

**L’Explorateur de tests ne découvre pas mes tests qui sont définis dynamiquement. (Par exemple, théories, adaptateurs personnalisés, caractéristiques personnalisées, #ifdefs, etc.) Comment puis-je découvrir ces tests ?**

::: moniker range=">=vs-2019"
Générez votre projet pour exécuter la découverte basée sur les assemblys.
::: moniker-end
::: moniker range="vs-2017"
Générez votre projet et vérifiez que la découverte basée sur les assemblys est activée sous **Outils** > **Options** > **Test**.
::: moniker-end
La [découverte de tests en temps réel](https://devblogs.microsoft.com/dotnet/real-time-test-discovery/) correspond à la découverte de tests basée sur les sources. Elle ne peut pas découvrir les tests qui utilisent des théories, des adaptateurs personnalisés, des caractéristiques personnalisées, des `#ifdef` instructions, etc., car elles sont définies au moment de l’exécution. Une build est nécessaire pour trouver ces tests avec précision. Dans Visual Studio 2017 version 15.6 et ultérieure, la découverte basée sur les assemblys (le découvreur traditionnel) s’exécute seulement après les builds. En d’autres termes, la découverte de tests en temps réel trouve autant de tests que possible au fur et à mesure que vous effectuez des modifications, et la découverte basée sur les assemblys permet de faire apparaître les tests définis dynamiquement après une build. La découverte de tests en temps réel améliore la réactivité, tout en vous permettant d’obtenir des résultats complets et précis après une build.

## <a name="test-explorer--plus-symbol"></a>Symbole « + » (plus) de l’Explorateur de tests

**Que signifie le signe plus (+) qui apparaît sur la ligne supérieure l’Explorateur de tests ?**

Le signe plus (+) indique que d’autres tests peuvent être découverts après une build quand la découverte basée sur les assemblys s’exécute. Ce symbole apparaît si des tests définis dynamiquement sont détectés dans votre projet.

![Signe plus sur la ligne de résumé](media/testex-plussymbol.png)

::: moniker range="vs-2017"
## <a name="assembly-based-discovery"></a>Découverte basée sur les assemblys

**La découverte basée sur les assemblys ne fonctionne plus pour mon projet. Comment faire le réactiver ?**

Accédez à **Outils** > **Options** > **Test** et cochez la case **Découvrez également les tests des assemblys générés après les builds**.

![Option basée sur les assemblys](media/testex-toolsoptions.png)
::: moniker-end

## <a name="real-time-test-discovery"></a>Découverte de tests en temps réel

**Les tests s’affichent désormais dans l’Explorateur de tests pendant que je tape, sans avoir à générer mon projet. Qu’est-ce qui a changé ?**

Cette fonctionnalité s’appelle la [découverte de tests en temps réel](https://devblogs.microsoft.com/dotnet/real-time-test-discovery/). Elle utilise un analyseur Roslyn pour trouver les tests et remplir l’Explorateur de tests en temps réel, sans que vous ayez à générer votre projet. Pour plus d’informations sur le comportement de la découverte de tests pour les tests définis dynamiquement, par exemple les théories ou les caractéristiques personnalisées, consultez [Découverte de tests dynamique](#dynamic-test-discovery).

## <a name="real-time-test-discovery-compatibility"></a>Compatibilité de la découverte de tests en temps réel

**Quels langages et quelles infrastructures de test peuvent utiliser la découverte de tests en temps réel ?**

La [découverte de tests en temps réel](https://devblogs.microsoft.com/dotnet/real-time-test-discovery/) fonctionne uniquement avec les langages managés (C# et Visual Basic), car elle utilise le compilateur Roslyn. Pour le moment, la découverte de tests en temps réel fonctionne uniquement avec les frameworks xUnit, NUnit et MSTest.

## <a name="test-explorer-logs"></a>Journaux de l’Explorateur de tests

**Comment activer les journaux pour l’Explorateur de tests ?**

Accédez à **Outils**  >  **options**  >  **test** et recherchez la section journalisation ici.

## <a name="uwp-test-discovery"></a>Découverte de tests UWP

**Pourquoi dois-je d’abord déployer mon application pour que mes tests soient découverts dans des projets UWP ?**

Les tests UWP ciblent un runtime différent quand l’application est déployée. Pour trouver de manière précise les tests pour les projets UWP, vous devez donc non seulement générer votre projet, mais aussi le déployer.

## <a name="test-explorer-sorting"></a>Tri dans l’Explorateur de tests

**Comment fonctionne le tri des résultats de tests dans l’affichage des hiérarchies ?**

L’affichage des hiérarchies trie les tests par ordre alphabétique et non par résultat. Les paramètres Group by précédents ont trié les résultats des tests par résultat, puis par ordre alphabétique. Vous pouvez toujours activer le tri par résultat en cliquant avec le bouton droit sur l’en-tête de colonne dans l’Explorateur de tests, en activant la colonne État, puis en cliquant sur l’en-tête de colonne État pour appliquer le tri sur cette colonne. Vous pouvez fournir des commentaires sur la conception dans ce [problème GitHub](https://github.com/Microsoft/vstest/issues/1425).

## <a name="test-explorer-hierarchy-view"></a>Vue de la hiérarchie de l’Explorateur de tests

**Dans l’affichage des hiérarchies, il existe des icônes réussite, échec, ignoré et ne pas exécuter en regard des regroupements de nœuds parents. Que signifient ces icônes ?**

Les icônes en regard des regroupements Projet, Espace de noms et Classe indiquent l’état des tests dans le regroupement. Consultez le tableau suivant.

![Icônes de la hiérarchie de l’Explorateur de tests](media/testex-hierarchyicons.png)

## <a name="search-by-file-path"></a>Rechercher par chemin d’accès du fichier

**Il n’y a plus de filtre « Chemin d’accès du fichier » dans la zone de recherche de l’explorateur de tests.**

Le filtre de chemin d’accès du fichier dans la zone de recherche de l’**Explorateur de tests** a été supprimé dans Visual Studio 2017, version 15.7. Cette fonctionnalité étant très peu utilisée, l’Explorateur de tests peut récupérer des méthodes de test plus rapidement en la laissant de côté. Si ce changement interrompt votre flux de développement, faites-le nous savoir en envoyant vos commentaires à la [Communauté des développeurs](https://aka.ms/feedback/suggest?space=8).

## <a name="remove-undocumented-interfaces"></a>Supprimer des interfaces non documentées

**Certaines API liées aux tests ne sont plus présentes dans Visual Studio 2019. Qu’est-ce qui a changé ?**

Dans Visual Studio 2019, certaines API de fenêtre de test, qui étaient auparavant dites publiques mais qui n’ont jamais été officiellement documentées, seront retirées. Elles avaient été marquées comme étant « déconseillées » dans Visual Studio 2017 pour avertir à l’avance les personnes chargées de la maintenance des extensions. À notre connaissance, très peu d’extensions avaient trouvé ces API et en dépendaient. Il s’agit notamment de `IGroupByProvider`, `IGroupByProvider<T>`, `KeyComparer`, `ISearchFilter`, `ISearchFilterToken`, `ISearchToken` et `SearchFilterTokenType`. Si ce changement affecte votre extension, faites-le nous savoir en entrant un bogue auprès de la [Communauté des développeurs](https://aka.ms/feedback/suggest?space=8).

## <a name="test-adapter-nuget-reference"></a>Référence NuGet sur l’adaptateur de test

**Dans Visual Studio 2017 version 15.8, mes tests sont détectés, mais ne s’exécutent pas.**

Tous les projets de test doivent inclure leur référence d’adaptateur de test .NET NuGet dans leur fichier .csproj. Dans le cas contraire, la sortie de test suivante s’affiche dans le projet si la découverte par une extension de l’adaptateur de test est lancée après une build ou si l’utilisateur tente d’exécuter les tests sélectionnés :

**Le projet {} de test ne fait référence à aucun adaptateur NuGet .net. La découverte de tests ou l’exécution peut ne pas fonctionner pour ce projet. Il est recommandé de référencer des adaptateurs de test NuGet dans chaque projet de test .NET de la solution.**

Au lieu d’utiliser des extensions d’adaptateur de test, les projets doivent utiliser les packages NuGet de l’adaptateur de test. Cette exigence améliore considérablement les performances et entraîne moins de problèmes avec l’intégration continue. En savoir plus sur la dépréciation de l’Extension de l’adaptateur de Test .NET dans les [notes de version](/visualstudio/releasenotes/vs2017-relnotes-v15.8#testadapterextension).

::: moniker range="vs-2017"
> [!NOTE]
> Si vous utilisez l’adaptateur de test NUnit 2 et que vous ne parvenez pas à migrer vers l’adaptateur de test NUnit 3, vous pouvez désactiver ce nouveau comportement de découverte dans Visual Studio version 15,8 dans **Outils**  >  **options**  >  **test**.

![Comportement de l’adaptateur de l’Explorateur de tests dans les options des outils](media/testex-adapterbehavior.png)
::: moniker-end

## <a name="uwp-testcontainer-was-not-found"></a>TestContainer UWP est introuvable

**Mes tests UWP ne sont plus exécutés dans Visual Studio 2017 versions 15.7 et ultérieures.**

Les projets de test UWP récents spécifient une propriété de génération de plateforme de test qui permet de meilleures performances pour identifier les applications de test. Si vous avez un projet de test UWP qui a été initialisé avant Visual Studio version 15,7, vous pouvez voir cette erreur dans les tests de **sortie**  >  :

**System.AggregateException : Une ou plusieurs erreurs se sont produites. ---> System.InvalidOperationException : Le TestContainer suivant est introuvable {} sur Microsoft.VisualStudio.TestWindow.Controller.TestContainerProvider \<GetTestContainerAsync>d__61.MoveNext()**

Pour résoudre ce problème :

- Mettez à jour votre propriété de génération de projet de test à l’aide du code suivant :

```XML
<UnitTestPlatformVersion Condition="'$(UnitTestPlatformVersion)' == ''">$(VisualStudioVersion)</UnitTestPlatformVersion>
```

- Mettez à jour la version du kit SDK TestPlatform à l’aide du code suivant :

```XML
<SDKReference Include="TestPlatform.Universal, Version=$(UnitTestPlatformVersion)" />
```
::: moniker range=">=vs-2019"
## <a name="using-preview-features"></a>Utilisation des fonctionnalités en version préliminaire

Dans Visual Studio 2019, vous pouvez choisir des fonctionnalités en version préliminaire dans **outils > Options > environnement > fonctionnalités préliminaires**.
::: moniker-end
::: moniker range=">=vs-2017"
## <a name="using-feature-flags"></a>Utiliser les indicateurs de fonctionnalités

**Comment puis-je activer les indicateurs de fonctionnalités pour tester les nouvelles fonctionnalités de test ?**

Les indicateurs de fonctionnalités servent à fournir des parties expérimentales ou inachevées du produit à des utilisateurs passionnés qui souhaitent envoyer des commentaires avant le lancement officiel des fonctionnalités. Ils peuvent affecter votre expérience IDE. Utilisez-les uniquement dans des environnements de développement sécurisés, tels que des machines virtuelles. Les indicateurs de fonctionnalités sont toujours des paramètres que vous utilisez à vos risques et périls. Vous pouvez activer les fonctionnalités expérimentales à l’aide de [l’extension des indicateurs de fonctionnalités](https://marketplace.visualstudio.com/items?itemName=PaulHarrington.FeatureFlagsExtension) ou de l’invite de commandes développeur.

![Extension Feature Flag](media/testex-featureflag.png)

Pour activer un indicateur de fonctionnalité à l’aide de l’invite de commandes développeur Visual Studio, utilisez la commande suivante. Changez le chemin de l’emplacement d’installation de Visual Studio sur votre machine, et remplacez la clé de Registre en fonction de l’indicateur de fonctionnalité souhaité.

```shell
vsregedit set “C:\Program Files (x86)\Microsoft Visual Studio\Preview\Enterprise" HKLM FeatureFlags\TestingTools\UnitTesting\HierarchyView Value dword 1
```

> [!NOTE]
> Vous pouvez désactiver l’indicateur à l’aide de la même commande, en utilisant la valeur 0 au lieu de 1 après dword.
::: moniker-end
## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=fullName>
- [Créer et exécuter des tests unitaires pour le code existant](/previous-versions/dd293546(v=vs.110))
- [Tests unitaires de votre code](unit-test-your-code.md)
- [Questions fréquentes concernant Live Unit Testing](live-unit-testing-faq.yml)