---
title: Tâche ClangCompile | Microsoft Docs
ms.date: 03/10/2019
ms.topic: reference
f1_keywords:
- vc.task.clangcompile
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (C++), ClangCompile task
- ClangCompile task (MSBuild (C++))
author: corob-msft
ms.author: corob
ms.workload:
- multiple
ms.openlocfilehash: c1526fbd3c2c0822781f0e011999ddcb9c679170
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/15/2020
ms.locfileid: "77275467"
---
# <a name="clangcompile-task"></a>Tâche ClangCompile

Encapsule l’outil C++ compilateur Microsoft, Clang. exe.

## <a name="parameters"></a>Paramètres

Le tableau ci-dessous décrit les paramètres de la tâche **ClangCompile**.

|Paramètre|Description|
|---------------|-----------------|
|**AdditionalIncludeDirectories**|Paramètre de **chaîne[]** facultatif.<br/><br/>Spécifie un ou plusieurs répertoires à ajouter au chemin Include, séparés par des points-virgules s’il en existe plusieurs.<br/><br/>Utilisez `-I[path]`.|
|**AdditionalOptions**|Paramètre de **chaîne** facultatif.|
|**BufferSecurityCheck**|Paramètre de **chaîne** facultatif.<br/><br/>La vérification de la sécurité permet de détecter les saturations de mémoire tampon de pile, une tentative courante d’attaque contre la sécurité d’un programme. <br/><br/>Utilisez `fstack-protector`.|
|**BuildingInIDE**|Paramètre **booléen** facultatif.|
|**CLanguageStandard**|Paramètre de **chaîne** facultatif.<br/><br/>Détermine la norme du langage C.<br/><br/>Utilisez `std=[value]` avec la valeur **c89**, **c99**, **c11**, **gnu99** ou **gnu11**.|
|**ClangVersion**|Paramètre de **chaîne** facultatif.|
|**CompileAs**|Paramètre de **chaîne** facultatif.<br/><br/>Permet de sélectionner l’option de langage de compilation pour les fichiers .c et .cpp. « Default » effectue la détection d’après l’extension (.c ou .cpp).<br/><br/>Utilisez `-x c`, `-x c++`.|
|**CppLanguageStandard**|Paramètre de **chaîne** facultatif.<br/><br/>Détermine la norme du langage C++.<br/><br/>Utilisez `std=[value]` avec la valeur **c++98**, **c++11**, **c++1y**, **gnu++98**, **gnu++11** ou **gnu++1y**.|
|**DataLevelLinking**|Paramètre **booléen** facultatif.<br/><br/>Permet aux optimisations de l’éditeur de liens de supprimer les données inutilisées en émettant chaque élément de données dans une section séparée.|
|**DebugInformationFormat**|Paramètre de **chaîne** facultatif.<br/><br/>Indique le type d'informations de débogage générées par le compilateur.<br/><br/>**Aucune**, ne génère aucune information de débogage ; la compilation peut donc être plus rapide (utilisez `g0`).<br/>**FullDebug**, générez des informations de débogage DWARF2 (utilisez `g2 -gdwarf-2`).<br/>**LineNumber**, générez uniquement des informations de numéro de ligne (utilisez `gline-tables-only`).|
|**EnableNeonCodegen**|Paramètre **booléen** facultatif.<br/><br/>Permet la génération de code pour le matériel NEON Floating Point. Applicable uniquement à l’architecture ARM.|
|**ExceptionHandling**|Paramètre de **chaîne** facultatif.<br/><br/>Spécifie le modèle de gestion des exceptions à utiliser par le compilateur.<br/><br/>**Désactivé**, désactivez la gestion des exceptions (utilisez `fno-exceptions`).<br/>**Activé**, activez la gestion des exceptions (utilisez `fexceptions`).<br/>**Tables Unwind**, génère les données statiques requises, mais n’affecte pas le code généré (utilisez `funwind-tables`).|
|**FloatABI**|Paramètre de **chaîne** facultatif.<br/><br/>Option pour choisir Floating Point ABI.<br/><br/>**soft**, le compilateur génère une sortie contenant des appels de bibliothèque pour les opérations à virgule flottante (utilisez `mfloat-abi=soft`).<br/>**softfp**, autorise la génération de code avec des instructions à virgule flottante matérielle, mais utilise toujours les conventions d’appel soft-float (utilisez `mfloat-abi=softfp`).<br/>**hard**, autorise la génération d’instructions à virgule flottante et utilise les conventions d’appel spécifiques FPU (utilisez `mfloat-abi=hard`).|
|**ForcedIncludeFiles**|Paramètre de **chaîne[]** facultatif.<br/><br/>Un ou plusieurs fichiers Include forcés.<br/><br/>Utilisez `-include [name]`.|
|**FunctionLevelLinking**|Paramètre **booléen** facultatif.<br/><br/>Permet au compilateur d’empaqueter des fonctions individuelles sous la forme de fonctions empaquetées (COMDATs). Requis avec l’option Modifier et Continuer.<br/><br/>Utilisez `ffunction-sections`.|
|**GccToolChain**|Paramètre de **chaîne** facultatif.<br/><br/>Chemin du dossier de la chaîne d’outils Gcc.|
|**GNUMode**|Paramètre **booléen** facultatif.<br/><br/>|
|**MSCompatibility**|Paramètre **booléen** facultatif.<br/><br/>Activez la compatibilité C++ Microsoft complète.|
|**MSCompatibilityVersion**|Paramètre de **chaîne** facultatif.<br/><br/>Valeur séparée par un point, qui représente le numéro de version du compilateur Microsoft à signaler dans _MSC_VER (0 = ne pas définir (valeur par défaut)).|
|**MSExtensions**|Paramètre **booléen** facultatif.<br/><br/>Acceptez certaines constructions non standard prises en charge par le compilateur Microsoft.|
|**MSCompilerVersion**|Paramètre de **chaîne** facultatif.<br/><br/>Numéro de version du compilateur Microsoft à signaler dans _MSC_VER (0 = ne pas définir (valeur par défaut)).|
|**MSVCErrorReport**|Paramètre **booléen** facultatif.<br/><br/>Signalez les erreurs que Visual Studio peut utiliser pour analyser les informations de fichier et de ligne.|
|**ObjectFileName**|Paramètre de **chaîne** facultatif.<br/><br/>Spécifie un nom de substitution pour le nom de fichier objet par défaut. Il peut s’agir d’un nom de fichier ou de répertoire.<br/><br/>Utilisez `/Fo[name]`.|
|**OmitFramePointers**|Paramètre **booléen** facultatif.<br/><br/>Empêche la création des pointeurs de frame sur la pile des appels.|
|**Optimization**|Paramètre de **chaîne** facultatif.<br/><br/>Indique le niveau d’optimisation pour l’application.<br/><br/>**Personnalisé**, optimisation personnalisée.<br/>**Désactivé**, désactivez l’optimisation (utilisez `O0`).<br/>**MinSize**, optimisez la taille (utilisez `Os`).<br/>**MaxSpeed**, optimisez la vitesse (utilisez `O2`).<br/>**Complet**, optimisations coûteuses (utilisez `O3`).|
|**PositionIndependentCode**|Paramètre **booléen** facultatif.<br/><br/>Générez du code PIC (Position Independent Code) à utiliser dans une bibliothèque partagée.|
|**PrecompiledHeader**|Paramètre de **chaîne** facultatif.<br/><br/>Active la création ou l’utilisation d’un en-tête précompilé pendant la génération.|
|**PrecompiledHeaderFile**|Paramètre de **chaîne** facultatif.<br/><br/>Spécifie le nom du fichier d’en-tête à utiliser pour le fichier d’en-tête précompilé. Ce fichier est également ajouté aux **Fichiers Include forcés** pendant la génération.|
|**PrecompiledHeaderOutputFileDirectory**|Paramètre de **chaîne** facultatif.<br/><br/>Spécifie le répertoire de l’en-tête précompilé généré. Ce répertoire est également ajouté aux **Autres répertoires Include** pendant la génération.|
|**PrecompiledHeaderCompileAs**|Paramètre de **chaîne** facultatif.<br/><br/>Sélectionnez l’option de langage de compilation pour le fichier d’en-tête précompilé.<br/><br/>Utilisez `-x c-header`, `-x c++-header`.|
|**PreprocessorDefinitions**|Paramètre de **chaîne[]** facultatif.<br/><br/>Définit des symboles de prétraitement pour votre fichier source.<br/><br/>Utilisez `-D`.|
|**RuntimeLibrary**|Paramètre de **chaîne** facultatif.<br/><br/>Spécifiez la bibliothèque Runtime pour la liaison.<br/><br/>Utilisez les commutateurs `MSVC /MT`, `/MTd`, `/MD`, `/MDd`.<br/><br/>**MultiThreaded**, indique à votre application d’utiliser la version statique multithread de la bibliothèque Runtime.<br/>**MultiThreadedDebug**, définit _DEBUG et _MT. Cette option indique également au compilateur d'ajouter le nom de bibliothèque LIBCMTD.lib dans le fichier .obj afin que l'Éditeur de liens utilise LIBCMTD.lib pour résoudre les symboles externes.<br/>**MultiThreadedDLL**, indique à votre application d’utiliser la version spécifique au multithread et à la DLL de la bibliothèque Runtime. Définit _MT et _DLL, puis indique au compilateur de placer le nom de la bibliothèque MSVCRT.lib dans le fichier .obj.<br/>**MultiThreadedDebugDLL**, définit _DEBUG, _MT et _DLL, puis indique à votre application d’utiliser la version spécifique au multithread et à la DLL de débogage de la bibliothèque Runtime. Le compilateur place également le nom de la bibliothèque MSVCRTD.lib dans le fichier .obj.|
|**RuntimeTypeInfo**|Paramètre **booléen** facultatif.<br/><br/>Ajoute le code permettant de vérifier les types d’objet C++ à l’exécution (informations de type au moment de l’exécution).<br/><br/>Utilisez `frtti`, `fno-rtti`.|
|**ShowIncludes**|Paramètre **booléen** facultatif.<br/><br/>Affiche la liste des fichiers include avec les résultats de la compilation.<br/><br/>Utilisez `-H`.|
|**Sources**|Paramètre **ITaskItem[]** obligatoire.|
|**StrictAliasing**|Paramètre **booléen** facultatif.<br/><br/>Les règles d’alias les plus strictes sont utilisées. Un objet d’un type ne sera jamais considéré comme résidant à la même adresse qu’un objet d’un autre type.|
|**Sysroot**|Paramètre de **chaîne** facultatif.<br/><br/>Chemin du dossier vers le répertoire racine pour les en-têtes et les bibliothèques.|
|**TargetArch**|Paramètre de **chaîne** facultatif.<br/><br/>Architecture cible.|
|**ThumbMode**|Paramètre de **chaîne** facultatif.<br/><br/>Générez du code qui s’exécute pour une microarchitecture Thumb. Applicable uniquement à l’architecture ARM.<br/><br/>**Thumb**, générez du code Thumb (utilisez `mthumb`).<br/>**ARM**, générez du code Arm (utilisez `marm`).<br/>**Désactivé**, option non applicable à la plateforme choisie.|
|**TrackerLogDirectory**|Paramètre de **chaîne** facultatif.<br/><br/>Répertoire des journaux de suivi.|
|**TreatWarningAsError**|Paramètre **booléen** facultatif.<br/><br/>Considère tous les avertissements du compilateur comme des erreurs.<br/><br/>Pour un nouveau projet, il est conseillé d’utiliser `/WX` dans toutes les compilations, car la résolution de tous les avertissements permet de réduire les erreurs de code difficilement détectables.|
|**UndefinePreprocessorDefinitions**|Paramètre de **chaîne[]** facultatif.<br/><br/>Spécifie l’annulation de la définition d’une ou de plusieurs définitions du préprocesseur.<br/><br/>Utilisez `-U [macro]`.|
|**UndefineAllPreprocessorDefinitions**|Paramètre **booléen** facultatif.<br/><br/>Annule la définition de toutes les valeurs de préprocesseur précédemment définies.<br/><br/>Utilisez `-undef`.|
|**UseMultiToolTask**|Paramètre **booléen** facultatif.<br/><br/>Compilation multiprocesseur.|
|**UseShortEnums**|Paramètre **booléen** facultatif.<br/><br/>Un type enum utilise uniquement le nombre d’octets requis par l’ensemble des valeurs possibles d’entrée.|
|**Verbose**|Paramètre **booléen** facultatif.<br/><br/>Affichez les commandes à exécuter et utilisez la sortie détaillée.|
|**WarningLevel**|Paramètre de **chaîne** facultatif.<br/><br/>Sélectionnez la rigueur avec laquelle le compilateur doit traiter les erreurs de code. D’autres indicateurs doivent être ajoutés directement dans les **Options supplémentaires** (voir `/w`, `/Weverything`).<br/><br/>**TurnOffAllWarnings**, désactive tous les avertissements du compilateur (utilisez `w`).<br/>**EnableAllWarnings**, active tous les avertissements, dont ceux qui sont désactivés par défaut (utilisez `Wall`).|

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les tâches](../msbuild/msbuild-task-reference.md)