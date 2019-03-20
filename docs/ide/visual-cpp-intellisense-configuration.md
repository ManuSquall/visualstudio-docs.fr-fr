---
title: Configurer un projet C++ pour IntelliSense
ms.date: 10/08/2018
ms.topic: conceptual
author: mblome
ms.author: mblome
manager: wpickett
ms.workload:
- cplusplus
ms.openlocfilehash: aee7faef7b33c8dd87a056077991a915df9b64a0
ms.sourcegitcommit: 4d9c54f689416bf1dc4ace058919592482d02e36
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58194056"
---
# <a name="configure-a-c-project-for-intellisense"></a>Configurer un projet C++ pour IntelliSense

Dans certains cas, il vous faudra peut-être configurer manuellement votre projet C++ pour qu’IntelliSense fonctionne correctement. En ce qui concerne les projets MSBuild (basés sur des fichiers .vcxproj), vous pouvez ajuster les paramètres dans les propriétés du projet. Pour les autres projets, les paramètres sont modifiables dans le fichier CppProperties.json qui se trouve dans le répertoire racine du projet. Dans certains cas, vous devrez peut-être créer un fichier hint pour aider IntelliSense à comprendre les définitions de macros. L’environnement de développement intégré (IDE) Visual Studio permet d’identifier et de résoudre les problèmes d’IntelliSense.



## <a name="single-file-intellisense"></a>IntelliSense avec un fichier unique

Lorsque vous ouvrez un fichier qui ne fait pas partie d’un projet, Visual Studio assure une prise en charge IntelliSense, mais par défaut aucune ligne ondulée d’erreur ne s’affiche. Si le **Barre de navigation** indique *Fichiers divers*, cela explique probablement pourquoi le code incorrect n’est pas souligné, ou pourquoi aucune macro de préprocesseur n’est définie.

## <a name="check-the-error-list"></a>Consulter la Liste d’erreurs

Si le fichier n’est pas ouvert en mode fichier unique et qu’IntelliSense ne fonctionne pas correctement, la première chose à vérifier est la fenêtre Liste d’erreurs. Pour afficher toutes les erreurs IntelliSense relatives au fichier source actuel ainsi que tous les fichiers d’en-tête inclus, sélectionnez **Build + IntelliSense** dans la liste déroulante :

![IntelliSense VC++ dans la Liste d’erreurs](media/vcpp-intellisense-error-list.png)

IntelliSense produit au maximum 1 000 erreurs. S’il y a plus de 1 000 erreurs dans les fichiers d’en-tête inclus par un fichier source, ce dernier ne montre qu’une seule ligne ondulée au tout début du fichier source.

## <a name="ensure-include-paths-are-correct"></a>Vérifier que les chemins d’accès #include sont corrects

### <a name="msbuild-projects"></a>Projets MSBuild

Si vous exécutez vos builds en dehors de l’environnement IDE de Visual Studio, qu’ils réussissent, mais qu’IntelliSense est incorrect, il est possible que votre ligne de commande soit désynchronisée avec les paramètres de projet pour une ou plusieurs configurations. Cliquez avec le bouton droit sur le nœud du projet dans **l’Explorateur de solutions** et vérifiez que tous les chemins d’accès **#include** sont corrects pour la configuration et la plateforme actuelles. Si les chemins d’accès sont identiques dans toutes les plateformes et toutes les configurations, vous pouvez sélectionner **Toutes les configurations** et **Toutes les plateformes**, puis vérifier qu’ils sont corrects.

![Répertoires Include VC++](media/vcpp-intellisense-include-paths.png)

 Pour voir les valeurs actuelles des macros de build comme **VC_IncludePath**, sélectionnez la ligne Répertoires Include, puis cliquez sur la liste déroulante à droite. Ensuite, sélectionnez **\<Modifier>**, puis cliquez sur le bouton **Macros**.

### <a name="makefile-projects"></a>projets Makefile

Dans le cas des projets Makefile qui reposent sur le modèle de projet NMake, sélectionnez **NMake** dans le volet gauche, puis **Chemin de recherche Include** sous la catégorie **IntelliSense** :

![Chemins Include du projet Makefile](media/vcpp-intellisense-makefile-include-paths.png)

Pour plus d'informations, voir [Procédure : Activer IntelliSense pour des projets Makefile](/cpp/ide/how-to-enable-intellisense-for-makefile-projects).

### <a name="open-folder-projects"></a>Projets Ouvrir un dossier

Dans le cas des projets CMake, vérifiez que les chemins d’accès #include sont spécifiés correctement pour toutes les configurations dans CMakeLists.txt. Un fichier CppProperties.json peut être requis dans d’autres types de projets. Pour plus d’informations, voir [Configurer IntelliSense avec CppProperties.json](/cpp/build/open-folder-projects-cpp#configure-intellisense-and-browsing-hints-with-cpppropertiesjson). Vérifiez que les chemins d’accès sont corrects pour chaque configuration définie dans le fichier.

S’il y a une erreur de syntaxe dans le fichier CppProperties.json, IntelliSense sera incorrect dans les fichiers affectés. Visual Studio affichera l’erreur dans la Fenêtre Sortie.

## <a name="tag-parser-issues"></a>Problèmes d’analyseur de balises

L’analyseur de balises est un analyseur C++ « approximatif » utilisé pour la navigation. Il est très rapide mais n’essaie pas de comprendre pleinement les différentes constructions de code.

Par exemple, il n’évalue pas les macros de préprocesseur, et risque par conséquent d’analyser incorrectement du code qui en ferait un usage intensif. Lorsque l’Analyseur de balises rencontre une construction de code inconnue, il peut ignorer la totalité de cette région de code.

Ce problème se manifeste principalement de deux manières dans Visual Studio :

1. Si la barre de navigation montre une macro plus intérieure, la définition de fonction en cours est ignorée :

   ![L’analyseur de balises ignore la définition de fonction](media/vcpp-intellisense-tag-parser-macro.png)

1. L’environnement IDE propose de créer une définition de fonction pour une fonction déjà définie :

   ![L’analyseur de balises propose de définir une fonction existante](media/vcpp-intellisense-tag-parser-function.png)

Pour résoudre ces types de problèmes, ajoutez un fichier nommé **cpp.hint** à la racine du répertoire de votre solution. Pour plus d’informations, voir [Fichiers hint](/cpp/build/reference/hint-files).

Les erreurs de l’analyseur de balises s’affichent dans la fenêtre **Liste d’erreurs**.

## <a name="validate-project-settings-with-diagnostic-logging"></a>Valider les paramètres du projet avec la journalisation des diagnostics

Pour vérifier que le compilateur IntelliSense utilise les bonnes options, chemins d’accès Include et macros de préprocesseur compris, activez la journalisation des diagnostics des lignes de commande IntelliSense dans **Outils > Options > Éditeur de texte > C/C++ > Avancé > Journalisation des diagnostics**. Définissez **Activer la journalisation** sur True, **Niveau de journalisation** sur 5 (le plus détaillé), et **Filtre de journalisation** sur 8 (journalisation IntelliSense).

La Fenêtre Sortie affiche maintenant les lignes de commande transmises au compilateur IntelliSense. Voici un exemple de sortie :

```output
 [IntelliSense] Configuration Name: Debug|Win32
 [IntelliSense] Toolset IntelliSense Identifier:
 [IntelliSense] command line options:
 /c
 /I.
 /IC:\Repo\Includes
 /DWIN32
 /DDEBUG
 /D_DEBUG
 /Zc:wchar_t-
 /Zc:forScope
 /Yustdafx.h
```

Ces informations peuvent vous aider à comprendre pourquoi IntelliSense fournit des informations inexactes. Par exemple, si le répertoire Include de votre projet contient **$(MaVariable) \Include** et que le journal de diagnostic présente **/I\Include** comme un chemin d’accès Include, cela signifie que **$(MaVariable)** n’a pas été évaluée et a été retirée du chemin d’accès Include final.

## <a name="about-the-intellisense-build"></a>À propos du build IntelliSense

Visual Studio utilise un compilateur C++ dédié pour créer et gérer la base de données qui alimente toutes les fonctionnalités IntelliSense. Pour préserver la synchronisation entre la base de données IntelliSense et le code, Visual Studio lance automatiquement en tâche de fond des builds IntelliSense seul en réponse à certaines modifications apportées aux paramètres du projet ou aux fichiers sources.

Dans certains cas toutefois, Visual Studio ne met pas à jour la base de données IntelliSense en temps voulu. Par exemple, lorsque vous exécutez une commande **git pull** ou **git checkout**, Visual Studio peut mettre une heure à détecter les modifications dans les fichiers. Vous pouvez forcer une nouvelle analyse de l’ensemble des fichiers dans une solution en cliquant avec le bouton droit sur le nœud du projet dans **l’Explorateur de solutions** et en sélectionnant **Relancer l’analyse de la solution**.

## <a name="troubleshooting-intellisense-build-failures"></a>Résoudre les échecs des builds IntelliSense

Même s’il ne génère pas de binaires, un build IntelliSense peut échouer. L’une des causes d’échec possibles est la présence de fichiers .props ou .targets personnalisés. Dans Visual Studio 2017 versions 15.6 et ultérieures, les erreurs de build liées uniquement à IntelliSense sont journalisées dans la fenêtre Sortie. Pour les afficher, définissez **Afficher la sortie de** sur **Solution** :

![Fenêtre Sortie pour les erreurs de la solution](media/vcpp-intellisense-output-window.png)

Le message d’erreur peut vous demander d’activer le traçage au moment du design :

```output
 error: Designtime build failed for project 'E:\src\MyProject\MyProject.vcxproj',
 configuration 'Debug|x64'. IntelliSense might be unavailable.
 Set environment variable TRACEDESIGNTIME=true and restart
 Visual Studio to investigate.
```

Si vous définissez la variable d’environnement TRACEDESIGNTIME sur true et redémarrez Visual Studio, un fichier journal apparaîtra dans le répertoire %TEMP%. Il pourra vous aider à diagnostiquer l’échec du build.

Pour plus d’informations sur la variable d’environnement TRACEDESIGNTIME, voir [Roslyn](https://github.com/dotnet/roslyn/wiki/Diagnosing-Project-System-Build-Errors) et [Système de projet commun](https://github.com/dotnet/project-system/blob/master/docs/design-time-builds.md). Les informations contenues dans ces articles s’appliquent aux projets C++.

## <a name="see-also"></a>Voir aussi

- [Visual C++ IntelliSense](visual-cpp-intellisense.md)
