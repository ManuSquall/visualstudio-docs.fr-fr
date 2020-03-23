---
title: Tâche CL | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.UseUnicodeForAssemblerListing
- vc.task.cl
- VC.Project.VCCLCompilerTool.TreatSpecificWarningsAsErrors
- VC.Project.VCCLCompilerTool.CreateHotpatchableImage
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild (C++), CL task
- CL task (MSBuild (C++))
ms.assetid: 651ba971-b755-4f03-a549-4816beb3cc0d
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bb0e1feee1f7e1d271dd436a1879731354cbd8bb
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "78865334"
---
# <a name="cl-task"></a>CL (tâche)

Enveloppe l’outil de compilation Microsoft CMD, *cl.exe*. Le compilateur produit des fichiers exécutables (*.exe),* des fichiers de bibliothèque de liaison dynamique *(.dll)* ou des fichiers module de code *(.netmodule).* Pour plus d’informations, consultez [les options Compiler](/cpp/build/reference/compiler-options) et [utilisez MSBuild à partir de la ligne de commande](/cpp/build/msbuild-visual-cpp) et utilisez [l’toolset Microsoft CMD de la ligne de commande](/cpp/build/building-on-the-command-line).

## <a name="parameters"></a>Paramètres

 La liste ci-dessous décrit les paramètres de la tâche **CL**. La plupart des paramètres de tâche, et quelques ensembles de paramètres, correspondent à une option de ligne de commande.

- **AdditionalIncludeDirectories**

   Paramètre String[] facultatif.

   Ajoute un répertoire à la liste des répertoires dans lesquels sont recherchés les fichiers include.

   Pour plus d’informations, voir [/I (Additional include directories)](/cpp/build/reference/i-additional-include-directories).

- **Options supplémentaires**

   Paramètre de chaîne facultatif.

   Liste des options de ligne de commande. Par exemple, « /\<option1> /\<option2> /\<option#> ». Utilisez ce paramètre pour spécifier des options de ligne de commande qui ne sont pas représentées par un autre paramètre de tâche.

   Pour plus d’informations, voir [options Compiler](/cpp/build/reference/compiler-options).

- **AdditionalUsingDirectories**

   Paramètre String[] facultatif.

   Spécifie un répertoire dans lequel le compilateur doit faire une recherche en vue de résoudre les références de fichiers transmises à la directive **#using**.

   Pour plus d’informations, voir [/AI (Specify métadonnées)](/cpp/build/reference/ai-specify-metadata-directories).

- **AlwaysAppend**

   Paramètre de chaîne facultatif.

   Chaîne qui toujours est émise sur la ligne de commande. Sa valeur par défaut est «  **/c** ».

- **AssemblerListingLocation**

   Crée un fichier listing qui contient le code de l’assembly.

   Pour plus d’informations, voir l’option **/Fa** en [/FA, /Fa (Fichier d’inscription)](/cpp/build/reference/fa-fa-listing-file).

- **AssemblerOutput**

   Paramètre de chaîne facultatif.

   Crée un fichier listing qui contient le code de l’assembly.

   Spécifiez l'une des valeurs suivantes, chacune d'elles correspondant à une option de ligne de commande.

  - **Aucun>** - *\<*

  - **AssemblyCode** - **/FA**

  - **AssemblyAndMachineCode** - **/FAc**

  - **AssemblyAndSourceCode** - **/FAs**

  - **Tous** - **/FAcs**

    Pour plus d’informations, voir le **/FA**, **/FAc**, **/FAs**, et **/FAcs** options en [/FA, /Fa (Fichier d’inscription)](/cpp/build/reference/fa-fa-listing-file).

- **BasicRuntimeChecks**

   Paramètre de chaîne facultatif.

   Active et désactive la fonctionnalité de vérification des erreurs d’exécution, conjointement avec le pragma [runtime_checks](/cpp/preprocessor/runtime-checks).

   Spécifiez l'une des valeurs suivantes, chacune d'elles correspondant à une option de ligne de commande.

  - **Default** -                          *Défaut\<aucun>*

  - **StackFrameRuntimeCheck** - **/RTC**

  - **UninitializedLocalUsageCheck** - **/RTCu**

  - **EnableFastChecks** -                          **/RTC1**

    Pour plus d’informations, voir [/RTC (Vérifications d’erreur en temps de fonctionnement)](/cpp/build/reference/rtc-run-time-error-checks).

- **BrowseInformation**

   Paramètre booléen facultatif.

   Si `true`, crée un fichier d’informations de consultation.

   Pour plus d’informations, voir l’option **/FR** [en/FR, /Fr (Créer .sbr fichier)](/cpp/build/reference/fr-fr-create-dot-sbr-file).

- **BrowseInformationFile**

   Paramètre de chaîne facultatif.

   Spécifie un nom pour le fichier d’informations de consultation.

   Pour plus d’informations, voir le **paramètre BrowseInformation** dans ce tableau, et aussi voir [/FR, /Fr (Créer .sbr fichier)](/cpp/build/reference/fr-fr-create-dot-sbr-file).

- **BufferSecurityCheck**

   Paramètre booléen facultatif.

   Si `true`, détecte des dépassements de mémoire tampon qui remplacent l’adresse de retour, une technique courante pour exploiter le code qui n’applique pas les restrictions de taille de la mémoire tampon.

   Pour plus d’informations, consultez [/GS (Vérification de la sécurité des mémoires tampons)](/cpp/build/reference/gs-buffer-security-check).

- **BuildingInIDE**

   Paramètre booléen facultatif.

   Si `true`, indique que **MSBuild** est appelé par l’IDE. Dans le cas contraire, **MSBuild** est appelé sur la ligne de commande.

- **CallingConvention**

   Paramètre de chaîne facultatif.

   Spécifie la convention d’appel qui détermine l’ordre dans lequel les arguments de fonction sont poussés sur la pile, si la fonction de l’appelant ou la fonction appelée supprime les arguments de la pile à la fin de l’appel, ainsi que la convention de décoration de nom que le compilateur utilise pour identifier des fonctions individuelles.

   Spécifiez l'une des valeurs suivantes, chacune d'elles correspondant à une option de ligne de commande.

  - **Cdecl** - **/Gd**

  - **FastCall** -                          **/Gr**

  - **StdCall** -                          **/Gz**

    Pour plus d’informations, voir [/Gd, /Gr, /Gv, /Gz (Convention d’appel)](/cpp/build/reference/gd-gr-gv-gz-calling-convention).

- **CompileAs**

   Paramètre de chaîne facultatif.

   Spécifie s’il convient de compiler le fichier d’entrée en tant que fichier source C ou C++.

   Spécifiez l'une des valeurs suivantes, chacune d'elles correspondant à une option de ligne de commande.

  - **Default** - *Défaut\<aucun>*

  - **ComppilileAsC** - **/TC**

  - **ComppilileAsCpp** - **/TP**

    Pour plus d’informations, voir [/Tc, /Tp, /TC, /TP (Spécifier le type de fichier source)](/cpp/build/reference/tc-tp-tc-tp-specify-source-file-type).

- **CompileAsManaged**

   Paramètre de chaîne facultatif.

   Permet aux applications et aux composants d’utiliser les fonctionnalités du Common Language Runtime (CLR).

   Spécifiez l'une des valeurs suivantes, chacune d'elles correspondant à une option de ligne de commande.

  - **faux** - *aucun>\<*

  - **vrai** - **/clr**

  - **Pure** - **/clr:pure**

  - **Coffre-fort** - **/clr:safe**

  - **OldSyntax** - **/clr:oldSyntax**

    Pour plus d’informations, consultez [/clr (Compilation pour le Common Language Runtime)](/cpp/build/reference/clr-common-language-runtime-compilation).

- **CreateHotpatchableImage**

   Paramètre booléen facultatif.

   Si `true`, indique au compilateur de préparer une image pour la *création d’images corrigeables en mémoire*. Ce paramètre vérifie que la première instruction de chaque fonction utilise deux octets, comme cela est requis pour la création d’images corrigeables en mémoire.

   Pour plus d’informations, voir [/hotpatch (Créer l’image hotpatchable)](/cpp/build/reference/hotpatch-create-hotpatchable-image).

- **DebugInformationFormat**

   Paramètre de chaîne facultatif.

   Sélectionne le type d’informations de débogage créées pour votre programme et si ces informations sont conservées dans des fichiers objet *(.obj)* ou dans une base de données de programme (PDB).

   Spécifiez l'une des valeurs suivantes, chacune d'elles correspondant à une option de ligne de commande.

  - **OldStyle** - **/Z7**

  - **ProgramDatabase** - **/Zi**

  - **EditAndContinue** - **/ZI**

    Pour plus d’informations, voir [/Z7, /Zi, /ZI (Format d’information Debug)](/cpp/build/reference/z7-zi-zi-debug-information-format).

- **DisableLanguageExtensions**

   Paramètre booléen facultatif.

   Si **true**, indique au compilateur d’émettre une erreur pour les constructions de langage qui ne sont compatibles ni avec ANSI C ni avec ANSI C++.

   Pour plus d’informations, voir l’option **/Za** dans [/Za, /Ze (Extensions de langue de désactivation)](/cpp/build/reference/za-ze-disable-language-extensions).

- **DisableSpecificWarnings**

   Paramètre String[] facultatif.

   Désactive les numéros d’avertissement spécifiés dans une liste séparée par des points-virgules.

   Pour plus d’informations, voir l’option `/wd` en [/w, /W0, /W1, /W2, /W3, /W4, /w1, /w2, /w3, /w4, /Wall, /wd, /we, /wo, /Wv, /WX (niveau d’avertissement)](/cpp/build/reference/compiler-option-warning-level).

- **EnableEnhancedInstructionSet**

   Paramètre de chaîne facultatif.

   Spécifie l’architecture de génération de code qui utilise les instructions des extensions Streaming SIMD (SSE) et des extensions Streaming SIMD 2 (SSE2).

   Spécifiez l'une des valeurs suivantes, chacune d'elles correspondant à une option de ligne de commande.

  - **StreamingSIMDExtensions** - **/arch:SSE**

  - **StreamingSIMDExtensions2** - **/arch:SSE2**

    Pour plus d’informations, consultez l’article [/arch (x86)](/cpp/build/reference/arch-x86).

- **EnableFiberSafeOptimizations**

   Paramètre booléen facultatif.

   Si `true`, prend en charge la sécurité des fibres pour les données allouées en utilisant un stockage local des threads de type statique, autrement dit les données allouées en utilisant `__declspec(thread)`.

   Pour plus d’informations, voir [/GT (Support fibre-safe thread-local stockage)](/cpp/build/reference/gt-support-fiber-safe-thread-local-storage).

- **EnablePREfast**

   Paramètre booléen facultatif.

   Si `true`, active l’analyse du code.

   Pour plus d’informations, voir [/analyser (analyse du code)](/cpp/build/reference/analyze-code-analysis).

- **ErreurReporting**

   Paramètre de chaîne facultatif.

   Vous permet de signaler les erreurs internes du compilateur (ICE) directement à Microsoft. Par défaut, dans les générations en mode IDE, le paramètre est **Prompt** tandis que dans les générations en mode ligne de commande, il s’agit du paramètre **Queue**.

   Spécifiez l'une des valeurs suivantes, chacune d'elles correspondant à une option de ligne de commande.

  - **Aucun** - **/erreurReport:aucun**

  - **Prompt** - **/erreurReport:prompt**

  - **File d’attente** - **/erreurReport:file d’attente**

  - **Envoyer** - **/errorReport:envoyer**

    Pour plus d’informations, voir [/erreurReport (Rapport erreurs de compilateur interne)](/cpp/build/reference/errorreport-report-internal-compiler-errors).

- **ExceptionHandling**

   Paramètre de chaîne facultatif.

   Spécifie le modèle de gestion des exceptions à utiliser par le compilateur.

   Spécifiez l'une des valeurs suivantes, chacune d'elles correspondant à une option de ligne de commande.

  - **faux** - *aucun>\<*

  - **Async** - **/EHa**

  - **Synchronisez** - **/EHsc**

  - **SyncCThrow** - **/EHs**

    Pour plus d’informations, voir [/EH (modèle de manutention d’exception)](/cpp/build/reference/eh-exception-handling-model).

- **ExpandAttributedSource**

   Paramètre booléen facultatif.

   Si `true`, crée un fichier listing dont les attributs développés sont injectés dans le fichier source.

   Pour plus d’informations, voir [/Fx (Merge code injecté)](/cpp/build/reference/fx-merge-injected-code).

- **FavorSizeOrSpeed**

   Paramètre de chaîne facultatif.

   Spécifie s’il convient de privilégier la vitesse du code ou sa taille.

   Spécifiez l'une des valeurs suivantes, chacune d'elles correspondant à une option de ligne de commande.

  - **Ni** - *aucun>\<*

  - **Taille** - **/Os**

  - **Vitesse** - **/Ot**

    Pour plus d’informations, voir [/Os, /Ot (Favor petit code, favoriser le code rapide)](/cpp/build/reference/os-ot-favor-small-code-favor-fast-code).

- **FloatingPointExceptions**

   Paramètre booléen facultatif.

   Si `true`, active le modèle de virgule flottante fiable. Des exceptions sont levées dès leur déclenchement.

   Pour plus d’informations, voir le /**fp: sauf** option en [/fp (Spécifier le comportement à point flottant)](/cpp/build/reference/fp-specify-floating-point-behavior).

- **FloatingPointModel**

   Paramètre de chaîne facultatif.

   Définit le modèle de virgule flottante.

   Spécifiez l'une des valeurs suivantes, chacune d'elles correspondant à une option de ligne de commande.

  - **Précis** - **/fp:précis**

  - **Strict** - **/fp:strict**

  - **Rapide** - **/fp:rapide**

    Pour plus d’informations, voir [/fp (Spécifier le comportement à point flottant)](/cpp/build/reference/fp-specify-floating-point-behavior).

- **ForceConformanceInForLoopScope**

   Paramètre booléen facultatif.

   Si `true`, implémente un comportement C++ standard dans les boucles [for](/cpp/cpp/for-statement-cpp) utilisant les extensions Microsoft ([/Ze](/cpp/build/reference/za-ze-disable-language-extensions)).

   Pour plus d’informations, voir [/Zc:forScope (Force conformance in for loop scope)](/cpp/build/reference/zc-forscope-force-conformance-in-for-loop-scope).

- **ForcedIncludeFiles**

   Paramètre `String[]` facultatif.

   Entraîne le traitement d’un ou de plusieurs fichiers d’en-tête spécifiés par le préprocesseur.

   Pour plus d’informations, voir [/FI (Nom forcé inclure fichier)](/cpp/build/reference/fi-name-forced-include-file).

- **ForcedUsingFiles**

   Paramètre **de chaîne en** option.

   Entraîne le traitement d’un ou de plusieurs fichiers **#using** spécifiés par le préprocesseur.

   Pour plus d’informations, voir [/FU (Nom forcé #using fichier)](/cpp/build/reference/fu-name-forced-hash-using-file).

- **FunctionLevelLinking**

   Paramètre `Boolean` facultatif.

   Si `true`, permet au compilateur d’empaqueter des fonctions individuelles sous la forme de fonctions empaquetées (COMDATs).

   Pour plus d’informations, voir [/Gy (Activer le lien au niveau de la fonction)](/cpp/build/reference/gy-enable-function-level-linking).

- **GenerateXMLDocumentationFiles**

   Paramètre `Boolean` facultatif.

   Si, `true`provoque le compilateur de traiter les commentaires de documentation dans les fichiers de code source et de créer un fichier *.xdc* pour chaque fichier de code source qui a des commentaires de documentation.

   Pour plus d’informations, voir [/doc (commentaires de documentation des processus) (C/C)](/cpp/build/reference/doc-process-documentation-comments-c-cpp). Consultez également le paramètre **XMLDocumentationFileName** dans ce tableau.

- **IgnoreStandardIncludePath**

   Paramètre `Boolean` facultatif.

   Si `true`, empêche le compilateur de rechercher des fichiers include dans les répertoires spécifiés dans les variables d’environnement PATH et INCLUDE.

   Pour plus d’informations, voir [/X (Ignorer la norme inclure les chemins)](/cpp/build/reference/x-ignore-standard-include-paths).

- **InlineFunctionExpansion**

   Paramètre **de chaîne** facultatif.

   Spécifie le niveau d’expansion des fonctions inline pour la génération.

   Spécifiez l'une des valeurs suivantes, chacune d'elles correspondant à une option de ligne de commande.

  - **Default** - *Défaut\<aucun>*

  - **Désactivé** - **/Ob0**

  - **SeulementExplicitInline** - **/Ob1**

  - **AnySuitable** - **/Ob2**

    Pour plus d’informations, voir [/Ob (Extension de la fonction Inline)](/cpp/build/reference/ob-inline-function-expansion).

- **IntrinsicFunctions**

   Paramètre `Boolean` facultatif.

   Si `true`, remplace certains appels de fonction par une forme intrinsèque ou par d’autres formes spéciales de la fonction qui contribuent à une exécution plus rapide de votre application.

   Pour plus d’informations, voir [/Oi (Générer des fonctions intrinsèques)](/cpp/build/reference/oi-generate-intrinsic-functions).

- **MinimalRebuild**

   Paramètre `Boolean` facultatif.

   Si `true`, permet une régénération minimale, qui détermine si les fichiers sources C++ qui incluent des définitions de classe C++ modifiées (stockées dans des fichiers d’en-tête [.h]) doivent être recompilés.

   Pour plus d’informations, voir [/Gm (Activer la reconstruction minimale)](/cpp/build/reference/gm-enable-minimal-rebuild).

- **MultiProcessorCompilation**

   Paramètre `Boolean` facultatif.

   Si `true`, utilise plusieurs processeurs pour procéder à la compilation. Ce paramètre crée un processus pour chaque processeur effectif de votre ordinateur.

   Pour plus d’informations, voir [/MP (Construire avec plusieurs processus)](/cpp/build/reference/mp-build-with-multiple-processes). Consultez également le paramètre **ProcessorNumber** dans ce tableau.

- **ObjectFileName**

   Paramètre **de chaîne** facultatif.

   Spécifie un nom de fichier objet (.obj) ou un répertoire à utiliser à la place de la valeur par défaut.

   Pour plus d’informations, consultez [/Fo (Nom de fichier objet)](/cpp/build/reference/fo-object-file-name).

- **ObjectFiles**

   Paramètre **de chaîne en** option.

   Liste des fichiers objets.

- **OmitDefaultLibName**

   Paramètre `Boolean` facultatif.

   Si `true`, omet le nom par défaut de la bibliothèque C run-time du fichier objet *(.obj).* Par défaut, le compilateur met le nom de la bibliothèque dans le fichier *.obj* pour diriger le lien vers la bibliothèque correcte.

   Pour plus d’informations, voir [/Zl (Omit nom de bibliothèque par défaut)](/cpp/build/reference/zl-omit-default-library-name).

- **OmitFramePointers**

   Paramètre `Boolean` facultatif.

   Si `true`, empêche la création des pointeurs de frame sur la pile des appels.

   Pour plus d’informations, voir [/Oy (Omission Frame-pointer)](/cpp/build/reference/oy-frame-pointer-omission).

- **OpenMPSupport**

   Paramètre `Boolean` facultatif.

   Si `true`, le compilateur traite les clauses et directives OpenMP.

   Pour plus d’informations, voir [/openmp (Activer le support OpenMP 2.0)](/cpp/build/reference/openmp-enable-openmp-2-0-support).

- **Optimisation**

   Paramètre **de chaîne** facultatif.

   Spécifie différentes optimisations de code en termes de vitesse et de taille.

   Spécifiez l'une des valeurs suivantes, chacune d'elles correspondant à une option de ligne de commande.

  - **Désactivé** - **/Od**

  - **MinSpace** - **/O1**

  - **MaxSpeed** - **/O2**

  - **Plein** - **/Ox**

    Pour plus d’informations, consultez [/O, options (Optimiser le code)](/cpp/build/reference/o-options-optimize-code).

- **PrecompiledHeader**

   Paramètre **de chaîne** facultatif.

   Créez ou utilisez un fichier en tête précalculé *(.pch)* pendant la construction.

   Spécifiez l'une des valeurs suivantes, chacune d'elles correspondant à une option de ligne de commande.

  - **NotUing** - *\<aucun>*

  - **Créer** - **/Yc**

  - **Utiliser** - **/Yu**

    Pour plus d’informations, voir [/Yc (Créer un fichier d’en-tête précompilé)](/cpp/build/reference/yc-create-precompiled-header-file) et [/Yu (Utilisez le fichier d’en-tête précompilé)](/cpp/build/reference/yu-use-precompiled-header-file). Consultez également les paramètres **PrecompiledHeaderFile** et **PrecompiledHeaderOutputFile** dans ce tableau.

- **PrecompiledHeaderFile**

   Paramètre **de chaîne** facultatif.

   Spécifie un nom de fichier d’en-tête précompilé à créer ou utiliser.

   Pour plus d’informations, voir [/Yc (Créer un fichier d’en-tête précompilé)](/cpp/build/reference/yc-create-precompiled-header-file) et [/Yu (Utilisez le fichier d’en-tête précompilé)](/cpp/build/reference/yu-use-precompiled-header-file).

- **PrecompiledHeaderOutputFile**

   Paramètre **de chaîne** facultatif.

   Spécifie un nom de chemin d’accès pour un en-tête précompilé au lieu d’utiliser le nom du chemin d’accès par défaut.

   Pour plus d’informations, voir [/Fp (Nom .pch fichier)](/cpp/build/reference/fp-name-dot-pch-file).

- **PreprocessKeepComments**

   Paramètre `Boolean` facultatif.

   Si `true`, conserve les commentaires pendant le prétraitement.

   Pour plus d’informations, voir [/C (Préserver les commentaires pendant le prétraitement)](/cpp/build/reference/c-preserve-comments-during-preprocessing).

- **PreprocessorDefinitions**

   Paramètre `String[]` facultatif.

   Définit un symbole de prétraitement pour votre fichier source.

   Pour plus d’informations, voir [/D (définitions préprocesseurs)](/cpp/build/reference/d-preprocessor-definitions).

- **PreprocessOutput**

   Paramètre `ITaskItem[]` facultatif.

   Définit un tableau d’éléments de sortie de préprocesseur pouvant être consommés et émis par des tâches.

- **PreprocessOutputPath**

   Paramètre `String` facultatif.

   Spécifie le nom du fichier de sortie dans lequel le paramètre **PreprocessToFile** écrit la sortie prétraitée.

   Pour plus d’informations, voir [/Fi (Nom de fichier de sortie de préprocessus)](/cpp/build/reference/fi-preprocess-output-file-name).

- **PreprocessSuppressLineNumbers**

   Paramètre `Boolean` facultatif.

   Si `true`, prétraite les fichiers sources C et C++ et copie les fichiers prétraités sur le périphérique de sortie standard.

   Pour plus d’informations, voir [/EP (Preprocess to stdout sans directives #line)](/cpp/build/reference/ep-preprocess-to-stdout-without-hash-line-directives).

- **PreprocessToFile**

   Paramètre `Boolean` facultatif.

   Si `true`, prétraite les fichiers sources C et C++ et copie la sortie prétraitée dans un fichier.

   Pour plus d’informations, voir [/P (Préprocesser à un fichier)](/cpp/build/reference/p-preprocess-to-a-file).

- **ProcessorNumber**

   Paramètre `Integer` facultatif.

   Spécifie le nombre maximal de processeurs à utiliser dans une compilation multiprocesseur. Utilisez ce paramètre conjointement avec le paramètre **MultiProcessorCompilation**.

- **ProgramDataBaseFileName**

   Paramètre `String` facultatif.

   Spécifie un nom pour le fichier de base de données du programme (PDB).

   Pour plus d’informations, voir [/Fd (Nom de fichier de base de données du programme)](/cpp/build/reference/fd-program-database-file-name).

- **RuntimeLibrary**

   Paramètre `String` facultatif.

   Indique si un module multithread est une DLL et sélectionne les versions retail ou debug de la bibliothèque runtime.

   Spécifiez l'une des valeurs suivantes, chacune d'elles correspondant à une option de ligne de commande.

  - **MultiThreaded** - **/MT**

  - **MultiThreadedDebug** - **/MTd**

  - **MultiThreadedDLL** - **/MD**

  - **MultiThreadedDebugDLL** - **/MDd**

    Pour plus d’informations, voir [/MD, /MT, /LD (Utilisez la bibliothèque de temps d’exécution)](/cpp/build/reference/md-mt-ld-use-run-time-library).

- **RuntimeTypeInfo**

   Paramètre `Boolean` facultatif.

   Si `true`, ajoute le code pour vérifier les types d’objet C++ à l’exécution (informations de type au moment de l’exécution).

   Pour plus d’informations, voir [/GR (Activez les informations de type temps d’exécution)](/cpp/build/reference/gr-enable-run-time-type-information).

- **ShowIncludes**

   Paramètre `Boolean` facultatif.

   Si `true`, le compilateur sort la liste des fichiers include.

   Pour plus d’informations, voir [/showIncludes (Liste inclure les fichiers)](/cpp/build/reference/showincludes-list-include-files).

- **SmallerTypeCheck**

   Paramètre `Boolean` facultatif.

   Si `true`, signale une erreur d’exécution si une valeur est affectée à un type de données inférieur et provoque une perte de données.

   Pour plus d’informations, voir l’option **/RTCc** dans [/RTC (Vérifications d’erreur à durée de course)](/cpp/build/reference/rtc-run-time-error-checks).

- **récentes**

   Paramètre `ITaskItem[]` requis.

   Spécifie la liste des fichiers sources séparés par des espaces.

- **StringPooling**

   Paramètre `Boolean` facultatif.

   Si `true`, permet au compilateur de créer une copie de chaînes identiques dans l’image du programme.

   Pour plus d’informations, voir [/GF (Éliminer les chaînes en double)](/cpp/build/reference/gf-eliminate-duplicate-strings).

- **StructMemberAlignment**

   Paramètre `String` facultatif.

   Spécifie l’alignement des octets pour tous les membres d’une structure.

   Spécifiez l'une des valeurs suivantes, chacune d'elles correspondant à une option de ligne de commande.

  - **Défaut** - **/Zp1**

  - **1Byte** - **/Zp1**

  - **2Bytes** - **/Zp2**

  - **4Bytes** - **/Zp4**

  - **8Bytes** - **/Zp8**

  - **16Bytes** - **/Zp16**

    Pour plus d’informations, voir [/Zp (alignement des membres Struct)](/cpp/build/reference/zp-struct-member-alignment).

- **SuppressStartupBanner**

   Paramètre `Boolean` facultatif.

   Si la valeur est `true`, empêche l'affichage du message de copyright et de numéro de version quand la tâche démarre.

   Pour plus d’informations, voir [/nologo (Supprimer la bannière startup) (C/C)](/cpp/build/reference/nologo-suppress-startup-banner-c-cpp).

- **TrackerLogDirectory**

   Paramètre `String` facultatif.

   Spécifie le répertoire intermédiaire dans lequel sont stockés les fichiers journaux de suivi de cette tâche.

   Pour plus d’informations, consultez les paramètres **TLogReadFiles** et **TLogWriteFiles** dans ce tableau.

- **TreatSpecificWarningsAsErrors**

   Paramètre **de chaîne en** option.

   Traite la liste spécifiée des avertissements du compilateur comme des erreurs.

   Pour plus d’informations, voir **l’option /nous** `n` en [/w, /W0, /W1, /W2, /W3, /W4, /w1, /w2, /w3, /w4, /Wall, /wd, /we, /wo, /Wv, /WX (niveau d’avertissement)](/cpp/build/reference/compiler-option-warning-level).

- **TreatWarningAsError**

   Paramètre `Boolean` facultatif.

   Si `true`, considère tous les avertissements du compilateur comme des erreurs.

   Pour plus d’informations, voir **/WX** option en [/w, /W0, /W1, /W2, /W3, /W4, /w1, /w2, /w3, /w4, /Wall, /wd, /we, /wo, /Wv, /WX (niveau d’avertissement)](/cpp/build/reference/compiler-option-warning-level).

- **TreatWChar_tAsBuiltInType**

   Paramètre `Boolean` facultatif.

   Si `true`, considère le type `wchar_t` comme un type natif.

   Pour plus d’informations, voir [/Zc:wchar_t (wchar_t est de type natif)](/cpp/build/reference/zc-wchar-t-wchar-t-is-native-type).

- **UndefineAllPreprocessorDefinitions**

   Paramètre `Boolean` facultatif.

   Si `true`, annule la définition des symboles propres à Microsoft que le compilateur définit.

   Pour plus d’informations, voir l’option **/u** en [/U, /u (symboles indéfinis)](/cpp/build/reference/u-u-undefine-symbols).

- **UndefinePreprocessorDefinitions**

   Paramètre `String[]` facultatif.

   Indique une liste d’un ou de plusieurs symboles de préprocesseur dont la définition va être annulée.

   Pour plus d’informations, voir **/U** option en [/U, /u (Symboles indéfinis)](/cpp/build/reference/u-u-undefine-symbols).

- **UseFullPaths**

   Paramètre `Boolean` facultatif.

   Si `true`, affiche le chemin d’accès complet des fichiers de code source transmis au compilateur dans les diagnostics.

   Pour plus d’informations, voir [/FC (Voie complète du fichier de code source dans les diagnostics)](/cpp/build/reference/fc-full-path-of-source-code-file-in-diagnostics).

- **UseUnicodeForAssemblerListing**

   Paramètre `Boolean` facultatif.

   Si `true`, entraîne la création du fichier de sortie au format UTF-8.

   Pour plus d’informations, voir l’option **/FAu** en [/FA, /Fa (Fichier d’inscription)](/cpp/build/reference/fa-fa-listing-file).

- **WarningLevel**

   Paramètre `String` facultatif.

   Spécifie le niveau d’avertissement le plus élevé devant être généré par le compilateur.

   Spécifiez l'une des valeurs suivantes, chacune d'elles correspondant à une option de ligne de commande.

  - **TurnOffAllWarnings** - **/W0**

  - **Niveau1** - **/W1**

  - **Niveau2** - **/W2**

  - **Niveau3** - **/W3**

  - **Niveau4** - **/W4**

  - **EnableAllWarnings** - **/Wall**

    Pour plus d’informations, voir **l’option /W**_n_ en [/w, /W0, /W1, /W2, /W3, /W4, /w1, /w2, /w3, /w4, /Wall, /wd, /we, /wo, /Wv, /WX (niveau d’avertissement)](/cpp/build/reference/compiler-option-warning-level).

- **WholeProgramOptimization**

   Paramètre `Boolean` facultatif.

   Si `true`, active l’optimisation de l’ensemble du programme.

   Pour plus d’informations, voir [/GL (optimisation du programme complet)](/cpp/build/reference/gl-whole-program-optimization).

- **XMLDocumentationFileName**

   Paramètre `String` facultatif.

   Spécifie le nom des fichiers de documentation XML générés. Ce paramètre peut être un nom de fichier ou de répertoire.

   Pour plus d’informations, voir l’argument `name` dans [/doc (Commentaires de documentation de processus) (C/C)](/cpp/build/reference/doc-process-documentation-comments-c-cpp). Consultez également le paramètre **GenerateXMLDocumentationFiles** dans ce tableau.

- **MinimalRebuildFromTracking**

   Paramètre `Boolean` facultatif.

   Si `true`, une génération incrémentielle suivie est exécutée ; si `false`, une régénération est exécutée.

- **TLogReadFiles**

   Paramètre `ITaskItem[]` facultatif.

   Spécifie un tableau des éléments qui représentent les *journaux de suivi des fichiers lus*.

   Un journal de suivi de fichier de lecture (*.tlog*) contient les noms des fichiers d’entrée qui sont lus par une tâche, et est utilisé par le système de construction de projet pour soutenir les constructions incrémentielles. Pour plus d’informations, consultez les paramètres **TrackerLogDirectory** et **TrackFileAccess** dans ce tableau.

- **TLogWriteFiles**

   Paramètre `ITaskItem[]` facultatif.

   Spécifie un tableau des éléments qui représentent les *journaux de suivi des fichiers écrits*.

   Un journal de suivi de fichier de rédaction (*.tlog*) contient les noms des fichiers de sortie qui sont écrits par une tâche, et est utilisé par le système de construction de projet pour soutenir les constructions incrémentielles. Pour plus d’informations, consultez les paramètres **TrackerLogDirectory** et **TrackFileAccess** dans ce tableau.

- **TrackFileAccess**

   Paramètre `Boolean` facultatif.

   Si `true`, effectue le suivi des modèles d’accès au fichier.

   Pour plus d’informations, consultez les paramètres **TLogReadFiles** et **TLogWriteFiles** dans ce tableau.

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur les tâches](../msbuild/msbuild-task-reference.md)
