---
title: Options de ligne de commande MSTest
ms.date: 07/12/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: reference
helpviewer_keywords:
- vstest.console.exe
- command-line tests
ms.author: gewarren
author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7f090607f1ebae6a03c7f12536e0dd5d46199f6e
ms.sourcegitcommit: 7bb0225e1fd45999ce09e0b49c2cfae515c27e11
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2018
ms.locfileid: "45612660"
---
# <a name="vstestconsoleexe-command-line-options"></a>Options de ligne de commande VSTest.Console.exe

*VSTest.Console.exe* est l’outil en ligne de commande pour exécuter des tests. Vous pouvez spécifier plusieurs options dans un ordre quelconque dans la ligne de commande. Ces options sont répertoriées dans [Options de ligne de commande générales](#general-command-line-options).

> [!NOTE]
> L’adaptateur MSTest de Visual Studio fonctionne également en mode hérité (équivalent de l’exécution de tests avec *mstest.exe*) pour la compatibilité. En mode hérité, il ne peut pas tirer parti de la fonctionnalité TestCaseFilter. L’adaptateur peut basculer en mode hérité quand un fichier *testsettings* est spécifié, que **forcelegacymode** a la valeur **true** dans un fichier *runsettings*, ou à l’aide d’attributs comme **HostType**.
>
> Pour exécuter des tests automatisés sur un ordinateur basé sur une architecture ARM, vous devez utiliser *VSTest.Console.exe*.

## <a name="general-command-line-options"></a>Options de ligne de commande générales

Le tableau suivant répertorie toutes les options de *VSTest.Console.exe*, ainsi que leurs brèves descriptions. Vous pouvez voir un résumé semblable en tapant `VSTest.Console/?` sur une ligne de commande.

| Option | Description |
|---|---|
|**[*noms de fichiers de test*]**|Exécutez les tests à partir des fichiers spécifiés. Séparez les noms de fichiers de test par des espaces.<br />Exemples : `mytestproject.dll`, `mytestproject.dll myothertestproject.exe`|
|**/Settings:[*nom de fichier*]**|Exécutez les tests avec d'autres paramètres tels que les collecteurs de données.<br />Exemple : `/Settings:Local.RunSettings`|
|**/Tests:[*nom du test*]**|Exécutez les tests avec les noms qui contiennent les valeurs fournies. Pour fournir plusieurs valeurs, séparez-les par des virgules.<br />Exemple : `/Tests:TestMethod1,testMethod2`<br />L’option de ligne de commande **/Tests** ne peut pas être utilisée avec l’option de ligne de commande **/TestCaseFilter**.|
|**/Parallel**|Spécifie que les tests doivent être exécutés en parallèle. Par défaut, tout ou partie des cœurs disponibles sur la machine sont utilisables. Le nombre de cœurs à utiliser peut être configuré à l’aide d’un fichier de paramètres.|
|**/Enablecodecoverage**|Active l'adaptateur de données de diagnostic CodeCoverage dans la série de tests.<br />Les paramètres par défaut sont utilisés s'ils ne sont pas spécifiés à l'aide du fichier de paramètres.|
|**/InIsolation**|Exécute les tests dans un processus isolé.<br />En raison de cette isolation, il est moins probable que le processus *vstest.console.exe* soit arrêté sur une erreur dans les tests, mais les tests peuvent s’exécuter plus lentement.|
|**/UseVsixExtensions**|Grâce à cette option, le processus *vstest.console.exe* utilise ou ignore les extensions VSIX installées (le cas échéant) dans la série de tests.<br />Cette option est dépréciée. À compter de la prochaine version majeure de Visual Studio, cette option peut être supprimée. Envisagez d’utiliser des extensions disponibles en tant que package NuGet.<br />Exemple : `/UseVsixExtensions:true`|
|**/TestAdapterPath:[*chemin*]**|Force le processus *vstest.console.exe* à utiliser des adaptateurs de test personnalisés à partir d’un chemin spécifié (le cas échéant) dans la série de tests.<br />Exemple : `/TestAdapterPath:&lt;pathToCustomAdapters&gt;`|
|**/Platform:[*type de plateforme*]**|Architecture de plateforme cible à utiliser pour l'exécution des tests.<br />Les valeurs valides sont x86, x64 et ARM.|
|**/Framework: [*version de .Net Framework*]**|Version .Net Framework cible à utiliser pour l'exécution des tests.<br />Les valeurs valides sont Framework35, Framework40, Framework45 et FrameworkUap10.<br />Si la version cible de .Net Framework est spécifiée comme étant **Framework35**, les tests s’exécutent en « mode de compatibilité » CLR 4.0.<br />Exemple : `/Framework:framework40`|
|**/TestCaseFilter:[*expression*]**|Exécutez les tests qui correspondent à l'expression donnée.<br /><Expression\> est au format <propriété\>=<valeur\>[&#124;<Expression\>].<br />Exemple : `/TestCaseFilter:"Priority=1"`<br />Exemple : `/TestCaseFilter:"TestCategory=Nightly&#124;FullyQualifiedName=Namespace.ClassName.MethodName"`<br />L’option de ligne de commande **/TestCaseFilter** ne peut pas être utilisée avec l’option de ligne de commande **/Tests**. <br />Pour plus d’informations sur la création et l’utilisation d’expressions, consultez [Filtre TestCase](https://github.com/Microsoft/vstest-docs/blob/master/docs/filter.md).|
|**/?**|Affiche les informations d’utilisation.|
|**/Logger:[*uri/nom_convivial*]**|Spécifiez un journal pour les résultats de tests.<br />Par exemple, pour stocker les résultats dans les fichiers de résultats des tests de Visual Studio (TRX), utilisez **/Logger:trx**.<br />Exemple : Pour publier les résultats des tests dans Team Foundation Server, utilisez TfsPublisher :<br />**/logger:TfsPublisher;**<br />**Collection=<URL du projet\>;**<br />**BuildName=<nom de la build\>;**<br />**TeamProject=<nom du projet\>;**<br />**[;Platform=<par défaut « N’importe quelle UC »>]**<br />**[;Flavor=<par défaut « Debug »>]**<br />**[;RunTitle=<titre\>]**|
|**/ListTests:[*nom de fichier*]**|Répertorie les tests détectés dans le conteneur de tests donné.|
|**/ListDiscoverers**|Répertorie les découvreurs de test installés.|
|**/ListExecutors**|Répertorie les exécuteurs de test installés.|
|**/ListLoggers**|Répertorie les journaux de test installés.|
|**/ListSettingsProviders**|Répertorie les fournisseurs de paramètres installés.|
|**/Blame**|Effectue le suivi des tests à mesure qu’ils sont exécutés et, si le processus hôte des tests plante, émet les noms des tests dans l’ordre de leur exécution, le dernier test cité étant celui qui était en cours d’exécution au moment du plantage. Cette sortie permet d’isoler le test incriminé et d’établir un diagnostic plus facilement. [Plus d’informations](https://github.com/Microsoft/vstest-docs/blob/master/docs/extensions/blame-datacollector.md).|
|**/Diag:[*nom de fichier*]**|Écrit les journaux de trace de diagnostic dans le fichier spécifié.|
|**/ResultsDirectory:[*chemin*]**|Un répertoire de résultats de test sera créé dans le chemin d’accès spécifié s’il n’en existe pas.<br />Exemple : `/ResultsDirectory:<pathToResultsDirectory>`|
|**/ParentProcessId:[*ID_processus_parent*]**|ID du processus parent chargé de lancer le processus actif.|
|**/Port:[*port*]**|Port de connexion de socket et de réception des messages d’événement.|
|**/Collect:[*nom_convivial collecteur_de_données*]**|Active le collecteur de données pour la série de tests. [Plus d’informations](https://aka.ms/vstest-collect).|

> [!TIP]
> Les options et les valeurs ne respectent pas la casse.

## <a name="examples"></a>Exemples

La syntaxe pour exécuter *VSTest.Console.exe* est la suivante :

`Vstest.console.exe [TestFileNames] [Options]`

La commande suivante exécute *VSTest.Console.exe* pour la bibliothèque de tests **myTestProject.dll** :

```cmd
vstest.console.exe myTestProject.dll
```

La commande suivante exécute *VSTest.Console.exe* avec plusieurs fichiers de test. Séparez les noms de fichiers de test par des espaces :

```cmd
Vstest.console.exe myTestFile.dll myOtherTestFile.dll
```

La commande suivante exécute *VSTest.Console.exe* avec plusieurs options. Elle exécute les tests du fichier *myTestFile.dll* dans un processus isolé et utilise des paramètres spécifiés dans le fichier *Local.RunSettings*. En outre, elle n’exécute que les tests marqués « Priority=1 » et journalise les résultats dans un fichier *.trx*.

```cmd
vstest.console.exe  myTestFile.dll /Settings:Local.RunSettings /InIsolation /TestCaseFilter:"Priority=1" /Logger:trx
```
