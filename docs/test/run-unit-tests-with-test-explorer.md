---
title: Exécuter, générer et déboguer des tests unitaires avec l’Explorateur de tests
description: Découvrez comment exécuter des tests avec l’Explorateur de tests dans Visual Studio. Cette rubrique explique comment activer des séries de tests automatiques après une génération, voir les résultats des tests, regrouper et filtrer la liste de tests, créer des sélections, déboguer les tests et utiliser des raccourcis de test.
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
f1_keywords:
- vs.unittesting.testexplorer.overview
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 3733588c1601f07c23ce9d85be9367a148e503de
ms.sourcegitcommit: e5a382de633156b85b292f35e3d740f817715d47
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/12/2018
ms.locfileid: "38977789"
---
# <a name="run-unit-tests-with-test-explorer"></a>Exécuter des tests unitaires avec l'Explorateur de tests

Utilisez **l’Explorateur de tests** pour exécuter des tests unitaires à partir de Visual Studio ou des projets de tests unitaires tiers. Vous pouvez également utiliser **l’Explorateur de tests** pour regrouper les tests en catégories, filtrer la liste de tests, et créer, enregistrer et exécuter des sélections de tests. Vous pouvez déboguer des tests et analyser les performances des tests et la couverture du code.

Visual Studio inclut les infrastructures de tests unitaires Microsoft pour le code managé comme pour le code natif. Cependant, **l’Explorateur de tests** peut également exécuter n’importe quel framework de tests unitaires ayant un adaptateur implémenté pour l’Explorateur de tests. Pour plus d’informations sur l’installation des frameworks de tests unitaires tiers, consultez [Installer des frameworks de tests unitaires tiers](../test/install-third-party-unit-test-frameworks.md).

**L’Explorateur de tests** peut exécuter des tests à partir de plusieurs projets de tests dans une solution et à partir de classes de test qui font partie des projets de code en production. Les projets de test peuvent utiliser différentes infrastructures de tests unitaires. Quand le code testé est écrit pour le .NET Framework, le projet de test peut être écrit dans n'importe quel langage qui cible également le .NET Framework, quel que soit le langage du code cible. Les projets de code C/C++ natifs doivent être testés à l'aide d'une infrastructure de tests unitaires C++. Pour plus d’informations, consultez [Écriture de tests unitaires pour C/C++](writing-unit-tests-for-c-cpp.md).

## <a name="run-tests-in-test-explorer"></a>Exécuter des tests dans l’explorateur de tests

Quand vous générez le projet de test, les tests s’affichent dans l’explorateur de tests. Si l’explorateur de tests n’est pas visible, sélectionnez **Test** dans le menu Visual Studio et choisissez **Fenêtres**, puis **Explorateur de tests**.

![Explorateur de tests unitaires](../test/media/ute_failedpassednotrunsummary.png)

Tandis que vous exécutez, écrivez et réexécutez vos tests, l'Explorateur de tests affiche les résultats dans les groupes par défaut **Échecs de tests**, **Tests réussis**, **Tests ignorés** et **Tests non exécutés**. Vous pouvez modifier la façon dont l'Explorateur de tests regroupe vos tests.

Vous pouvez effectuer la majeure partie du travail de recherche, d'organisation et d'exécution des tests à partir de la barre d'outils de l'Explorateur de tests.

![Exécuter des tests à partir de la barre d'outils de l'explorateur de tests](../test/media/ute_toolbar.png)

### <a name="run-tests"></a>Exécuter les tests

Vous pouvez exécuter tous les tests dans la solution, tous les tests dans un groupe, ou un ensemble de tests que vous sélectionnez. Effectuez l’une des opérations suivantes :

- Pour exécuter tous les tests dans une solution, choisissez **Exécuter tout**.

- Pour exécuter tous les tests dans un groupe par défaut, choisissez **Exécuter**, puis le groupe dans le menu.

- Sélectionnez les différents tests à exécuter, ouvrez le menu contextuel pour un test sélectionné, puis choisissez **Exécuter les tests sélectionnés**.

- Si les tests individuels n’ont aucune dépendance qui les empêche d’être exécutés dans n’importe quel ordre, activez l’exécution parallèle des tests avec le bouton bascule ![UTE&#95;parallelicon&#45;small](../test/media/ute_parallelicon-small.png) dans la barre d’outils. Cela peut réduire sensiblement le temps nécessaire pour exécuter tous les tests.

La barre Réussite/Échec en haut de la fenêtre Explorateur de tests est animée pendant l'exécution des tests. À la fin de la série de tests, la barre Réussite/Échec devient verte si tous les tests ont réussi ou rouge si un test a échoué.

### <a name="run-tests-after-every-build"></a>Exécuter des tests après chaque génération

|Bouton|Description|
|-|-|
|![Exécuter après les builds](../test/media/ute_runafterbuild_btn.png)|Pour exécuter vos tests unitaires après chaque génération locale, choisissez **Test** dans le menu standard, puis **Exécuter les tests après la génération** dans la barre d'outils de l'Explorateur de tests.|

## <a name="view-test-results"></a>Afficher les résultats des tests

Tandis que vous exécutez, écrivez et réexécutez vos tests, l'Explorateur de tests affiche les résultats dans les groupes **Échecs de tests**, **Tests réussis**, **Tests ignorés** et **Tests non exécutés**. Le volet d'informations en bas de l'Explorateur de tests affiche un résumé de la série de tests.

### <a name="view-test-details"></a>Afficher les détails du test

Pour afficher les détails d'un test individuel, sélectionnez le test.

![Détails de l'exécution de tests](../test/media/ute_testdetails.png)

Le volet d'informations de test affiche les informations suivantes :

- Nom du fichier source et numéro de ligne de la méthode de test.

- Statut du test.

- Temps d'exécution de la méthode.

Si le test échoue, le volet d'informations affiche également :

- Le message retourné par l'infrastructure de tests unitaires pour le test.

- La trace de la pile au moment de l'échec du test.

### <a name="view-the-source-code-of-a-test-method"></a>Afficher le code source d'une méthode de test

 Pour afficher le code source d’une méthode de test dans l’éditeur Visual Studio, sélectionnez le test, puis choisissez **Ouvrir un test** dans le menu contextuel (clavier : **F12**).

## <a name="group-and-filter-the-test-list"></a>Regrouper et filtrer la liste de tests

L'Explorateur de tests vous permet de regrouper vos tests en catégories prédéfinies. La plupart des infrastructures de tests unitaires qui s'exécutent dans l'Explorateur de tests vous permettent de définir vos propres catégories et paires catégorie/valeur pour regrouper vos tests. Vous pouvez également filtrer la liste de tests en mettant en correspondance les chaînes avec les propriétés de test.

### <a name="group-tests-in-the-test-list"></a>Regrouper des tests dans la liste de tests

 Pour modifier le mode d’organisation des tests, cliquez sur la flèche vers le bas à côté du bouton **Grouper par** ![Bouton Grouper de l’Explorateur de tests](../test/media/ute_groupby_btn.png) et sélectionnez un nouveau critère de regroupement.

 ![Grouper les tests par catégorie dans l’Explorateur de tests](../test/media/ute_groupbycategory.png)

### <a name="test-explorer-groups"></a>Groupes de l'explorateur de tests

|Regrouper|Description|
|-----------|-----------------|
|**Durée**|Regroupe les tests selon la durée d'exécution : **Rapide**, **Moyenne**et **Lente**.|
|**Résultat**|Regroupe les tests selon les résultats de l'exécution : **Échecs de tests**, **Tests ignorés**, **Tests réussis**.|
|**Caractéristiques**|Regroupe les tests selon les paires catégorie/valeur que vous définissez. La syntaxe permettant de spécifier les catégories et les valeurs des caractéristiques est définie par l'infrastructure de tests unitaires.|
|**Projet**|Regroupe les tests selon le nom des projets.|

### <a name="group-by-traits"></a>Regrouper par caractéristiques

 Une caractéristique est habituellement une paire nom/valeur de catégorie, mais elle peut également être une catégorie unique. Des caractéristiques peuvent être assignées aux méthodes identifiées comme une méthode de test par l'infrastructure de tests unitaires. Une infrastructure de tests unitaires peut définir des catégories de caractéristiques. Vous pouvez ajouter des valeurs aux catégories de caractéristiques pour définir vos propres paires nom/valeur de catégorie. La syntaxe permettant de spécifier les catégories et les valeurs des caractéristiques est définie par l'infrastructure de tests unitaires.

 **Caractéristiques dans le framework de tests unitaires Microsoft pour le code managé**

 Dans l'infrastructure de tests unitaires Microsoft pour les applications managées, vous définissez une paire nom/valeur de caractéristique dans un attribut  <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestPropertyAttribute> . L'infrastructure de tests contient également les caractéristiques prédéfinies suivantes : 

|Caractéristique|Description|
|-----------|-----------------|
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.OwnerAttribute>|La catégorie Owner est définie par l'infrastructure de tests unitaires et nécessite que vous fournissiez une valeur de chaîne du propriétaire.|
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.PriorityAttribute>|La catégorie Priority est définie par l'infrastructure de tests unitaires et nécessite que vous fournissiez une valeur entière de la priorité.|
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCategoryAttribute>|L'attribut TestCategory vous permet de fournir une catégorie sans valeur. Une catégorie définie par l'attribut TestCategory peut également être la catégorie d'un attribut TestProperty.|
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestPropertyAttribute>|L'attribut TestProperty vous permet de définir la paire catégorie/valeur de caractéristique.|

 **Caractéristiques dans le framework de tests unitaires Microsoft pour C++** Consultez [Guide pratique pour utiliser le framework de tests unitaires Microsoft pour C++](how-to-use-microsoft-test-framework-for-cpp.md).

### <a name="search-and-filter-the-test-list"></a>Rechercher et filtrer la liste de tests

Vous pouvez utiliser des filtres de l'Explorateur de tests pour limiter les méthodes de test dans les projets que vous affichez et exécutez.

Quand vous tapez une chaîne dans la zone de recherche de l’Explorateur de tests et appuyez sur Entrée, la liste de tests est filtrée pour afficher uniquement les tests dont les noms qualifiés complets contiennent la chaîne.

Pour filtrer selon un autre critère :

1. Ouvrez la liste déroulante à droite de la zone de recherche.

2. Choisissez un nouveau critère.

3. Entrez la valeur de filtre entre guillemets.

![Filtrer les tests dans l’Explorateur de tests](../test/media/ute_filtertestlist.png)

> [!NOTE]
> Les recherches ne respectent pas la casse et associent la chaîne spécifiée à une partie de la valeur de critère.

|Qualificateur|Description|
|---------------|-----------------|
|**Caractéristique**|Recherche la catégorie et la valeur de caractéristique pour les correspondances. La syntaxe permettant de spécifier les catégories et les valeurs des caractéristiques est définie par l'infrastructure de tests unitaires.|
|**Projet**|Recherche les noms de projet de test pour les correspondances.|
|**Message d'erreur**|Recherche les messages d'erreur définis par l'utilisateur retournés par des assertions ayant échoué pour les correspondances.|
|**Chemin d'accès au fichier**|Recherche le nom de fichier qualifié complet des fichiers sources de test pour les correspondances.|
|**Nom qualifié complet**|Recherche le nom de fichier qualifié complet des espaces de noms, des classes et des méthodes de test pour les correspondances.|
|**Sortie**|Recherche les messages d'erreur définis par l'utilisateur qui sont écrits dans la sortie standard (stdout) ou une erreur standard (stderr). La syntaxe permettant de spécifier les messages de sortie est définie par l'infrastructure de tests unitaires.|
|**Résultat**|Recherche les noms de catégorie de l'Explorateur de tests pour les correspondances : **Échecs de tests**, **Tests ignorés**, **Tests réussis**.|

Pour exclure un sous-ensemble des résultats d'un filtre, utilisez la syntaxe suivante :

```cpp
FilterName:"Criteria" -FilterName:"SubsetCriteria"
```

Par exemple, `FullName:"MyClass" - FullName:"PerfTest"` retourne tous les tests qui incluent « MyClass » dans leur nom, sauf ceux qui incluent également « PerfTest » dans leur nom.

## <a name="create-custom-playlists"></a>Créer des sélections personnalisées

 Vous pouvez créer et enregistrer une liste de tests que vous souhaitez exécuter ou visualiser en tant que groupe. Quand vous sélectionnez une sélection, les tests de la liste sont affichés dans l'Explorateur de tests. Vous pouvez ajouter un test à plusieurs sélections, et tous les tests de votre projet sont disponibles quand vous choisissez la sélection par défaut **Tous les tests** .

 ![Choisir une sélection](../test/media/ute_playlist.png)

 **Pour créer une sélection**, sélectionnez un ou plusieurs tests dans l'Explorateur de tests. Dans le menu contextuel, sélectionnez **Ajouter à la sélection**, **NewPlaylist**. Enregistrez le fichier sous le nom et à l'emplacement que vous spécifiez dans la boîte de dialogue **Créer une sélection** .

 **Pour ajouter des tests à une sélection**, sélectionnez un ou plusieurs tests dans l'Explorateur de tests. Dans le menu contextuel, choisissez **Ajouter à la sélection**, puis la sélection à laquelle vous souhaitez ajouter des tests.

 **Pour ouvrir une sélection**, choisissez Test, Sélection dans le menu Visual Studio, puis choisissez une sélection dans la liste de sélections récemment utilisées ou choisissez Ouvrir la sélection pour spécifier le nom et l'emplacement de la sélection.

 Si les tests individuels n’ont aucune dépendance qui les empêche d’être exécutés dans n’importe quel ordre, activez l’exécution parallèle des tests avec le bouton bascule ![UTE&#95;parallelicon&#45;small](../test/media/ute_parallelicon-small.png) dans la barre d’outils. Cela peut réduire sensiblement le temps nécessaire pour exécuter tous les tests.

## <a name="debug-and-analyze-unit-tests"></a>Déboguer et analyser des tests unitaires

### <a name="debug-unit-tests"></a>Déboguer les tests unitaires

Vous pouvez utiliser l'Explorateur de tests pour démarrer une session de débogage de vos tests. L'exécution pas à pas de votre code avec le débogueur Visual Studio vous conduit de manière transparente à des allers et retours entre les tests unitaires et le projet testé. Pour démarrer le débogage :

1. Dans l’éditeur Visual Studio, définissez un point d’arrêt dans une ou plusieurs méthodes de test que vous souhaitez déboguer.

    > [!NOTE]
    > Comme les méthodes de test peuvent s'exécuter dans n'importe quel ordre, définissez les points d'arrêt dans toutes les méthodes de test que vous souhaitez déboguer.

2. Dans l'Explorateur de tests, sélectionnez les méthodes de test, puis choisissez **Déboguer les tests sélectionnés** dans le menu contextuel.

 Pour plus d’informations sur le débogueur, consultez [Debugging in Visual Studio](../debugger/debugging-in-visual-studio.md).

### <a name="diagnose-test-method-performance-issues"></a>Diagnostiquer les problèmes de performances de méthode de test

 Pour diagnostiquer la raison pour laquelle une méthode de test est beaucoup trop longue, sélectionnez la méthode dans l'Explorateur de tests, puis choisissez Profil dans le menu contextuel. Consultez [Explorateur de performances](../profiling/performance-explorer.md).

### <a name="analyze-unit-test-code-coverage"></a>Analyser la couverture du code de test unitaire

Vous pouvez déterminer la quantité de code de votre produit qui est réellement testée par vos tests unitaires à l'aide de l'outil de couverture de code Visual Studio. Vous pouvez exécuter la couverture de code sur les tests sélectionnés ou sur tous les tests d'une solution.

Pour exécuter la couverture du code pour les méthodes de test dans une solution :

1. Choisissez **Tests** dans le menu Visual Studio, puis **Analyser la couverture du code**.

2. Sélectionnez l'une des commandes suivantes dans le sous-menu :

    - **Tests sélectionnés** exécute les méthodes de test que vous avez sélectionnées dans l'Explorateur de tests.

    - **Tous les tests** exécute toutes les méthodes de test de la solution.

La fenêtre Résultats de la couverture du code affiche le pourcentage des blocs du code du produit qui ont été testés par ligne, fonction, classe, espace de noms et module.

Pour plus d’informations, consultez [Utilisation de la couverture du code pour déterminer la quantité de code testé](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).

## <a name="test-shortcuts"></a>Raccourcis pour les tests

Vous pouvez exécuter les tests à partir de **l’Explorateur de tests** en cliquant avec le bouton droit dans l’éditeur de code sur un test et en sélectionnant **Exécuter le test**, ou en utilisant les [raccourcis de l’Explorateur de tests](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_testexplorerGLOBAL) par défaut dans Visual Studio. Certains raccourcis dépendent du contexte. Cela signifie qu’ils exécutent ou déboguent les tests en fonction de l’endroit où se trouve votre curseur dans l’éditeur de code. Si le curseur est à l’intérieur d’une méthode de test, cette méthode de test s’exécute. Si le curseur est au niveau de la classe, tous les tests de cette classe s’exécutent. C’est pareil pour le niveau d’espace de noms.

|Commandes fréquentes| Raccourcis clavier|
|--------------|------------------------|
|TestExplorer.DebugAllTestsInContext|Ctrl+R, Ctrl+T|
|TestExplorer.RunAllTestsInContext|Ctrl+R, T|

> [!NOTE]
> Vous ne pouvez pas exécuter un test dans une classe abstraite, car les tests sont seulement définis dans les classes abstraites et ne sont pas instanciés. Pour exécuter des tests dans des classes abstraites, créez une classe qui dérive de la classe abstraite.

## <a name="see-also"></a>Voir aussi

- [Tests unitaires sur votre code](../test/unit-test-your-code.md)
- [Exécuter un test unitaire comme processus 64 bits](../test/run-a-unit-test-as-a-64-bit-process.md)
