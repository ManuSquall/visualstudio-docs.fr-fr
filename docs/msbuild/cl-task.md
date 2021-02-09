---
title: Tâche CL | Microsoft Docs
description: Décrit l’objectif et les paramètres de la tâche CL MSBuild, qui encapsule l’outil compilateur Microsoft C++, cl.exe.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 542d84f4c0279c1f76fa1ea29a244e78c53b394d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99878433"
---
# <a name="cl-task"></a>CL (tâche)

Encapsule l’outil compilateur Microsoft C++, *cl.exe*. Le compilateur produit des fichiers exécutables (*. exe*), des fichiers de bibliothèque de liens dynamiques (*. dll*) ou des fichiers de module de code (*. netmodule*). Pour plus d’informations, consultez [Options du compilateur](/cpp/build/reference/compiler-options) et [Utiliser MSBuild à partir de la ligne de commande](/cpp/build/msbuild-visual-cpp) et [Utilisez l’ensemble d’outils Microsoft C++ à partir de la ligne de commande](/cpp/build/building-on-the-command-line).

## <a name="parameters"></a>Paramètres

 La liste ci-dessous décrit les paramètres de la tâche **CL**. La plupart des paramètres de tâche, et quelques ensembles de paramètres, correspondent à une option de ligne de commande.

- **AdditionalIncludeDirectories**

   Paramètre String[] facultatif.

   Ajoute un répertoire à la liste des répertoires dans lesquels sont recherchés les fichiers include.

   Pour plus d’informations, consultez [/i (autres répertoires Include)](/cpp/build/reference/i-additional-include-directories).

- **AdditionalOptions**

   Paramètre de chaîne facultatif.

   Liste des options de ligne de commande. Par exemple, « / \<option1>  / \<option2>  / \<option#> ». Utilisez ce paramètre pour spécifier des options de ligne de commande qui ne sont pas représentées par un autre paramètre de tâche.

   Pour plus d’informations, consultez [Options du compilateur](/cpp/build/reference/compiler-options).

- **AdditionalUsingDirectories**

   Paramètre String[] facultatif.

   Spécifie un répertoire dans lequel le compilateur doit faire une recherche en vue de résoudre les références de fichiers transmises à la directive **#using**.

   Pour plus d’informations, consultez [/ai (spécifier les répertoires de métadonnées)](/cpp/build/reference/ai-specify-metadata-directories).

- **AlwaysAppend**

   Paramètre de chaîne facultatif.

   Chaîne qui toujours est émise sur la ligne de commande. Sa valeur par défaut est «  **/c** ».

- **AssemblerListingLocation**

   Crée un fichier listing qui contient le code de l’assembly.

   Pour plus d’informations, consultez l’option **/Fa** dans [/FA,/FA (fichier listing)](/cpp/build/reference/fa-fa-listing-file).

- **AssemblerOutput**

   Paramètre de chaîne facultatif.

   Crée un fichier listing qui contient le code de l’assembly.

   Spécifiez l'une des valeurs suivantes, chacune d'elles correspondant à une option de ligne de commande.

  - **Nolist** - *\<none>*

  - **AssemblyCode**  -  **/FA**

  - **AssemblyAndMachineCode**  -  **/FAC**

  - **AssemblyAndSourceCode**  -  **/FAS**

  - **Tout**  -  **/FACS**

    Pour plus d’informations, consultez les options **/Fa**, **/FAC**, **/FAS** et **/FACS** dans [/FA,/FA (fichier listing)](/cpp/build/reference/fa-fa-listing-file).

- **BasicRuntimeChecks**

   Paramètre de chaîne facultatif.

   Active et désactive la fonctionnalité de vérification des erreurs d’exécution, conjointement avec le pragma [runtime_checks](/cpp/preprocessor/runtime-checks).

   Spécifiez l'une des valeurs suivantes, chacune d'elles correspondant à une option de ligne de commande.

  - **Valeurs** -                          *\<none>*

  - **StackFrameRuntimeCheck**  -  **/RTCs**

  - **UninitializedLocalUsageCheck**  -  **/RTCu**

  - **EnableFastChecks**  -                           **/RTC1**

    Pour plus d’informations, consultez [/RTC (vérifications des erreurs au moment de l’exécution)](/cpp/build/reference/rtc-run-time-error-checks).

- **BrowseInformation**

   Paramètre booléen facultatif.

   Si `true`, crée un fichier d’informations de consultation.

   Pour plus d’informations, consultez l’option **/fr** dans [/fr,/fr (créer un fichier. SBR)](/cpp/build/reference/fr-fr-create-dot-sbr-file).

- **BrowseInformationFile**

   Paramètre de chaîne facultatif.

   Spécifie un nom pour le fichier d’informations de consultation.

   Pour plus d’informations, consultez le paramètre **BrowseInformation** dans ce tableau et consultez [/fr,/fr (créer un fichier. SBR)](/cpp/build/reference/fr-fr-create-dot-sbr-file).

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

  - **Cdecl**  -  **/Gd**

  - **FastCall**  -                           **/GR**

  - **StdCall**  -                           **/Gz**

    Pour plus d’informations, consultez [/GD,/GR,/GV,/gz (Convention d’appel)](/cpp/build/reference/gd-gr-gv-gz-calling-convention).

- **CompileAs**

   Paramètre de chaîne facultatif.

   Spécifie s’il convient de compiler le fichier d’entrée en tant que fichier source C ou C++.

   Spécifiez l'une des valeurs suivantes, chacune d'elles correspondant à une option de ligne de commande.

  - **Valeurs** - *\<none>*

  - **CompileAsC**  -  **/TC**

  - **CompileAsCpp**  -  **/TP**

    Pour plus d’informations, consultez [/TC,/TP,/TC,/TP (spécifier le type de fichier source)](/cpp/build/reference/tc-tp-tc-tp-specify-source-file-type).

- **CompileAsManaged**

   Paramètre de chaîne facultatif.

   Permet aux applications et aux composants d’utiliser les fonctionnalités du Common Language Runtime (CLR).

   Spécifiez l'une des valeurs suivantes, chacune d'elles correspondant à une option de ligne de commande.

  - **fausses** - *\<none>*

  - **true**  -  **/CLR**

  - **Pur**  -  **/clr : pure**

  - **Sécurité**  -  **/clr : safe**

  - **OldSyntax**  -  **/clr : oldSyntax**

    Pour plus d’informations, consultez [/clr (Compilation pour le Common Language Runtime)](/cpp/build/reference/clr-common-language-runtime-compilation).

- **CreateHotpatchableImage**

   Paramètre booléen facultatif.

   Si `true`, indique au compilateur de préparer une image pour la *création d’images corrigeables en mémoire*. Ce paramètre vérifie que la première instruction de chaque fonction utilise deux octets, comme cela est requis pour la création d’images corrigeables en mémoire.

   Pour plus d’informations, consultez [/hotpatch (créer une image corrigeable en mémoire)](/cpp/build/reference/hotpatch-create-hotpatchable-image).

- **DebugInformationFormat**

   Paramètre de chaîne facultatif.

   Sélectionne le type d’informations de débogage créées pour votre programme et indique si ces informations sont conservées dans des fichiers objets (*. obj*) ou dans une base de données de programme (PDB).

   Spécifiez l'une des valeurs suivantes, chacune d'elles correspondant à une option de ligne de commande.

  - **Ancien style**  -  **/Z7**

  - **ProgramDatabase**  -  **/Zi**

  - **EditAndContinue**  -  **/Zi**

    Pour plus d’informations, consultez [/Z7,/Zi,/ZI (format des informations de débogage)](/cpp/build/reference/z7-zi-zi-debug-information-format).

- **DisableLanguageExtensions**

   Paramètre booléen facultatif.

   Si **true**, indique au compilateur d’émettre une erreur pour les constructions de langage qui ne sont compatibles ni avec ANSI C ni avec ANSI C++.

   Pour plus d’informations, consultez l’option **/za** dans [/za,/Ze (désactiver les extensions de langage)](/cpp/build/reference/za-ze-disable-language-extensions).

- **DisableSpecificWarnings**

   Paramètre String[] facultatif.

   Désactive les numéros d’avertissement spécifiés dans une liste séparée par des points-virgules.

   Pour plus d’informations, consultez l' `/wd` option dans [/W,/W0,/W1,/W2,/W3,/W4,/W1,/W2,/W3,/W4,/Wall,/WD,/we,/WO,/WV,/WX (niveau d’avertissement)](/cpp/build/reference/compiler-option-warning-level).

- **EnableEnhancedInstructionSet**

   Paramètre de chaîne facultatif.

   Spécifie l’architecture de génération de code qui utilise les instructions des extensions Streaming SIMD (SSE) et des extensions Streaming SIMD 2 (SSE2).

   Spécifiez l'une des valeurs suivantes, chacune d'elles correspondant à une option de ligne de commande.

  - **StreamingSIMDExtensions**  -  **/arch : SSE**

  - **StreamingSIMDExtensions2**  -  **/arch : SSE2**

    Pour plus d’informations, consultez l’article [/arch (x86)](/cpp/build/reference/arch-x86).

- **EnableFiberSafeOptimizations**

   Paramètre booléen facultatif.

   Si `true`, prend en charge la sécurité des fibres pour les données allouées en utilisant un stockage local des threads de type statique, autrement dit les données allouées en utilisant `__declspec(thread)`.

   Pour plus d’informations, consultez [/gt (prendre en charge le stockage local des threads avec fibres sécurisées)](/cpp/build/reference/gt-support-fiber-safe-thread-local-storage).

- **EnablePREfast**

   Paramètre booléen facultatif.

   Si `true`, active l’analyse du code.

   Pour plus d’informations, consultez [/Analyze (analyse du code)](/cpp/build/reference/analyze-code-analysis).

- **Errorreporting (**

   Paramètre de chaîne facultatif.

   Vous permet de signaler les erreurs internes du compilateur (ICE) directement à Microsoft. Par défaut, dans les générations en mode IDE, le paramètre est **Prompt** tandis que dans les générations en mode ligne de commande, il s’agit du paramètre **Queue**.

   Spécifiez l'une des valeurs suivantes, chacune d'elles correspondant à une option de ligne de commande.

  - **Aucun**  -  **/errorreport : aucun**

  - **Invite**  -  **/errorreport : invite**

  - **File d’attente**  -  **/errorreport : queue**

  - **Envoyer**  -  **/errorreport : envoyer**

    Pour plus d’informations, consultez [/errorreport (signaler les erreurs internes du compilateur)](/cpp/build/reference/errorreport-report-internal-compiler-errors).

- **ExceptionHandling**

   Paramètre de chaîne facultatif.

   Spécifie le modèle de gestion des exceptions à utiliser par le compilateur.

   Spécifiez l'une des valeurs suivantes, chacune d'elles correspondant à une option de ligne de commande.

  - **fausses** - *\<none>*

  - **Asynchrone**  -  **/EHa**

  - **Synchronisation**  -  **/EHsc**

  - **SyncCThrow**  -  **/EHS**

    Pour plus d’informations, consultez [/Eh (modèle de gestion des exceptions)](/cpp/build/reference/eh-exception-handling-model).

- **ExpandAttributedSource**

   Paramètre booléen facultatif.

   Si `true`, crée un fichier listing dont les attributs développés sont injectés dans le fichier source.

   Pour plus d’informations, consultez [/FX (fusionner le code injecté)](/cpp/build/reference/fx-merge-injected-code).

- **FavorSizeOrSpeed**

   Paramètre de chaîne facultatif.

   Spécifie s’il convient de privilégier la vitesse du code ou sa taille.

   Spécifiez l'une des valeurs suivantes, chacune d'elles correspondant à une option de ligne de commande.

  - **SP5** - *\<none>*

  - **Taille**  -  **/OS**

  - **Vitesse**  -  **/OT**

    Pour plus d’informations, consultez [/OS,/OT (favoriser la taille du code, favoriser la rapidité du code)](/cpp/build/reference/os-ot-favor-small-code-favor-fast-code).

- **FloatingPointExceptions**

   Paramètre booléen facultatif.

   Si `true`, active le modèle de virgule flottante fiable. Des exceptions sont levées dès leur déclenchement.

   Pour plus d’informations, consultez l’option/**FP : except** dans [/FP (spécifier le comportement de virgule flottante)](/cpp/build/reference/fp-specify-floating-point-behavior).

- **FloatingPointModel**

   Paramètre de chaîne facultatif.

   Définit le modèle de virgule flottante.

   Spécifiez l'une des valeurs suivantes, chacune d'elles correspondant à une option de ligne de commande.

  - **Précis**  -  **/FP : precise**

  - **Strict**  -  **/FP : strict**

  - **Rapide**  -  **/FP : Fast**

    Pour plus d’informations, consultez [/FP (spécifier le comportement de virgule flottante)](/cpp/build/reference/fp-specify-floating-point-behavior).

- **ForceConformanceInForLoopScope**

   Paramètre booléen facultatif.

   Si `true`, implémente un comportement C++ standard dans les boucles [for](/cpp/cpp/for-statement-cpp) utilisant les extensions Microsoft ([/Ze](/cpp/build/reference/za-ze-disable-language-extensions)).

   Pour plus d’informations, consultez [/Zc : forScope (conformité forcée dans la portée de la boucle for)](/cpp/build/reference/zc-forscope-force-conformance-in-for-loop-scope).

- **ForcedIncludeFiles**

   Paramètre `String[]` facultatif.

   Entraîne le traitement d’un ou de plusieurs fichiers d’en-tête spécifiés par le préprocesseur.

   Pour plus d’informations, consultez [/fi (nom du fichier include forcé)](/cpp/build/reference/fi-name-forced-include-file).

- **ForcedUsingFiles**

   Paramètre **String []** facultatif.

   Entraîne le traitement d’un ou de plusieurs fichiers **#using** spécifiés par le préprocesseur.

   Pour plus d’informations, consultez [/Fu (nommer le fichier #using forcé)](/cpp/build/reference/fu-name-forced-hash-using-file).

- **FunctionLevelLinking**

   Paramètre `Boolean` facultatif.

   Si `true`, permet au compilateur d’empaqueter des fonctions individuelles sous la forme de fonctions empaquetées (COMDATs).

   Pour plus d’informations, consultez [/Gy (activer la liaison au niveau des fonctions)](/cpp/build/reference/gy-enable-function-level-linking).

- **GenerateXMLDocumentationFiles**

   Paramètre `Boolean` facultatif.

   Si `true` , force le compilateur à traiter les commentaires de documentation dans les fichiers de code source et à créer un fichier *. XDC* pour chaque fichier de code source qui contient des commentaires de documentation.

   Pour plus d’informations, consultez [/doc (traiter les commentaires de documentation) (C/C++)](/cpp/build/reference/doc-process-documentation-comments-c-cpp). Consultez également le paramètre **XMLDocumentationFileName** dans ce tableau.

- **IgnoreStandardIncludePath**

   Paramètre `Boolean` facultatif.

   Si `true`, empêche le compilateur de rechercher des fichiers include dans les répertoires spécifiés dans les variables d’environnement PATH et INCLUDE.

   Pour plus d’informations, consultez [/x (ignorer les chemins d’accès Include standard)](/cpp/build/reference/x-ignore-standard-include-paths).

- **InlineFunctionExpansion**

   Paramètre de **chaîne** facultatif.

   Spécifie le niveau d’expansion des fonctions inline pour la génération.

   Spécifiez l'une des valeurs suivantes, chacune d'elles correspondant à une option de ligne de commande.

  - **Valeurs** - *\<none>*

  - **Désactivé**  -  **/Ob0**

  - **OnlyExplicitInline**  -  **/Ob1**

  - **AnySuitable**  -  **/OB2**

    Pour plus d’informations, consultez [/ob (expansion des fonctions inline)](/cpp/build/reference/ob-inline-function-expansion).

- **IntrinsicFunctions**

   Paramètre `Boolean` facultatif.

   Si `true`, remplace certains appels de fonction par une forme intrinsèque ou par d’autres formes spéciales de la fonction qui contribuent à une exécution plus rapide de votre application.

   Pour plus d’informations, consultez [/Oi (générer des fonctions intrinsèques)](/cpp/build/reference/oi-generate-intrinsic-functions).

- **MinimalRebuild**

   Paramètre `Boolean` facultatif.

   Si `true`, permet une régénération minimale, qui détermine si les fichiers sources C++ qui incluent des définitions de classe C++ modifiées (stockées dans des fichiers d’en-tête [.h]) doivent être recompilés.

   Pour plus d’informations, consultez [/GM (activer la régénération minimale)](/cpp/build/reference/gm-enable-minimal-rebuild).

- **MultiProcessorCompilation**

   Paramètre `Boolean` facultatif.

   Si `true`, utilise plusieurs processeurs pour procéder à la compilation. Ce paramètre crée un processus pour chaque processeur effectif de votre ordinateur.

   Pour plus d’informations, consultez [/MP (générer avec plusieurs processus)](/cpp/build/reference/mp-build-with-multiple-processes). Consultez également le paramètre **ProcessorNumber** dans ce tableau.

- **ObjectFileName**

   Paramètre de **chaîne** facultatif.

   Spécifie un nom de fichier objet (.obj) ou un répertoire à utiliser à la place de la valeur par défaut.

   Pour plus d’informations, consultez [/Fo (Nom de fichier objet)](/cpp/build/reference/fo-object-file-name).

- **ObjectFiles**

   Paramètre **String []** facultatif.

   Liste des fichiers objets.

- **OmitDefaultLibName**

   Paramètre `Boolean` facultatif.

   Si `true` , omet le nom par défaut de la bibliothèque Runtime C à partir du fichier objet (*. obj*). Par défaut, le compilateur place le nom de la bibliothèque dans le fichier *. obj* pour diriger l’éditeur de liens vers la bibliothèque correcte.

   Pour plus d’informations, consultez [/zl (omettre le nom de la bibliothèque par défaut)](/cpp/build/reference/zl-omit-default-library-name).

- **OmitFramePointers**

   Paramètre `Boolean` facultatif.

   Si `true`, empêche la création des pointeurs de frame sur la pile des appels.

   Pour plus d’informations, consultez [/Oy (omission du pointeur de frame)](/cpp/build/reference/oy-frame-pointer-omission).

- **OpenMPSupport**

   Paramètre `Boolean` facultatif.

   Si `true`, le compilateur traite les clauses et directives OpenMP.

   Pour plus d’informations, consultez [/openmp (activer la prise en charge d’openmp 2,0)](/cpp/build/reference/openmp-enable-openmp-2-0-support).

- **Optimisation**

   Paramètre de **chaîne** facultatif.

   Spécifie différentes optimisations de code en termes de vitesse et de taille.

   Spécifiez l'une des valeurs suivantes, chacune d'elles correspondant à une option de ligne de commande.

  - **Désactivé**  -  **/OD**

  - **MinSpace**  -  **/O1**

  - **Maxspeed**  -  **/O2**

  - **Plein**  -  **/Ox**

    Pour plus d’informations, consultez [/O, options (Optimiser le code)](/cpp/build/reference/o-options-optimize-code).

- **PrecompiledHeader**

   Paramètre de **chaîne** facultatif.

   Créez ou utilisez un fichier d’en-tête précompilé (*. pch*) au cours de la génération.

   Spécifiez l'une des valeurs suivantes, chacune d'elles correspondant à une option de ligne de commande.

  - **NotUsing** - *\<none>*

  - **Créer**  -  **/Yc**

  - **Utilisez**  -  **/Yu**

    Pour plus d’informations, consultez [/Yc (créer un fichier d’en-tête précompilé)](/cpp/build/reference/yc-create-precompiled-header-file) et [/Yu (utiliser un fichier d’en-tête précompilé)](/cpp/build/reference/yu-use-precompiled-header-file). Consultez également les paramètres **PrecompiledHeaderFile** et **PrecompiledHeaderOutputFile** dans ce tableau.

- **PrecompiledHeaderFile**

   Paramètre de **chaîne** facultatif.

   Spécifie un nom de fichier d’en-tête précompilé à créer ou utiliser.

   Pour plus d’informations, consultez [/Yc (créer un fichier d’en-tête précompilé)](/cpp/build/reference/yc-create-precompiled-header-file) et [/Yu (utiliser un fichier d’en-tête précompilé)](/cpp/build/reference/yu-use-precompiled-header-file).

- **PrecompiledHeaderOutputFile**

   Paramètre de **chaîne** facultatif.

   Spécifie un nom de chemin d’accès pour un en-tête précompilé au lieu d’utiliser le nom du chemin d’accès par défaut.

   Pour plus d’informations, consultez [/FP (nom de fichier. pch)](/cpp/build/reference/fp-name-dot-pch-file).

- **PreprocessKeepComments**

   Paramètre `Boolean` facultatif.

   Si `true`, conserve les commentaires pendant le prétraitement.

   Pour plus d’informations, consultez [/c (conserver les commentaires pendant le prétraitement)](/cpp/build/reference/c-preserve-comments-during-preprocessing).

- **PreprocessorDefinitions**

   Paramètre `String[]` facultatif.

   Définit un symbole de prétraitement pour votre fichier source.

   Pour plus d’informations, consultez [/d (définitions de préprocesseur)](/cpp/build/reference/d-preprocessor-definitions).

- **PreprocessOutput**

   Paramètre `ITaskItem[]` facultatif.

   Définit un tableau d’éléments de sortie de préprocesseur pouvant être consommés et émis par des tâches.

- **PreprocessOutputPath**

   Paramètre `String` facultatif.

   Spécifie le nom du fichier de sortie dans lequel le paramètre **PreprocessToFile** écrit la sortie prétraitée.

   Pour plus d’informations, consultez [/fi (prétraiter le nom du fichier de sortie)](/cpp/build/reference/fi-preprocess-output-file-name).

- **PreprocessSuppressLineNumbers**

   Paramètre `Boolean` facultatif.

   Si `true`, prétraite les fichiers sources C et C++ et copie les fichiers prétraités sur le périphérique de sortie standard.

   Pour plus d’informations, consultez [/EP (Prétraiter dans stdout sans directives #line)](/cpp/build/reference/ep-preprocess-to-stdout-without-hash-line-directives).

- **PreprocessToFile**

   Paramètre `Boolean` facultatif.

   Si `true`, prétraite les fichiers sources C et C++ et copie la sortie prétraitée dans un fichier.

   Pour plus d’informations, consultez [/p (Prétraiter dans un fichier)](/cpp/build/reference/p-preprocess-to-a-file).

- **ProcessorNumber**

   Paramètre `Integer` facultatif.

   Spécifie le nombre maximal de processeurs à utiliser dans une compilation multiprocesseur. Utilisez ce paramètre conjointement avec le paramètre **MultiProcessorCompilation**.

- **ProgramDataBaseFileName**

   Paramètre `String` facultatif.

   Spécifie un nom pour le fichier de base de données du programme (PDB).

   Pour plus d’informations, consultez [/FD (nom de fichier de la base de données du programme)](/cpp/build/reference/fd-program-database-file-name).

- **RuntimeLibrary**

   Paramètre `String` facultatif.

   Indique si un module multithread est une DLL et sélectionne les versions retail ou debug de la bibliothèque runtime.

   Spécifiez l'une des valeurs suivantes, chacune d'elles correspondant à une option de ligne de commande.

  - **Multithread**  -  **/MT**

  - **MultiThreadedDebug**  -  **/MTD**

  - **MultiThreadedDLL**  -  **/MD**

  - **MultiThreadedDebugDLL**  -  **/MDD**

    Pour plus d’informations, consultez [/MD,/MT,/LD (utiliser la bibliothèque Runtime)](/cpp/build/reference/md-mt-ld-use-run-time-library).

- **RuntimeTypeInfo**

   Paramètre `Boolean` facultatif.

   Si `true`, ajoute le code pour vérifier les types d’objet C++ à l’exécution (informations de type au moment de l’exécution).

   Pour plus d’informations, consultez [/gr (activer les informations de type au moment de l’exécution)](/cpp/build/reference/gr-enable-run-time-type-information).

- **ShowIncludes**

   Paramètre `Boolean` facultatif.

   Si `true`, le compilateur sort la liste des fichiers include.

   Pour plus d’informations, consultez [/showIncludes (liste des fichiers Include)](/cpp/build/reference/showincludes-list-include-files).

- **SmallerTypeCheck**

   Paramètre `Boolean` facultatif.

   Si `true`, signale une erreur d’exécution si une valeur est affectée à un type de données inférieur et provoque une perte de données.

   Pour plus d’informations, consultez l’option **/RTCc** dans [/RTC (vérifications des erreurs au moment de l’exécution)](/cpp/build/reference/rtc-run-time-error-checks).

- **Sources**

   Paramètre `ITaskItem[]` requis.

   Spécifie la liste des fichiers sources séparés par des espaces.

- **StringPooling**

   Paramètre `Boolean` facultatif.

   Si `true`, permet au compilateur de créer une copie de chaînes identiques dans l’image du programme.

   Pour plus d’informations, consultez [/GF (éliminer les chaînes dupliquées)](/cpp/build/reference/gf-eliminate-duplicate-strings).

- **StructMemberAlignment**

   Paramètre `String` facultatif.

   Spécifie l’alignement des octets pour tous les membres d’une structure.

   Spécifiez l'une des valeurs suivantes, chacune d'elles correspondant à une option de ligne de commande.

  - **Par défaut**  -  **/Zp1**

  - **1Byte**  -  **/Zp1**

  - **2Bytes**  -  **/ZP2**

  - **4Bytes**  -  **/Zp4**

  - **8Bytes**  -  **/Zp8**

  - **16Bytes**  -  **/Zp16**

    Pour plus d’informations, consultez [/Zp (alignement des membres de la structure)](/cpp/build/reference/zp-struct-member-alignment).

- **SuppressStartupBanner**

   Paramètre `Boolean` facultatif.

   Si la valeur est `true`, empêche l'affichage du message de copyright et de numéro de version quand la tâche démarre.

   Pour plus d’informations, consultez [/nologo (supprimer la bannière de démarrage) (C/C++)](/cpp/build/reference/nologo-suppress-startup-banner-c-cpp).

- **TrackerLogDirectory**

   Paramètre `String` facultatif.

   Spécifie le répertoire intermédiaire dans lequel sont stockés les fichiers journaux de suivi de cette tâche.

   Pour plus d’informations, consultez les paramètres **TLogReadFiles** et **TLogWriteFiles** dans ce tableau.

- **TreatSpecificWarningsAsErrors**

   Paramètre **String []** facultatif.

   Traite la liste spécifiée des avertissements du compilateur comme des erreurs.

   Pour plus d’informations, consultez l’option **/We** `n` dans [/W,/W0,/W1,/W2,/W3,/W4,/W1,/W2,/W3,/W4,/Wall,/WD,/we,/WO,/WV,/WX (niveau d’avertissement)](/cpp/build/reference/compiler-option-warning-level).

- **TreatWarningAsError**

   Paramètre `Boolean` facultatif.

   Si `true`, considère tous les avertissements du compilateur comme des erreurs.

   Pour plus d’informations, consultez l’option **/WX** dans [/w,/W0,/W1,/W2,/W3,/W4,/W1,/W2,/W3,/W4,/Wall,/WD,/we,/WO,/WV,/WX (niveau d’avertissement)](/cpp/build/reference/compiler-option-warning-level).

- **TreatWChar_tAsBuiltInType**

   Paramètre `Boolean` facultatif.

   Si `true`, considère le type `wchar_t` comme un type natif.

   Pour plus d’informations, consultez [/Zc : wchar_t (wchar_t est un type natif)](/cpp/build/reference/zc-wchar-t-wchar-t-is-native-type).

- **UndefineAllPreprocessorDefinitions**

   Paramètre `Boolean` facultatif.

   Si `true`, annule la définition des symboles propres à Microsoft que le compilateur définit.

   Pour plus d’informations, consultez l’option **/u** dans [/u,/u (annuler la définition des symboles)](/cpp/build/reference/u-u-undefine-symbols).

- **UndefinePreprocessorDefinitions**

   Paramètre `String[]` facultatif.

   Indique une liste d’un ou de plusieurs symboles de préprocesseur dont la définition va être annulée.

   Pour plus d’informations, consultez l’option **/u** dans [/u,/u (annuler la définition des symboles)](/cpp/build/reference/u-u-undefine-symbols).

- **UseFullPaths**

   Paramètre `Boolean` facultatif.

   Si `true`, affiche le chemin d’accès complet des fichiers de code source transmis au compilateur dans les diagnostics.

   Pour plus d’informations, consultez [/FC (chemin d’accès complet du fichier de code source dans les Diagnostics)](/cpp/build/reference/fc-full-path-of-source-code-file-in-diagnostics).

- **UseUnicodeForAssemblerListing**

   Paramètre `Boolean` facultatif.

   Si `true`, entraîne la création du fichier de sortie au format UTF-8.

   Pour plus d’informations, consultez l’option **/FAu** dans [/FA,/FA (fichier listing)](/cpp/build/reference/fa-fa-listing-file).

- **WarningLevel**

   Paramètre `String` facultatif.

   Spécifie le niveau d’avertissement le plus élevé devant être généré par le compilateur.

   Spécifiez l'une des valeurs suivantes, chacune d'elles correspondant à une option de ligne de commande.

  - **TurnOffAllWarnings**  -  **/W0**

  - **Niveau1**  -  **/W1**

  - **D’isolement2**  -  **/W2**

  - **Niveau3**  -  **/W3**

  - **Level4**  -  **/W4**

  - **Activer**  -  **/Wall**

    Pour plus d’informations, consultez l’option **/w**_n_ dans [/w,/W0,/W1,/W2,/W3,/W4,/W1,/W2,/W3,/W4,/Wall,/WD,/we,/WO,/WV,/WX (niveau d’avertissement)](/cpp/build/reference/compiler-option-warning-level).

- **WholeProgramOptimization**

   Paramètre `Boolean` facultatif.

   Si `true`, active l’optimisation de l’ensemble du programme.

   Pour plus d’informations, consultez [/GL (optimisation de l’ensemble du programme)](/cpp/build/reference/gl-whole-program-optimization).

- **XMLDocumentationFileName**

   Paramètre `String` facultatif.

   Spécifie le nom des fichiers de documentation XML générés. Ce paramètre peut être un nom de fichier ou de répertoire.

   Pour plus d’informations, consultez l' `name` argument dans [/doc (traiter les commentaires de documentation) (C/C++)](/cpp/build/reference/doc-process-documentation-comments-c-cpp). Consultez également le paramètre **GenerateXMLDocumentationFiles** dans ce tableau.

- **MinimalRebuildFromTracking**

   Paramètre `Boolean` facultatif.

   Si `true`, une génération incrémentielle suivie est exécutée ; si `false`, une régénération est exécutée.

- **TLogReadFiles**

   Paramètre `ITaskItem[]` facultatif.

   Spécifie un tableau des éléments qui représentent les *journaux de suivi des fichiers lus*.

   Un journal de suivi des fichiers lus (*. TLog*) contient les noms des fichiers d’entrée qui sont lus par une tâche et est utilisé par le système de génération de projet pour prendre en charge les builds incrémentielles. Pour plus d’informations, consultez les paramètres **TrackerLogDirectory** et **TrackFileAccess** dans ce tableau.

- **TLogWriteFiles**

   Paramètre `ITaskItem[]` facultatif.

   Spécifie un tableau des éléments qui représentent les *journaux de suivi des fichiers écrits*.

   Un journal de suivi des fichiers d’écriture (*. TLog*) contient les noms des fichiers de sortie écrits par une tâche, et est utilisé par le système de génération de projet pour prendre en charge les builds incrémentielles. Pour plus d’informations, consultez les paramètres **TrackerLogDirectory** et **TrackFileAccess** dans ce tableau.

- **TrackFileAccess**

   Paramètre `Boolean` facultatif.

   Si `true`, effectue le suivi des modèles d’accès au fichier.

   Pour plus d’informations, consultez les paramètres **TLogReadFiles** et **TLogWriteFiles** dans ce tableau.

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur les tâches](../msbuild/msbuild-task-reference.md)
