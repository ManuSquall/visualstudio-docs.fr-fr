---
title: Options de ligne de commande VSTest.Console.exe
description: En savoir plus sur l’outil en ligne de commande VSTest.Console.exe qui exécute les tests. Cet article comprend les options de ligne de commande générales.
ms.custom: SEO-VS-2020
ms.date: 07/17/2020
ms.topic: reference
helpviewer_keywords:
- vstest.console.exe
- command-line tests
ms.author: mikejo
author: mikejo5000
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6256343efbc9b81c14b03753fab2fa478df1e4f5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99946187"
---
# <a name="vstestconsoleexe-command-line-options"></a>Options de ligne de commande VSTest.Console.exe

*VSTest.Console.exe* est l’outil en ligne de commande pour exécuter des tests. Vous pouvez spécifier plusieurs options dans un ordre quelconque dans la ligne de commande. Ces options sont répertoriées dans [Options de ligne de commande générales](#general-command-line-options).

> [!NOTE]
> L’adaptateur MSTest de Visual Studio fonctionne également en mode hérité (équivalent de l’exécution de tests avec *mstest.exe*) pour la compatibilité. En mode hérité, il ne peut pas tirer parti de la fonctionnalité TestCaseFilter. L’adaptateur peut basculer en mode hérité quand un fichier *testsettings* est spécifié, que **forcelegacymode** a la valeur **true** dans un fichier *runsettings*, ou à l’aide d’attributs comme **HostType**.
>
> Pour exécuter des tests automatisés sur un ordinateur basé sur une architecture ARM, vous devez utiliser *VSTest.Console.exe*.

Ouvrez une [invite de commandes développeur](/dotnet/framework/tools/developer-command-prompt-for-vs) pour utiliser l’outil en ligne de commande, ou vous pouvez trouver l’outil dans *% Program Files (x86)% \ Microsoft Visual Studio \\<version \> \\<Edition \> \common7\ide\CommonExtensions \\<plateforme |>Microsoft*.

## <a name="general-command-line-options"></a>Options de ligne de commande générales

Le tableau suivant répertorie toutes les options de *VSTest.Console.exe*, ainsi que leurs brèves descriptions. Vous pouvez voir un résumé semblable en tapant `VSTest.Console/?` sur une ligne de commande.

| Option | Description |
|---|---|
|**[*noms de fichiers de test*]**|Exécutez les tests à partir des fichiers spécifiés. Séparez les noms de fichiers de test par des espaces.<br />Exemples : `mytestproject.dll`, `mytestproject.dll myothertestproject.exe`|
|**/Settings:[*nom de fichier*]**|Exécutez les tests avec d'autres paramètres tels que les collecteurs de données. Pour plus d’informations, consultez [configurer des tests unitaires à l’aide d’un fichier. RunSettings](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)<br />Exemple : `/Settings:local.runsettings`|
|**/Tests:[*nom du test*]**|Exécutez les tests avec les noms qui contiennent les valeurs fournies. Pour fournir plusieurs valeurs, séparez-les par des virgules.<br />Exemple : `/Tests:TestMethod1,testMethod2`<br />L’option de ligne de commande **/Tests** ne peut pas être utilisée avec l’option de ligne de commande **/TestCaseFilter**.|
|**/Parallel**|Spécifie que les tests doivent être exécutés en parallèle. Par défaut, tout ou partie des cœurs disponibles sur la machine peuvent être utilisés. Vous pouvez configurer le nombre de cœurs à utiliser dans un fichier de paramètres.|
|**/Enablecodecoverage**|Active l'adaptateur de données de diagnostic CodeCoverage dans la série de tests.<br />Les paramètres par défaut sont utilisés s'ils ne sont pas spécifiés à l'aide du fichier de paramètres.|
|**/InIsolation**|Exécute les tests dans un processus isolé.<br />En raison de cette isolation, il est moins probable que le processus *vstest.console.exe* soit arrêté sur une erreur dans les tests, mais les tests peuvent s’exécuter plus lentement.|
|**/UseVsixExtensions**|Grâce à cette option, le processus *vstest.console.exe* utilise ou ignore les extensions VSIX installées (le cas échéant) dans la série de tests.<br />Cette fonction est déconseillée. À compter de la prochaine version majeure de Visual Studio, cette option peut être supprimée. Envisagez d’utiliser des extensions disponibles en tant que package NuGet.<br />Exemple : `/UseVsixExtensions:true`|
|**/TestAdapterPath:[*chemin*]**|Force le processus *vstest.console.exe* à utiliser des adaptateurs de test personnalisés à partir d’un chemin spécifié (le cas échéant) dans la série de tests.<br />Exemple : `/TestAdapterPath:[pathToCustomAdapters]`|
|**/Platform:[*type de plateforme*]**|Force l’utilisation de la plateforme donnée à la place de la plateforme déterminée à partir du runtime actuel. Cette option est en mesure de forcer uniquement les plateformes x86 et x64 sur Windows. L’option ARM est rompue et se traduit par x64 sur la plupart des systèmes.<br />Ne spécifiez pas cette option à exécuter sur les runtimes qui ne figurent pas dans la liste des valeurs valides telles que ARM64.<br />Les valeurs valides sont x86, x64 et ARM.<br /> 
|**/Framework: [*version de .Net Framework*]**|Version de .NET cible à utiliser pour l’exécution des tests.<br />Les valeurs possibles sont `Framework35`, `Framework40`, `Framework45`, `FrameworkUap10` et `.NETCoreApp,Version=v1.1`.<br />TargetFrameworkAttribute est utilisé pour détecter automatiquement cette option à partir de votre assembly, et prend la valeur par défaut `Framework40` lorsque l’attribut n’est pas présent. Vous devez spécifier cette option explicitement si vous supprimez le [TargetFrameworkAttribute](/dotnet/api/system.runtime.versioning.targetframeworkattribute) de vos assemblys .net core.<br />Si la version cible du .NET Framework est spécifiée en tant que **Framework35**, les tests s’exécutent en mode de compatibilité CLR 4,0.<br />Exemple : `/Framework:framework40`|
|**/TestCaseFilter:[*expression*]**|Exécutez les tests qui correspondent à l'expression donnée.<br /><Expression\> est au format <propriété\>=<valeur\>[\|<Expression\>].<br />Exemple : `/TestCaseFilter:"Priority=1"`<br />Exemple : `/TestCaseFilter:"TestCategory=Nightly|FullyQualifiedName=Namespace.ClassName.MethodName"`<br />L’option de ligne de commande **/TestCaseFilter** ne peut pas être utilisée avec l’option de ligne de commande **/Tests**. <br />Pour plus d’informations sur la création et l’utilisation d’expressions, consultez [Filtre TestCase](https://github.com/Microsoft/vstest-docs/blob/master/docs/filter.md).|
|**/?**|Affiche des informations sur l’utilisation.|
|**/Logger:[*uri/nom_convivial*]**|Spécifiez un journal pour les résultats de tests. Spécifiez le paramètre plusieurs fois pour activer plusieurs enregistreurs d’événements.<br />Exemple : pour enregistrer les résultats dans un fichier de Résultats des tests Visual Studio (TRX), utilisez<br />**/Logger : trx**<br />**[; LogFileName = \<Defaults to unique file name> ]**|
|**/ListTests:[*nom de fichier*]**|Répertorie les tests détectés dans le conteneur de tests donné.|
|**/ListDiscoverers**|Répertorie les découvreurs de test installés.|
|**/ListExecutors**|Répertorie les exécuteurs de test installés.|
|**/ListLoggers**|Répertorie les journaux de test installés.|
|**/ListSettingsProviders**|Répertorie les fournisseurs de paramètres installés.|
|**/Blame**|Exécute les tests en mode responsable. Cette option est utile pour isoler les tests problématiques qui provoquent le blocage de l’hôte de test. Lorsqu’un incident est détecté, il crée un fichier de séquence dans `TestResults/<Guid>/<Guid>_Sequence.xml` qui capture l’ordre des tests qui ont été exécutés avant l’incident. Pour plus d’informations, consultez le [collecteur de données de responsabilité](https://github.com/Microsoft/vstest-docs/blob/master/docs/extensions/blame-datacollector.md).|
|**/Diag:[*nom de fichier*]**|Écrit les journaux de trace de diagnostic dans le fichier spécifié.|
|**/ResultsDirectory:[*chemin*]**|Un répertoire de résultats de test sera créé dans le chemin d’accès spécifié s’il n’en existe pas.<br />Exemple : `/ResultsDirectory:<pathToResultsDirectory>`|
|**/ParentProcessId:[*ID_processus_parent*]**|ID du processus parent chargé de lancer le processus actif.|
|**/Port:[*port*]**|Port de connexion de socket et de réception des messages d’événement.|
|**/Collect:[*nom_convivial collecteur_de_données*]**|Active le collecteur de données pour la série de tests. [Plus d’informations](https://github.com/Microsoft/vstest-docs/blob/master/docs/analyze.md).|

> [!TIP]
> Les options et les valeurs ne respectent pas la casse.

## <a name="examples"></a>Exemples

La syntaxe d’exécution de *vstest.console.exe* est la suivante :

`vstest.console.exe [TestFileNames] [Options]`

La commande suivante exécute *vstest.console.exe* pour la *myTestProject.dll* de la bibliothèque de tests :

```cmd
vstest.console.exe myTestProject.dll
```

La commande suivante exécute *vstest.console.exe* avec plusieurs fichiers de test. Séparez les noms de fichiers de test par des espaces :

```cmd
vstest.console.exe myTestFile.dll myOtherTestFile.dll
```

La commande suivante exécute *vstest.console.exe* avec plusieurs options. Elle exécute les tests du fichier *myTestFile.dll* dans un processus isolé et utilise des paramètres spécifiés dans le fichier *Local.RunSettings*. En outre, elle n’exécute que les tests marqués « Priority=1 » et journalise les résultats dans un fichier *.trx*.

```cmd
vstest.console.exe myTestFile.dll /Settings:Local.RunSettings /InIsolation /TestCaseFilter:"Priority=1" /Logger:trx
```

La commande suivante exécute *vstest.console.exe* avec l' `/blame` option pour la bibliothèque de tests *myTestProject.dll*:

```cmd
vstest.console.exe myTestFile.dll /blame
```

Si un incident de l’hôte de test s’est produit, le fichier *sequence.xml* est généré. Le fichier contient des noms complets des tests dans leur séquence d’exécution jusqu’au test spécifique qui était en cours d’exécution au moment de l’incident.

En l’absence d’incident de l’hôte de test, le fichier *sequence.xml* ne sera pas généré.

Exemple de fichier de *sequence.xml* généré : 

```xml
<?xml version="1.0"?>
<TestSequence>
  <Test Name="TestProject.UnitTest1.TestMethodB" Source="D:\repos\TestProject\TestProject\bin\Debug\TestProject.dll" />
  <Test Name="TestProject.UnitTest1.TestMethodA" Source="D:\repos\TestProject\TestProject\bin\Debug\TestProject.dll" />
</TestSequence>
```
