---
title: Avertissements de C++ Core Guidelines
ms.date: 08/10/2017
ms.topic: conceptual
ms.assetid: 7c83814a-f21d-4323-ad5f-13bac40d3e38
author: mblome
ms.author: mblome
manager: wpickett
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.workload:
- cplusplus
ms.openlocfilehash: 035f1fe305576eb7f5bf05fb6cc5f6343e256dca
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44279748"
---
# <a name="using-the-c-core-guidelines-checkers"></a>À l’aide des vérificateurs C++ Core Guidelines
Les recommandations C++ Core Guidelines sont un ensemble portable d’instructions, des règles et des meilleures pratiques sur le codage en C++ créé par les concepteurs et les experts de C++. Visual Studio prend actuellement en charge un sous-ensemble de ces règles dans le cadre de ses outils d’analyse de code C++. Les vérificateurs d’indication core sont installés par défaut dans Visual Studio 2017 et sont [disponible comme package NuGet pour Visual Studio 2015](#vs2015_corecheck).

## <a name="the-c-core-guidelines-project"></a>Les recommandations C++ Core Guidelines de projet
 Créé par Bjarne Stroustrup et d’autres, les recommandations C++ Core Guidelines sont un guide d’utilisation de C++ moderne efficacement et en toute sécurité. Les instructions de mettre l’accent sur la sécurité de type statique et sécurité des ressources. Ils identifient les moyens pour éliminer ou réduire les parties plus sujet aux erreurs de la langue et que vous suggèrent comment rendre votre code plus simple et plus performant de façon fiable. Ces instructions sont gérées par le Standard C++ Foundation. Pour plus d’informations, consultez la documentation, [C++ Core Guidelines](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines)et accéder aux fichiers de projet de documentation de C++ Core Guidelines sur [GitHub](https://github.com/isocpp/CppCoreGuidelines).

## <a name="enable-the-c-core-check-guidelines-in-code-analysis"></a>Activer les recommandations C++ Core Check dans l’analyse du Code
 Vous pouvez activer l’analyse du code sur votre projet en sélectionnant le **activer l’analyse du Code sur la Build** case à cocher dans la **analyse du Code** section de la **Pages de propriétés** boîte de dialogue pour votre projet.

 ![Page de propriétés de paramètres généraux d’analyse de Code](../code-quality/media/cppcorecheck_codeanalysis_general.png)

 Les règles C++ Core Check sont des extensions pour les ensembles de règles par défaut qui s’exécutent lors de l’analyse du code est activée. Étant donné que les règles C++ Core Check sont en cours de développement, certaines règles sont bien établies et certaines peuvent ne pas être prêt à être utilisé sur tout le code, mais il peuvent toujours être informatives. Les règles sont divisées en deux groupes : publiées et expérimentales. Vous pouvez choisir d’exécuter les règles a été résiliés ou expérimentales dans les propriétés de votre projet.

 ![Page de propriétés pour les paramètres des Extensions d’analyse de Code](../code-quality/media/cppcorecheck_codeanalysis_extensions.png)

 Pour activer ou désactiver les ensembles de règles C++ Core Check, ouvrez le **Pages de propriétés** boîte de dialogue pour votre projet. Sous **propriétés de Configuration**, développez **analyse du Code**, **Extensions**. Dans la liste déroulante contrôler regard **activer C++ Core Check (Released)** ou **activer C++ Core Check (expérimental)**, choisissez **Oui** ou **non**. Choisissez **OK** ou **appliquer** pour enregistrer vos modifications.

## <a name="examples"></a>Exemples
 Voici un exemple de certains des problèmes que les règles C++ Core Check trouverez :

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

 Cet exemple illustre quelques-unes des avertissements que les règles C++ Core Check trouverez :

-   C26494 est règle Type.5 : Initialisez toujours un objet.

-   C26485 est règle Bounds.3 : aucune perte de tableau en pointeur.

-   C26481 est règle Bounds.1 : ne pas utiliser l’opération arithmétique de pointeur. Utilisez plutôt `span`.

 Si les ensembles de règles C++ Core Check l’analyse de code sont installées et activées lorsque vous compilez ce code, les deux premiers avertissements sont générés, mais la troisième est supprimée. Voici la sortie de génération à partir de l’exemple de code :

```Output
1>------ Build started: Project: CoreCheckExample, Configuration: Debug Win32 ------
1>  CoreCheckExample.cpp
1>  CoreCheckExample.vcxproj -> C:\Users\username\documents\visual studio 2015\Projects\CoreCheckExample\Debug\CoreCheckExample.exe
1>  CoreCheckExample.vcxproj -> C:\Users\username\documents\visual studio 2015\Projects\CoreCheckExample\Debug\CoreCheckExample.pdb (Full PDB)
c:\users\username\documents\visual studio 2015\projects\corecheckexample\corecheckexample\corecheckexample.cpp(6): warning C26494: Variable 'arr' is uninitialized. Always initialize an object. (type.5: http://go.microsoft.com/fwlink/p/?LinkID=620421)
c:\users\username\documents\visual studio 2015\projects\corecheckexample\corecheckexample\corecheckexample.cpp(7): warning C26485: Expression 'arr': No array to pointer decay. (bounds.3: http://go.microsoft.com/fwlink/p/?LinkID=620415)
========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========
```

Les recommandations C++ Core Guidelines sont là pour vous aider à écrire du code de meilleure et plus sûr. Toutefois, si vous avez une instance où une règle ou un profil ne doit pas être appliqué, il est facile de supprimer directement dans le code. Vous pouvez utiliser le `gsl::suppress` attribut conserver C++ Core Check de détection et de signaler toute violation d’une règle dans le bloc de code suivant. Vous pouvez marquer les instructions individuelles pour supprimer des règles spécifiques. Vous pouvez même supprimer le profil bounds entière en écrivant `[[gsl::suppress(bounds)]]` sans inclure un numéro de règle spécifique.

## <a name="supported-rule-sets"></a>Prise en charge des ensembles de règles
Comme les nouvelles règles sont ajoutées pour le vérificateur de recommandations C++ Core, le nombre d’avertissements qui se sont produites pour code préexistant peut augmenter. Vous pouvez utiliser des ensembles de règles prédéfinies pour filtrer les types de règles à activer. À compter de Visual Studio 2017 version 15.3, les ensembles de règles pris en charge sont :
  - **Règles pour les pointeurs propriétaire** appliquer [vérifie de gestion des ressources liées à owner<T> à partir de C++ Core Guidelines](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management).

  - **Règles constantes** appliquer [les vérifications liées const à partir de C++ Core Guidelines](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con-constants-and-immutability).

  - **Règles pour les pointeurs bruts** appliquer [gestion des ressources vérifie les pointeurs liés aux brutes à partir de C++ Core Guidelines](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management).

  - **Les règles de pointeur unique** appliquer [vérifie de gestion des ressources liées aux types avec une sémantique de pointeur unique à partir de C++ Core Guidelines](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management).

  - **Règles de limites** appliquer le [délimite le profil de C++ Core Guidelines](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#probounds-bounds-safety-profile).

  - **Règles de type** appliquer le [Type de profil de C++ Core Guidelines](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#prosafety-type-safety-profile).


 Vous pouvez choisir de limiter les avertissements pour une ou plusieurs des groupes. Le **Minimum Native** et **recommandé natif** règle jeux incluent les règles C++ Core Check en plus des autres vérifications PREfast. Pour afficher les ensembles de règles, ouvrez la boîte de dialogue Propriétés du projet, sélectionnez **Code Analysis\General**, ouvrez la liste déroulante dans le **des ensembles de règles** zone de liste déroulante, afin de sélectionner les **choisir plusieurs ensembles de règles** . Pour plus d’informations sur l’utilisation d’ensembles de règles dans Visual Studio, consultez [à l’aide des ensembles de règles à un groupe de règles d’analyse du Code](using-rule-sets-to-group-code-analysis-rules.md).

## <a name="macros"></a>Macros
 Le vérificateur de recommandations C++ Core est fourni avec un fichier d’en-tête qui définit les macros qui le rendent plus facile de supprimer des catégories d’avertissements dans le code :

```cpp
ALL_CPPCORECHECK_WARNINGS
CPPCORECHECK_TYPE_WARNINGS
CPPCORECHECK_RAW_POINTER_WARNINGS
CPPCORECHECK_CONST_WARNINGS
CPPCORECHECK_OWNER_POINTER_WARNINGS
CPPCORECHECK_UNIQUE_POINTER_WARNINGS
CPPCORECHECK_BOUNDS_WARNINGS
```

Ces macros correspondent aux ensembles de règles et développer dans un espace-listes séparées par des numéros d’avertissement. En utilisant les constructions de pragma approprié, vous pouvez configurer l’ensemble des règles effectif qui est intéressant pour un projet ou une section de code. Dans l’exemple suivant, l’analyse du code uniquement signalera manquant modificateurs constante :

```cpp
#include <CppCoreCheck\Warnings.h>
#pragma warning(disable: ALL_CPPCORECHECK_WARNINGS)
#pragma warning(default: CPPCORECHECK_CONST_WARNINGS)
```

## <a name="attributes"></a>Attributs
 Le compilateur Microsoft Visual C++ a une prise en charge limitée pour le GSL supprimer l’attribut.
Il peut être utilisé pour supprimer des avertissements sur expression et les blocs d’instructions à l’intérieur d’une fonction.

```cpp
// Supress only warnings from the 'r.11' rule in expression.
[[gsl::suppress(r.11)]] new int;

// Supress all warnings from the 'r' rule group (resource management) in block.
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

## <a name="suppressing-analysis-by-using-command-line-options"></a>Suppression d’analyse à l’aide des options de ligne de commande
 Au lieu de #pragmas, vous pouvez utiliser les options de ligne de commande dans la page de propriétés du fichier à supprimer des avertissements pour un projet ou un seul fichier. Par exemple, pour désactiver l’avertissement 26400 pour un fichier :

 1) Cliquez sur le fichier dans **l’Explorateur de solutions**

 2) Choisissez **propriétés | C / C ++ | Ligne de commande**

 3) Dans le **des Options supplémentaires** fenêtre, ajoutez `/wd26400`.

 Vous pouvez utiliser l’option de ligne de commande pour désactiver temporairement toutes les analyses de code pour un fichier en spécifiant `/analyze-`. Cela génère l’avertissement *D9025 substitution '/analyze' avec ' / analyze-'*, ce qui vous rappellera pour réactiver l’analyse du code plus tard.

 ## <a name="corecheck_per_file"></a> L’activation de l’outil de vérification C++ Core instructions sur les fichiers de projet spécifique
Il peut parfois être utile de concentrée l’analyse du code et de tirer parti de l’IDE Visual Studio. Voici un exemple de scénario qui peut être utilisé pour les grands projets pour gagner du temps de génération et pour le rendre plus facile pour filtrer les résultats.
1.  Dans l’interface de commande définir le `esp.extension` et `esp.annotationbuildlevel` variables d’environnement.
2.  Démarrez Visual Studio à partir de l’interface de commande pour hériter de ces variables.
3.  Chargez votre projet et ouvrez ses propriétés.
4.  Activer l’analyse du code, choisissez les ensembles de règles approprié, mais n’activez pas les extensions d’analyse de code.
5.  Accédez au fichier que vous souhaitez analyser avec le vérificateur de recommandations C++ Core et ouvrez ses propriétés.
6.  Choisissez **C / C ++ \Commande Options de ligne de** et ajouter `/analyze:plugin EspXEngine.dll`
7.  Désactiver l’utilisation de l’en-tête précompilé (**C / C ++ \Precompiled en-têtes**). Cela est nécessaire, car le moteur d’extensions peut tenter de lire ses informations internes à partir de l’en-tête précompilé et si ce dernier a été compilé avec les options de projet par défaut, il ne seront pas compatible.
8.  Regénérez le projet. Les vérifications de PREFast communes doivent s’exécuter sur tous les fichiers. Étant donné que le vérificateur de recommandations C++ Core n’est pas activé par défaut, il doit s’exécuter uniquement sur le fichier qui est configuré pour l’utiliser.

## <a name="how-to-use-the-c-core-guidelines-checker-outside-of-visual-studio"></a>Comment utiliser le vérificateur de recommandations C++ Core en dehors de Visual Studio
Vous pouvez utiliser les vérifications C++ Core Guidelines dans les générations automatisées.

### <a name="msbuild"></a>MSBuild
 L’outil de vérification de l’analyse du Code natif (PREfast) est intégré dans l’environnement de MSBuild par les fichiers de cibles personnalisées. Vous pouvez utiliser les propriétés du projet pour l’activer et ajouter le vérificateur de recommandations C++ Core (qui est basé sur PREfast) :

 ```xml
  <PropertyGroup>
    <EnableCppCoreCheck>true</EnableCppCoreCheck>
    <CodeAnalysisRuleSet>CppCoreCheckRules.ruleset</CodeAnalysisRuleSet>¬¬
    <RunCodeAnalysis>true</RunCodeAnalysis>
  </PropertyGroup>
```
Assurez-vous que vous ajoutez ces propriétés avant l’importation du fichier Microsoft.Cpp.targets. Vous pouvez choisir des ensembles de règles spécifique, ou créer un ensemble de règles personnalisé ou utiliser l’ensemble de règles par défaut qui inclut d’autres vérifications PREfast.

Vous pouvez exécuter l’outil de vérification de base C++ uniquement sur les fichiers spécifiés à l’aide de la même approche que [décrit précédemment](#coreckeck_per_file), mais l’utilisation de fichiers de MSBuild. Les variables d’environnement peuvent être définies à l’aide de la `BuildMacro` élément :

```xml
<ItemGroup>
    <BuildMacro Include="Esp_AnnotationBuildLevel">
      <EnvironmentVariable>true</EnvironmentVariable>
      <Value>Ignore</Value>
    </BuildMacro>
    <BuildMacro Include="Esp_Extensions">
      <EnvironmentVariable>true</EnvironmentVariable>
      <ValueCppCoreCheck.dll</Value>
    </BuildMacro>
</ItemGroup>
```

Si vous ne souhaitez pas modifier le fichier projet, vous pouvez passer des propriétés sur la ligne de commande :

```cmd
msbuild /p:EnableCppCoreCheck=true /p:RunCodeAnalysis=true /p:CodeAnalysisRuleSet=CppCoreCheckRules.ruleset ...
```

### <a name="non-msbuild-projects"></a>Projets non MSBuild
Si vous utilisez un système de génération qui ne repose pas sur MSBuild, vous pouvez toujours exécuter l’outil de vérification, mais vous devrez vous familiariser avec certains mécanismes internes de la configuration du moteur de l’analyse du Code (qui n’est pas nécessairement être pris en charge dans le futur).

Vous devez définir quelques variables d’environnement et utilisez les options de ligne de commande appropriée pour le compilateur. Il est préférable fonctionner sous l’environnement « invite de commandes des outils natifs » afin que vous n’êtes pas obligé de rechercher des chemins d’accès spécifiques pour le compilateur, inclure des répertoires, etc.

1.  **Variables d’environnement**
  - `set esp.extensions=cppcorecheck.dll` Cela indique au moteur de charger le module C++ Core Guidelines.
  - `set esp.annotationbuildlevel=ignore` Cela désactive la logique qui traite les annotations SAL. Annotations n’affectent pas l’analyse du code dans le vérificateur de recommandations C++ Core, mais leur prend de traitement temps (parfois beaucoup de temps). Ce paramètre est facultatif mais fortement recommandé.
  - `set caexcludepath=%include%` Nous vous recommandons vivement de désactiver les avertissements qui se déclenchent sur les en-têtes standard. Vous pouvez ajouter plusieurs chemins d’accès ici, par exemple le chemin d’accès pour les en-têtes courants dans votre projet.
2.  **Options de ligne de commande**
  - `/analyze`  Active l’analyse du code (vous pouvez utiliser / analyze : uniquement et / analyze : quiet).
  - `/analyze:plugin EspXEngine.dll` Cette option charge le moteur de Code Analysis Extensions dans le PREfast. Ce moteur, charge à son tour, le vérificateur de recommandations C++ Core.



## <a name="use-the-guideline-support-library"></a>Utiliser la bibliothèque de prise en charge d’indication
 La bibliothèque de prise en charge d’indication est conçue pour vous aider à suivre les instructions de base. GSL inclut les définitions qui vous permettent de remplacer des constructions susceptibles d’engendrer des erreurs avec des solutions plus sûres. Par exemple, vous pouvez remplacer un `T*, length` paire de paramètres avec le `span<T>` type. GSL est disponible à l’adresse [ http://www.nuget.org/packages/Microsoft.Gsl ](http://www.nuget.org/packages/Microsoft.Gsl). La bibliothèque étant open source, vous pouvez afficher les sources, formuler des commentaires ou contribuer. Vous trouverez le projet dans [ https://github.com/Microsoft/GSL ](https://github.com/Microsoft/GSL).

 ## <a name="vs2015_corecheck"></a> Utilisez les recommandations C++ Core Check dans les projets Visual Studio 2015
  Si vous utilisez Visual Studio 2015, les ensembles de règles analyse de code C++ Core Check ne sont pas installés par défaut. Vous devez effectuer quelques étapes supplémentaires avant de pouvoir activer les outils d’analyse de code C++ Core Check dans Visual Studio 2015. Microsoft prend en charge pour les projets Visual Studio 2015 à l’aide d’un package Nuget. Le package est nommé Microsoft.CppCoreCheck, et il est disponible à l’adresse [ http://www.nuget.org/packages/Microsoft.CppCoreCheck ](http://www.nuget.org/packages/Microsoft.CppCoreCheck). Ce package nécessite que vous avez au moins installé Visual Studio 2015 avec Update 1.

 Le package installe également un autre package en tant que dépendance, un en-tête seule orientation prise en charge de bibliothèque (GSL). GSL est également disponible sur GitHub à l’adresse [ https://github.com/Microsoft/GSL ](https://github.com/Microsoft/GSL).

 En raison de la façon dont les règles d’analyse de code sont chargés, vous devez installer le package NuGet de Microsoft.CppCoreCheck dans chaque projet C++ que vous souhaitez vérifier dans Visual Studio 2015.

#### <a name="to-add-the-microsoftcppcorecheck-package-to-your-project-in-visual-studio-2015"></a>Pour ajouter le package de Microsoft.CppCoreCheck à votre projet dans Visual Studio 2015

1.  Dans **l’Explorateur de solutions**, avec le bouton droit pour ouvrir le menu contextuel de votre projet dans la solution que vous souhaitez ajouter le package. Choisissez **gérer les Packages NuGet** pour ouvrir le **Gestionnaire de Package NuGet**.

2.  Dans le **Gestionnaire de Package NuGet** fenêtre, recherchez Microsoft.CppCoreCheck.

     ![Fenêtre du Gestionnaire de Package NuGet montre CppCoreCheck package](../code-quality/media/cppcorecheck_nuget_window.png)

3.  Sélectionnez le package Microsoft.CppCoreCheck, puis choisissez le **installer** pour ajouter les règles à votre projet.

 Le package NuGet ajoute un fichier .targets de MSBuild supplémentaire à votre projet qui est appelé lorsque vous activez l’analyse du code dans votre projet. Ce fichier .targets ajoute les règles C++ Core Check comme une extension supplémentaire à l’outil d’analyse de code Visual Studio. Lorsque le package est installé, vous pouvez utiliser la boîte de dialogue Pages de propriétés pour activer ou désactiver les règles publiées et expérimentales.

