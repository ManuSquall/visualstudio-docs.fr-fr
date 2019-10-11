---
title: Utilisation des vérificateurs C++ Core Guidelines
ms.date: 08/14/2018
ms.topic: conceptual
author: mikeblome
ms.author: mblome
manager: markl
dev_langs:
- CPP
ms.openlocfilehash: 57c8d6daf75987bfb5c6a6642b89f198693a5dce
ms.sourcegitcommit: 535ef05b1e553f0fc66082cd2e0998817eb2a56a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72018414"
---
# <a name="use-the-c-core-guidelines-checkers"></a>Utiliser les vérificateurs de C++ Core Guidelines

Les C++ directives principales sont un ensemble portable d’instructions, de règles et de meilleures pratiques concernant le C++ codage créé C++ par des experts et des concepteurs. Visual Studio prend actuellement en charge un sous-ensemble de ces règles dans le cadre de C++ses outils d’analyse du code pour. Les contrôleurs d’instructions de base sont installés par défaut dans Visual Studio 2017 et Visual Studio 2019, et sont [disponibles en tant que package NuGet pour Visual studio 2015](#vs2015_corecheck).

## <a name="the-c-core-guidelines-project"></a>Le C++ projet de recommandations principales

Créé par Bjarne Stroustrup et d’autres, C++ les recommandations de base sont un guide d' C++ utilisation de la sécurité moderne et efficace. Les directives insistent sur la sécurité des types statiques et la sécurité des ressources. Ils identifient les moyens d’éliminer ou de réduire les parties les plus sujettes aux erreurs du langage, et de vous suggérer comment rendre votre code plus simple et plus performant de manière fiable. Ces recommandations sont gérées par la C++ base standard. Pour en savoir plus, consultez la documentation, C++ [ C++ les instructions principales](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines)et accédez aux fichiers de projet de base de documentation sur [GitHub](https://github.com/isocpp/CppCoreGuidelines).

## <a name="enable-the-c-core-check-guidelines-in-code-analysis"></a>Activer les C++ instructions de contrôle de base dans l’analyse du code
Vous pouvez activer l’analyse du code sur votre projet en activant la case à cocher **activer l’analyse du code sur la build** dans la section **analyse du code** de la boîte de dialogue **pages de propriétés** de votre projet.

![Page de propriétés pour les paramètres généraux de l’analyse du code](media/cppcorecheck_codeanalysis_general.png)

Un sous- C++ ensemble de règles de contrôle de base est inclus dans l’ensemble de règles Microsoft Native Recommended qui s’exécute par défaut lorsque l’analyse du code est activée. Pour activer des règles de vérification de noyau supplémentaires, cliquez sur la liste déroulante et choisissez les ensembles de règles que vous souhaitez inclure :

![Liste déroulante pour les ensembles de règles de vérification de noyau supplémentaires C++](media/cppcorecheck_codeanalysis_extensions.png)

## <a name="examples"></a>Exemples
Voici un exemple de certains des problèmes que les C++ règles de contrôle de base peuvent trouver :

```cpp
// CoreCheckExample.cpp
// Add CppCoreCheck package and enable code analysis in build for warnings.

int main()
{
    int arr[10];           // warning C26494
    int* p = arr;          // warning C26485

    [[gsl::suppress(bounds.1)]] // This attribute suppresses Bounds rule #1
    {
        int* q = p + 1;    // warning C26481 (suppressed)
        p = q++;           // warning C26481 (suppressed)
    }

    return 0;
}
```

Cet exemple illustre quelques-uns des avertissements que les C++ règles de contrôle de base peuvent trouver :

- C26494 est de type règle. 5 : Initialisez toujours un objet.

- C26485 est une limite de règle. 3 : Aucune atténuation de tableau à pointeur.

- C26481 est une limite de règle. 1 : N’utilisez pas opérations arithmétiques de pointeur. Utilisez plutôt `span`.

Si les C++ ensembles de règles d’analyse du code de contrôle de base sont installés et activés lorsque vous compilez ce code, les deux premiers avertissements sont générés, mais le troisième est supprimé. Voici la sortie de la génération de l’exemple de code :

```Output
1>------ Build started: Project: CoreCheckExample, Configuration: Debug Win32 ------
1>  CoreCheckExample.cpp
1>  CoreCheckExample.vcxproj -> C:\Users\username\documents\visual studio 2015\Projects\CoreCheckExample\Debug\CoreCheckExample.exe
1>  CoreCheckExample.vcxproj -> C:\Users\username\documents\visual studio 2015\Projects\CoreCheckExample\Debug\CoreCheckExample.pdb (Full PDB)
c:\users\username\documents\visual studio 2015\projects\corecheckexample\corecheckexample\corecheckexample.cpp(6): warning C26494: Variable 'arr' is uninitialized. Always initialize an object. (type.5: http://go.microsoft.com/fwlink/p/?LinkID=620421)
c:\users\username\documents\visual studio 2015\projects\corecheckexample\corecheckexample\corecheckexample.cpp(7): warning C26485: Expression 'arr': No array to pointer decay. (bounds.3: http://go.microsoft.com/fwlink/p/?LinkID=620415)
========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========
```

Les C++ recommandations de base sont là pour vous aider à écrire du code plus sécurisé. Toutefois, si vous avez une instance dans laquelle une règle ou un profil ne doit pas être appliqué, il est facile de la supprimer directement dans le code. Vous pouvez utiliser l’attribut `gsl::suppress` pour garantir C++ une vérification de base de la détection et du signalement d’une violation d’une règle dans le bloc de code suivant. Vous pouvez marquer des instructions individuelles pour supprimer des règles spécifiques. Vous pouvez même supprimer le profil de limites entier en écrivant `[[gsl::suppress(bounds)]]` sans inclure un numéro de règle spécifique.

## <a name="supported-rule-sets"></a>Ensembles de règles pris en charge
À mesure que de nouvelles règles sont C++ ajoutées à l’outil de vérification des instructions de base, le nombre d’avertissements générés pour le code préexistant peut augmenter. Vous pouvez utiliser des ensembles de règles prédéfinis pour filtrer les genres de règles à activer.
Les rubriques de référence pour la plupart des règles sont sous [référence de vérification principale de Visual C++ Studio](code-analysis-for-cpp-corecheck.md).

À compter de Visual Studio 2017 version 15,3, les ensembles de règles pris en charge sont les suivants :
- Les **règles du pointeur propriétaire** appliquent [les vérifications de gestion des ressources liées à owner @ no__t C++ -2T > dans les instructions de base](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management).

- Les **règles const** appliquent [ C++ les vérifications liées à const à partir des instructions de base](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con-constants-and-immutability).

- Les **règles de pointeur brut** appliquent [ C++ les vérifications de gestion des ressources liées aux pointeurs bruts à partir des recommandations principales](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management).

- Les **règles de pointeur uniques** appliquent [les C++ vérifications de gestion des ressources liées aux types avec une sémantique de pointeur unique à partir des instructions de base](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management).

- Les **règles de limites** appliquent le [profil de limites C++ des recommandations principales](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#probounds-bounds-safety-profile).

- Les **règles de type** appliquent le [profil C++ de type des recommandations principales](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#prosafety-type-safety-profile).

**Visual Studio 2017 version 15.5** :

- **Règles de classe** Quelques règles qui se concentrent sur l’utilisation correcte des fonctions membres spéciales et des spécifications virtuelles. Il s’agit d’un sous-ensemble de vérifications recommandé pour les [classes et les hiérarchies](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-class)de classes.
- **Règles d’accès concurrentiel** Une seule règle, qui intercepte les objets Guard mal déclarés. Pour plus d’informations, consultez [instructions relatives à l’accès concurrentiel](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-concurrency).
- **Règles de déclaration** Quelques règles des instructions de l' [interface](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-interfaces) qui se concentrent sur la façon dont les variables globales sont déclarées.
- **Règles de fonction** Deux contrôles qui permettent d’adopter le spécificateur `noexcept`. Cela fait partie des indications relatives à la [conception et](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-functions)à l’implémentation de la fonction Clear.
- **Règles de pointeur partagé** Dans le cadre de l’application des règles de [gestion des ressources](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-resource) , nous avons ajouté quelques règles spécifiques à la façon dont les pointeurs partagés sont passés dans des fonctions ou utilisés localement.
- **Règles de style** Un contrôle simple mais important, qui interdit l’utilisation de [goto](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Res-goto). Il s’agit de la première étape d’amélioration du style de codage et de l’utilisation C++des expressions et des instructions dans.

**Visual Studio 2017 version 15.6** :

- **Règles arithmétiques** Règles de détection des [dépassements](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Res-overflow) arithmétiques, des [opérations non signées](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Res-unsigned) et des [manipulations de bits](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Res-nonnegative).

Vous pouvez choisir de limiter les avertissements à un seul ou à quelques groupes. Les ensembles de règles natifs **minimum** et **natif recommandés** incluent C++ des règles de contrôle de base en plus d’autres vérifications prérapides. Pour afficher les ensembles de règles disponibles, ouvrez la boîte de dialogue Propriétés du projet, sélectionnez **code Analysis\General**, ouvrez la zone de liste déroulante **ensembles de règles** , puis **Choisissez plusieurs ensembles de règles**. Pour plus d’informations sur l’utilisation d’ensembles de règles dans Visual Studio, consultez [utilisation d’ensembles de règles pour regrouper des règles d’analyse du code](using-rule-sets-to-group-code-analysis-rules.md).

## <a name="macros"></a>Macros

Le C++ vérificateur des instructions de base est fourni avec un fichier d’en-tête, qui définit des macros qui facilitent la suppression des catégories entières d’avertissements dans le code :

```cpp
ALL_CPPCORECHECK_WARNINGS
CPPCORECHECK_TYPE_WARNINGS
CPPCORECHECK_RAW_POINTER_WARNINGS
CPPCORECHECK_CONST_WARNINGS
CPPCORECHECK_OWNER_POINTER_WARNINGS
CPPCORECHECK_UNIQUE_POINTER_WARNINGS
CPPCORECHECK_BOUNDS_WARNINGS
```

Ces macros correspondent aux ensembles de règles et se développent en une liste de numéros d’avertissement séparés par des espaces. En utilisant les constructions de pragma appropriées, vous pouvez configurer l’ensemble de règles effectif qui est intéressant pour un projet ou une section de code. Dans l’exemple suivant, l’analyse du code n’avertit que les modificateurs de constante manquants :

```cpp
#include <CppCoreCheck\Warnings.h>
#pragma warning(disable: ALL_CPPCORECHECK_WARNINGS)
#pragma warning(default: CPPCORECHECK_CONST_WARNINGS)
```

## <a name="attributes"></a>Attributs

Le compilateur Microsoft C++ Visual a une prise en charge limitée de l’attribut de suppression GSL. Il peut être utilisé pour supprimer des avertissements sur les instructions d’expression et de bloc dans une fonction.

```cpp
// Suppress only warnings from the 'r.11' rule in expression.
[[gsl::suppress(r.11)]] new int;

// Suppress all warnings from the 'r' rule group (resource management) in block.
[[gsl::suppress(r)]]
{
    new int;
}

// Suppress only one specific warning number.
// For declarations, you may need to use the surrounding block.
// Macros are not expanded inside of attributes.
// Use plain numbers instead of macros from the warnings.h.
[[gsl::suppress(26400)]]
{
    int *p = new int;
}
```

## <a name="suppress-analysis-by-using-command-line-options"></a>Supprimer l’analyse à l’aide des options de ligne de commande

Au lieu de #pragmas, vous pouvez utiliser les options de ligne de commande dans la page de propriétés du fichier pour supprimer les avertissements d’un projet ou d’un fichier unique. Par exemple, pour désactiver l’avertissement 26400 pour un fichier :

1. Cliquez avec le bouton droit sur le fichier dans **Explorateur de solutions**

2. Choisir les **Propriétés | C/C++| Ligne de commande**

3. Dans la fenêtre **options supplémentaires** , ajoutez `/wd26400`.

Vous pouvez utiliser l’option de ligne de commande pour désactiver temporairement l’ensemble de l’analyse du code pour un fichier en spécifiant `/analyze-`. Cela génère un avertissement *D9025 remplaçant'/Analyze’par'/Analyze-'* , ce qui vous rappelle de réactiver l’analyse du code ultérieurement.

## <a name="corecheck_per_file"></a>Activer le C++ vérificateur des instructions de base sur des fichiers de projet spécifiques

Parfois, il peut être utile d’effectuer une analyse du code ciblé tout en continuant à utiliser l’IDE de Visual Studio. L’exemple de scénario suivant peut être utilisé pour des projets volumineux afin d’économiser du temps de génération et de faciliter le filtrage des résultats :

1. Dans l’interface de commande, définissez les variables d’environnement `esp.extension` et `esp.annotationbuildlevel`.
2. Pour hériter de ces variables, ouvrez Visual Studio à partir de l’interface de commande.
3. Chargez votre projet et ouvrez ses propriétés.
4. Activez l’analyse du code, choisissez les ensembles de règles appropriés, mais n’activez pas les extensions d’analyse du code.
5. Accédez au fichier que vous souhaitez analyser à l’aide C++ de l’outil de vérification des instructions de base et ouvrez ses propriétés.
6. Choisissez les **optionsC++de ligne C/\Command** et ajoutez `/analyze:plugin EspXEngine.dll`
7. Désactivez l’utilisation de l’en-tête précompilé (**en-têtes CC++/\Precompiled**). Cela est nécessaire, car le moteur d’extensions peut tenter de lire ses informations internes à partir de l’en-tête précompilé (PCH). Si le PCH compilé avec les options de projet par défaut, il ne sera pas compatible.
8. Regénérez le projet. Les vérifications prérapides courantes doivent s’exécuter sur tous les fichiers. Étant donné C++ que le vérificateur des instructions de base n’est pas activé par défaut, il ne doit s’exécuter que sur le fichier configuré pour l’utiliser.

## <a name="how-to-use-the-c-core-guidelines-checker-outside-of-visual-studio"></a>Comment utiliser le C++ vérificateur des instructions de base en dehors de Visual Studio

Vous pouvez utiliser les C++ contrôles des instructions principales dans les builds automatisées.

### <a name="msbuild"></a>MSBuild
L’outil d’analyse du code natif (PREfast) est intégré à l’environnement MSBuild par les fichiers de cibles personnalisés. Vous pouvez utiliser les propriétés du projet pour l’activer et ajouter C++ le vérificateur des instructions de base (qui est basé sur PREfast) :

```xml
  <PropertyGroup>
    <EnableCppCoreCheck>true</EnableCppCoreCheck>
    <CodeAnalysisRuleSet>CppCoreCheckRules.ruleset</CodeAnalysisRuleSet>¬¬
    <RunCodeAnalysis>true</RunCodeAnalysis>
  </PropertyGroup>
```

Veillez à ajouter ces propriétés avant d’importer le fichier Microsoft. cpp. targets. Vous pouvez choisir des ensembles de règles spécifiques ou créer un ensemble de règles personnalisé ou utiliser l’ensemble de règles par défaut qui comprend d’autres vérifications PREfast.

Vous pouvez exécuter l' C++ outil de vérification de base uniquement sur les fichiers spécifiés à l’aide de la même approche que celle [décrite précédemment](#corecheck_per_file), mais en utilisant des fichiers MSBuild. Les variables d’environnement peuvent être définies à l’aide de l’élément `BuildMacro` :

```xml
<ItemGroup>
    <BuildMacro Include="Esp_AnnotationBuildLevel">
      <EnvironmentVariable>true</EnvironmentVariable>
      <Value>Ignore</Value>
    </BuildMacro>
    <BuildMacro Include="Esp_Extensions">
      <EnvironmentVariable>true</EnvironmentVariable>
      <Value>CppCoreCheck.dll</Value>
    </BuildMacro>
</ItemGroup>
```

Si vous ne souhaitez pas modifier le fichier projet, vous pouvez passer des propriétés sur la ligne de commande :

```cmd
msbuild /p:EnableCppCoreCheck=true /p:RunCodeAnalysis=true /p:CodeAnalysisRuleSet=CppCoreCheckRules.ruleset ...
```

### <a name="non-msbuild-projects"></a>Projets non-MSBuild

Si vous utilisez un système de génération qui ne repose pas sur MSBuild, vous pouvez toujours exécuter l’outil de vérification, mais vous devez vous familiariser avec certains éléments internes de la configuration du moteur d’analyse du code. Il n’est pas garanti que ces éléments internes soient pris en charge à l’avenir.

Vous devez définir certaines variables d’environnement et utiliser les options de ligne de commande appropriées pour le compilateur. Il est préférable de travailler dans l’environnement « invite de commandes des outils natifs » afin de ne pas avoir à rechercher des chemins spécifiques pour le compilateur, les répertoires Include, etc.

1. **Variables d’environnement**
   - `set esp.extensions=cppcorecheck.dll` indique au moteur de charger le C++ module instructions principales.
   - `set esp.annotationbuildlevel=ignore` désactive la logique qui traite les annotations SAL. Les annotations n’affectent pas l' C++ analyse du code dans le vérificateur des instructions de base, mais leur traitement prend du temps (parfois à long terme). Ce paramètre est facultatif, mais fortement recommandé.
   - `set caexcludepath=%include%`, nous vous recommandons vivement de désactiver les avertissements qui se déclenchent sur les en-têtes standard. Vous pouvez ajouter d’autres chemins ici, par exemple, le chemin d’accès aux en-têtes courants dans votre projet.
2. **Options de ligne de commande**
   - `/analyze` active l’analyse du code (envisagez également d’utiliser/Analyze : uniquement et/Analyze : quiet).
   - `/analyze:plugin EspXEngine.dll` cette option charge le moteur d’extensions d’analyse du code dans le préfast. Ce moteur charge, à son tour, C++ le vérificateur des instructions de base.

## <a name="use-the-guideline-support-library"></a>Utiliser la bibliothèque de prise en charge des instructions
La bibliothèque de prise en charge des instructions est conçue pour vous aider à suivre les instructions principales. Le portail GSL comprend des définitions qui vous permettent de remplacer des constructions sujettes aux erreurs par des alternatives plus sûres. Par exemple, vous pouvez remplacer une paire `T*, length` de paramètres par le type `span<T>`. Le portail GSL est disponible au [http://www.nuget.org/packages/Microsoft.Gsl](http://www.nuget.org/packages/Microsoft.Gsl). La bibliothèque étant Open source, vous pouvez afficher les sources, créer des commentaires ou contribuer. Le projet se trouve à l’adresse [https://github.com/Microsoft/GSL](https://github.com/Microsoft/GSL).

## <a name="vs2015_corecheck"></a>Utiliser les C++ instructions de contrôle de base dans les projets Visual Studio 2015

Si vous utilisez Visual Studio 2015, les C++ ensembles de règles d’analyse du code de contrôle de base ne sont pas installés par défaut. Vous devez effectuer quelques étapes supplémentaires avant de pouvoir activer les C++ outils d’analyse du code de vérification de base dans Visual Studio 2015. Microsoft fournit une prise en charge pour les projets Visual Studio 2015 à l’aide d’un package NuGet. Le package est nommé Microsoft. CppCoreCheck et est disponible sur [http://www.nuget.org/packages/Microsoft.CppCoreCheck](http://www.nuget.org/packages/Microsoft.CppCoreCheck). Pour ce package, vous devez avoir au moins Visual Studio 2015 avec la mise à jour 1 installée.

Le package installe également un autre package en tant que dépendance, une bibliothèque de prise en charge des instructions en en-tête uniquement (GSL). Le portail GSL est également disponible sur GitHub au [https://github.com/Microsoft/GSL](https://github.com/Microsoft/GSL).

En raison du mode de chargement des règles d’analyse du code, vous devez installer le package NuGet Microsoft. CppCoreCheck C++ dans chaque projet que vous souhaitez vérifier dans Visual Studio 2015.

### <a name="to-add-the-microsoftcppcorecheck-package-to-your-project-in-visual-studio-2015"></a>Pour ajouter le package Microsoft. CppCoreCheck à votre projet dans Visual Studio 2015

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit pour ouvrir le menu contextuel de votre projet dans la solution à laquelle vous souhaitez ajouter le package. Sélectionnez **gérer les packages NuGet** pour ouvrir le **Gestionnaire de package NuGet**.

2. Dans la fenêtre **Gestionnaire de package NuGet** , recherchez Microsoft. CppCoreCheck.

    ![La fenêtre du gestionnaire de package NuGet affiche le package CppCoreCheck](../code-quality/media/cppcorecheck_nuget_window.png)

3. Sélectionnez le package Microsoft. CppCoreCheck, puis cliquez sur le bouton **installer** pour ajouter les règles à votre projet.

   Le package NuGet ajoute un fichier MSBuild *. targets* supplémentaire à votre projet qui est appelé lorsque vous activez l’analyse du code sur votre projet. Ce fichier *. targets* ajoute C++ les règles de contrôle de base en tant qu’extension supplémentaire à l’outil d’analyse du code Visual Studio. Lorsque le package est installé, vous pouvez utiliser la boîte de dialogue pages de propriétés pour activer ou désactiver les règles de publication et expérimentale.

## <a name="see-also"></a>Voir aussi

- [Référence de C++ la vérification principale de Visual Studio](code-analysis-for-cpp-corecheck.md)