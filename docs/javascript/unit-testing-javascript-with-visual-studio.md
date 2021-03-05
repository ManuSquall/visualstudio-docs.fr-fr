---
title: Tests unitaires JavaScript et TypeScript
description: Visual Studio fournit la prise en charge des tests unitaires du code JavaScript et TypeScript à l’aide de Node.js Tools pour Visual Studio
ms.date: 07/06/2020
ms.topic: how-to
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jmartens
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 04ef9834fdc66256b601ecdcf156e4d290447ce3
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102171316"
---
# <a name="unit-testing-javascript-and-typescript-in-visual-studio"></a>Test unitaire JavaScript et TypeScript dans Visual Studio

Node.js Tools pour Visual Studio vous permet d’écrire et d’exécuter des tests unitaires à l’aide de certains des frameworks JavaScript les plus courants sans avoir besoin de passer à une invite de commandes.

Les frameworks pris en charge sont :
* Mocha ([mochajs.org](https://mochajs.org/))
* Jasmine ([Jasmine.github.io](https://jasmine.github.io/))
* Tape ([github.com/substack/tape](https://github.com/substack/tape))
* Jest ([jestjs.io](https://jestjs.io/))
* Export Runner (ce framework est spécifique à Node.js Tools pour Visual Studio)

Si votre framework préféré n’est pas pris en charge, consultez [Ajouter la prise en charge d’un framework de tests unitaires](#addingFramework) pour plus d’informations sur l’ajout d’une prise en charge.

## <a name="write-unit-tests"></a>Écrire des tests unitaires

Avant d’ajouter des tests unitaires à votre projet, vérifiez que le framework que vous envisagez d’utiliser est installé localement dans votre projet. Effectuez facilement cette opération à l’aide de la [fenêtre d’installation du package npm](npm-package-management.md#npmInstallWindow).

La meilleure façon d’ajouter des tests unitaires à votre projet consiste à créer un dossier *tests* dans votre projet et à le définir comme racine de test dans les propriétés du projet. Vous devez également sélectionner le framework de tests que vous souhaitez utiliser.

![Définir la racine de test et le framework de tests](../javascript/media/unit-test-project-properties.png)

Vous pouvez ajouter des tests vides simples à votre projet à l’aide de la boîte de dialogue **Ajouter un nouvel élément**. JavaScript et TypeScript sont tous deux pris en charge dans le même projet.

![Ajouter un nouveau test unitaire](../javascript/media/unit-test-add-new-item.png)

Pour un test unitaire Mocha, utilisez le code suivant :

```javascript
var assert = require('assert');

describe('Test Suite 1', function() {
    it('Test 1', function() {
        assert.ok(true, "This shouldn't fail");
    })

    it('Test 2', function() {
        assert.ok(1 === 1, "This shouldn't fail");
        assert.ok(false, "This should fail");
    })
})
```

Si vous n’avez pas défini les options de test unitaire dans les propriétés du projet, vous devez vérifier que la propriété **Framework de tests** dans la fenêtre **Propriétés** a pour valeur le framework de tests correct pour vos fichiers de test unitaire. Cette opération est effectuée automatiquement par les modèles de fichier de test unitaire.

![Framework de test](../javascript/media/UnitTestsFrameworkMocha.png)

> [!Note]
> Les options de test unitaire sont prioritaires sur les paramètres des fichiers individuels.

Après l’ouverture de l’Explorateur de tests (choisissez **tester** l’Explorateur de  >    >  **tests** Windows), Visual Studio Découvre et affiche les tests. Si les tests ne sont pas visibles au départ, regénérez le projet pour actualiser la liste.

![Explorateur de tests](../javascript/media/UnitTestsDiscoveryMocha.png)

> [!NOTE]
> Pour la machine à écrire, n’utilisez pas l' `outdir` `outfile` option ou dans *tsconfig.js*, car l’Explorateur de tests ne pourra pas trouver vos tests unitaires.

## <a name="run-tests"></a>Exécuter les tests

Vous pouvez exécuter des tests dans Visual Studio ou à partir de la ligne de commande.

### <a name="run-tests-in-visual-studio"></a>Exécuter des tests dans Visual Studio

::: moniker range=">=vs-2019"
Vous pouvez exécuter les tests en cliquant sur le lien **Exécuter tout** dans l’Explorateur de tests. Ou bien, vous pouvez exécuter des tests en sélectionnant un ou plusieurs tests ou groupes, en cliquant avec le bouton droit et en sélectionnant **exécuter** dans le menu contextuel. Les tests sont exécutés en arrière-plan et l’Explorateur de tests met automatiquement à jour et affiche les résultats. En outre, vous pouvez également déboguer les tests sélectionnés en cliquant avec le bouton droit et en sélectionnant **Déboguer**.
::: moniker-end
::: moniker range="vs-2017"
Vous pouvez exécuter les tests en cliquant sur le lien **Exécuter tout** dans l’Explorateur de tests. Vous pouvez aussi exécuter des tests en sélectionnant un ou plusieurs tests ou groupes, en effectuant un clic droit, puis en sélectionnant **Exécuter les tests sélectionnés** dans le menu contextuel. Les tests sont exécutés en arrière-plan et l’Explorateur de tests met automatiquement à jour et affiche les résultats. En outre, vous pouvez également déboguer les tests sélectionnés en sélectionnant **Déboguer les tests sélectionnés**.
::: moniker-end

Pour la machine à écrire, les tests unitaires sont exécutés sur le code JavaScript généré.

> [!NOTE]
> Dans la plupart des scénarios de création d’une machine à écrire, vous pouvez déboguer un test unitaire en définissant un point d’arrêt dans le code machine à écrire, en cliquant avec le bouton droit sur un test dans l’Explorateur de tests, puis Dans les scénarios plus complexes, tels que certains scénarios qui utilisent des mappages de source, vous pouvez avoir des difficultés à atteindre des points d’arrêt dans le code machine à écrire. Pour résoudre ce problème, essayez d’utiliser le `debugger` mot clé.

> [!NOTE]
> Nous ne prenons actuellement pas en charge les tests de profilage, ou couverture du code.

### <a name="run-tests-from-the-command-line"></a>Exécuter des tests à partir de la ligne de commande

Vous pouvez exécuter les tests à partir de [invite de commandes développeur pour Visual Studio](../ide/reference/command-prompt-powershell.md) à l’aide de la commande suivante :

```
vstest.console.exe <path to project file>\NodejsConsoleApp23.njsproj /TestAdapterPath:<VisualStudioFolder>\Common7\IDE\Extensions\Microsoft\NodeJsTools\TestAdapter
```

Cette commande propose une sortie du type suivant :

```
Microsoft (R) Test Execution Command Line Tool Version 15.5.0
Copyright (c) Microsoft Corporation.  All rights reserved.

Starting test execution, please wait...
Processing: NodejsConsoleApp23\NodejsConsoleApp23\UnitTest1.js
  Creating TestCase:NodejsConsoleApp23\NodejsConsoleApp23\UnitTest1.js::Test Suite 1 Test 1::mocha
  Creating TestCase:NodejsConsoleApp23\NodejsConsoleApp23\UnitTest1.js::Test Suite 1 Test 2::mocha
Processing finished for framework of Mocha
Passed   Test Suite 1 Test 1
Standard Output Messages:
 Using default Mocha settings
 1..2
 ok 1 Test Suite 1 Test 1

Failed   Test Suite 1 Test 2
Standard Output Messages:
 not ok 1 Test Suite 1 Test 2
   AssertionError [ERR_ASSERTION]: This should fail
       at Context.<anonymous> (NodejsConsoleApp23\NodejsConsoleApp23\UnitTest1.js:10:16)

Total tests: 2. Passed: 1. Failed: 1. Skipped: 0.
Test Run Failed.
Test execution time: 1.5731 Seconds
```

> [!NOTE]
> Si vous obtenez une erreur indiquant que *vstest.console.exe* est introuvable, vérifiez que vous avez ouvert l’invite de commandes développeur et non une invite de commandes standard.

## <a name="add-support-for-a-unit-test-framework"></a><a name="addingFramework"></a>Ajouter la prise en charge d’un framework de tests unitaires

Vous pouvez ajouter la prise en charge de frameworks de tests supplémentaires en implémentant la logique de découverte et d’exécution à l’aide de JavaScript. Pour cela, ajoutez un dossier portant le nom du framework de tests sous :

`<VisualStudioFolder>\Common7\IDE\Extensions\Microsoft\NodeJsTools\TestAdapter\TestFrameworks`

Ce dossier doit contenir un fichier JavaScript portant le même nom, qui exporte les deux fonctions suivantes :

* `find_tests`
* `run_tests`

Pour obtenir un bon exemple des implémentations `find_tests` et `run_tests`, consultez l’implémentation du framework de tests unitaires Mocha dans :

`<VisualStudioFolder>\Common7\IDE\Extensions\Microsoft\NodeJsTools\TestAdapter\TestFrameworks\mocha\mocha.js`

La découverte des frameworks de tests disponibles se produit au démarrage de Visual Studio. Si un framework est ajouté pendant que Visual Studio est en cours d’exécution, redémarrez Visual Studio pour détecter le framework. Toutefois, vous n’avez pas besoin de redémarrer quand vous apportez des modifications à l’implémentation.

## <a name="unit-tests-in-other-project-types"></a>Tests unitaires dans d’autres types de projet

Vous n’êtes pas limité à l’écriture de tests unitaires juste dans vos projets Node.js. Quand vous ajoutez les propriétés TestFramework et TestRoot à un projet C# ou Visual Basic, ces tests sont énumérés et vous pouvez les exécuter en utilisant la fenêtre Explorateur de tests.

Pour ce faire, cliquez sur le nœud du projet dans l’Explorateur de solutions, choisissez **Décharger le projet**, puis choisissez **Modifier le projet**. Ensuite, dans le fichier projet, ajoutez les deux éléments suivants à un groupe de propriétés.

> [!IMPORTANT]
> Vérifiez qu’aucune condition n’est spécifiée pour le groupe de propriétés auquel vous ajoutez les éléments.
> Le cas échéant, cela peut entraîner un comportement inattendu.

```xml
<PropertyGroup>
    <JavaScriptTestRoot>tests\</JavaScriptTestRoot>
    <JavaScriptTestFramework>Tape</JavaScriptTestFramework>
</PropertyGroup>
```

Ensuite, ajoutez vos tests dans le dossier racine de test que vous avez spécifié : ils sont alors disponibles pour être exécutés dans la fenêtre Explorateur de tests. S’ils n’apparaissent pas immédiatement, il peut être nécessaire de regénérer le projet.

### <a name="unit-test-net-core-and-net-standard"></a>Test unitaire dans .NET Core et .NET Standard

En plus des propriétés ci-dessus, vous devez également installer le package NuGet [Microsoft.JavaScript.UnitTest](https://www.nuget.org/packages/Microsoft.JavaScript.UnitTest/) et définir la propriété :

```xml
<PropertyGroup>
    <GenerateProgramFile>false</GenerateProgramFile>
</PropertyGroup>
```

Certaines infrastructures de test peuvent nécessiter des packages NPM supplémentaires pour la détection des tests. Par exemple, Jest requiert le package NPM jest-Editor-support. Si nécessaire, consultez la documentation relative à l’infrastructure spécifique.
