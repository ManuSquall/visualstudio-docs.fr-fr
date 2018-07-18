---
title: Propriétés du projet Clang (Android C++) | Microsoft Docs
ms.custom: ''
ms.date: 10/23/2017
ms.technology: vs-ide-mobile
ms.topic: conceptual
ms.assetid: 663140ea-a568-472b-a79a-dfea8818e06a
author: corob
ms.author: mblome
manager: douge
f1_keywords:
- VC.Project.VCClangCompilerTool.AdditionalIncludeDirectories
- VC.Project.VCClangCompilerTool.DebugInformationFormat
- VC.Project.VCClangCompilerTool.ObjectFile
- VC.Project.VCClangCompilerTool.WarningLevel
- VC.Project.VCClangCompilerTool.WarnAsError
- VC.Project.VCClangCompilerTool.Verbose
- VC.Project.VCClangCompilerTool.Optimization
- VC.Project.VCClangCompilerTool.StrictAliasing
- VC.Project.VCClangCompilerTool.OmitFramePointers
- VC.Project.VCClangCompilerTool.ExceptionHandling
- VC.Project.VCClangCompilerTool.EnableFunctionLevelLinking
- VC.Project.VCClangCompilerTool.DataLevelLinking
- VC.Project.VCClangCompilerTool.DataLevelLinking
- VC.Project.VCClangCompilerTool.FloatABI
- VC.Project.VCClangCompilerTool.BufferSecurityCheck
- VC.Project.VCClangCompilerTool.PIC
- VC.Project.VCClangCompilerTool.UseShortEnums
- VC.Project.VCClangCompilerTool.RuntimeTypeInfo
- VC.Project.VCClangCompilerTool.CLanguageStandard
- VC.Project.VCClangCompilerTool.CppLanguageStandard
- VC.Project.VCClangCompilerTool.PreprocessorDefinitions
- VC.Project.VCClangCompilerTool.UndefinePreprocessorDefinitions
- VC.Project.VCClangCompilerTool.UndefineAllPreprocessorDefinitions
- VC.Project.VCClangCompilerTool.ShowIncludes
- VC.Project.VCClangCompilerTool.PrecompiledHeader
- VC.Project.VCClangCompilerTool.PrecompiledHeaderFile
- VC.Project.VCClangCompilerTool.PrecompiledHeaderOutputFileDirectory
- VC.Project.VCClangCompilerTool.PrecompiledHeaderCompileAs
- VC.Project.VCClangCompilerTool.CompileAs
- VC.Project.VCClangCompilerTool.ForcedIncludeFiles
- VC.Project.VCClangCompilerTool.MultiProcessorCompilation
- vc.project.AdditionalOptionsPage
ms.workload:
- xplat-cplusplus
ms.openlocfilehash: 8a1fd92a41f145e097615bea4434ea80fd592416
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31067530"
---
# <a name="clang-project-properties-android-c"></a>Propriétés du projet Clang (Android C++)

Propriété | Description | Options
--- | ---| ---
Autres répertoires Include | Spécifie un ou plusieurs répertoires à ajouter au chemin include. Si vous ajoutez plusieurs répertoires, séparez-les par des points-virgules. (-I[path]).
Format des informations de débogage | Indique le type d'informations de débogage générées par le compilateur. | **Aucune** : ne génère aucune information de débogage ; la compilation peut donc être plus rapide.<br>**Informations de débogage complètes (DWARF2)** : générez des informations de débogage DWARF2.<br>**Informations de numéro de ligne** : générez uniquement des informations de numéro de ligne.<br>
Nom de fichier objet | Spécifie un nom de substitution pour le nom de fichier objet par défaut. Il peut s’agir d’un nom de fichier ou de répertoire. (/Fo[name]).
Niveau d’avertissement | Sélectionnez la rigueur avec laquelle le compilateur doit traiter les erreurs de code.  D’autres indicateurs doivent être ajoutés directement dans les options supplémentaires. (/w, /Weverything). | **Désactiver tous les avertissements** : désactive tous les avertissements du compilateur.<br>**Activer tous les avertissements** : active tous les avertissements, dont ceux qui sont désactivés par défaut.<br>
Considérer les avertissements comme des erreurs | Considère tous les avertissements du compilateur comme des erreurs. Pour un nouveau projet, il est conseillé d’utiliser /WX dans toutes les compilations, car la résolution de tous les avertissements permet de réduire les erreurs de code difficilement détectables.
Activer le mode détaillé | Affichez les commandes à exécuter et utilisez la sortie détaillée.
Optimisation | Indique le niveau d’optimisation pour l’application. | **Personnalisé** : optimisation personnalisée.<br>**Désactivé** : désactive l’optimisation.<br>**Réduire la taille** : optimise la taille.<br>**Augmenter la vitesse** : optimise la vitesse.<br>**Optimisation complète** : optimisations coûteuses.<br>
Alias strict | Les règles d’alias les plus strictes sont utilisées.  Un objet d’un type ne sera jamais considéré comme résidant à la même adresse qu’un objet d’un autre type.
Omettre le pointeur de frame | Empêche la création des pointeurs de frame sur la pile des appels.
Activer les exceptions C++ | Spécifie le modèle de gestion des exceptions à utiliser par le compilateur. | **Non** : désactive la gestion des exceptions.<br>**Oui** : activez la gestion des exceptions.<br>**Tables Unwind** : génère les données statiques requises, mais n’affecte pas le code généré.<br>
Activer la liaison au niveau des fonctions | Permet au compilateur d’empaqueter des fonctions individuelles sous la forme de fonctions empaquetées (COMDATs). Requis avec l’option Modifier et Continuer.     (ffunction-sections).
Activer la liaison au niveau des données | Permet aux optimisations de l’éditeur de liens de supprimer les données inutilisées en émettant chaque élément de données dans une section séparée.
Activer Advanced SIMD (Neon) | Permet la génération de code pour le matériel NEON Floating Point. Applicable uniquement à l’architecture ARM.
Floating-point ABI | Option pour choisir Floating Point ABI. | **Soft** : avec l’option 'Soft', le compilateur génère une sortie contenant des appels de bibliothèque pour les opérations à virgule flottante.<br>**SoftFP** : 'SoftFP' autorise la génération de code avec des instructions à virgule flottante matérielle, mais utilise toujours les conventions d’appel soft-float.<br>**Hard** : 'Hard' autorise la génération d’instructions à virgule flottante et utilise les conventions d’appel spécifiques à FPU.<br>
Vérification de la sécurité | La vérification de la sécurité permet de détecter les saturations de mémoire tampon de pile, une tentative courante d’attaque contre la sécurité d’un programme. (fstack-protector). | **Désactiver la vérification de la sécurité** : désactivez la vérification de la sécurité.<br>**Activer la vérification de la sécurité** : activez la vérification de la sécurité. (fstack-protector)<br>
PIC (Position Independent Code) | Générez du code PIC (Position Independent Code) à utiliser dans une bibliothèque partagée.
Utiliser des enums courts | Un type enum utilise uniquement le nombre d’octets requis par l’ensemble des valeurs possibles d’entrée.
Activer les informations de type au moment de l’exécution | Ajoute le code permettant de vérifier les types d’objet C++ à l’exécution (informations de type au moment de l’exécution).     (frtti, fno-rtti)
Norme du langage C | Détermine la norme du langage C. | **Default**<br>**C89** : norme du langage C89.<br>**C99** : norme du langage C99.<br>**C11** : norme du langage C11.<br>**C99 (Dialecte GNU)**  : norme du langage C99 (Dialecte GNU).<br>**C11 (Dialecte GNU)**  : norme du langage C11 (Dialecte GNU).<br>
Norme du langage C++ | Détermine la norme du langage C++. | **Default**<br>**C++03** : norme du langage C++03.<br>**C++11** : norme du langage C++11.<br>**C++14** : norme du langage C++14.<br>**C++03 (Dialecte GNU)**  : norme du langage C++03 (Dialecte GNU).<br>**C++11 (Dialecte GNU)**  : norme du langage C++11 (Dialecte GNU).<br>**C++14 (Dialecte GNU)**  : norme du langage C++14 (Dialecte GNU).<br>
Définitions de préprocesseur | Définit des symboles de prétraitement pour votre fichier source. (-D)
Annuler la définition de définitions de préprocesseur | Spécifie l’annulation de la définition d’une ou de plusieurs définitions du préprocesseur.  (-U [macro])
Annulation de la définition de toutes les définitions du préprocesseur | Annule la définition de toutes les valeurs de préprocesseur précédemment définies.  (-undef)
Affichage des fichiers Include | Affiche la liste des fichiers include avec les résultats de la compilation.  (-H)
En-tête précompilé | Créer/utiliser un en-tête précompilé : active la création ou l’utilisation d’un en-tête précompilé durant la génération. | **Utiliser** : utilisez un en-tête précompilé.<br>**Sans utiliser les en-têtes précompilés** : n’utilise pas un en-tête précompilé.<br>
Fichier d’en-tête précompilé | Spécifie le nom du fichier d’en-tête à utiliser pour le fichier d’en-tête précompilé. Ce fichier est également ajouté aux Fichiers Include forcés durant la génération
Répertoire du fichier d’en-tête précompilé de sortie | Spécifie le répertoire de l’en-tête précompilé généré. Ce répertoire est également ajouté aux Autres répertoires Include durant la génération
Compiler l’en-tête précompilé comme | Sélectionnez l’option de langage de compilation pour le fichier d’en-tête précompilé (-x c-header, -x c++-header). | **Compiler en code C** : compilez en code C.<br>**Compiler en code C++** : compilez en code C++.<br>
Compiler en | Permet de sélectionner l’option de langage de compilation pour les fichiers .c et .cpp.  'Default' effectue la détection d’après l’extension (.c ou .cpp). (-x c, -x c++) | **Par défaut** : option par défaut.<br>**Compiler en code C** : compile en code C.<br>**Compiler en code C++**  : compile en code C++.<br>
Fichiers Include forcés | un ou plusieurs fichiers Include forcés.     (-include [name])
Compilation multiprocesseur | Compilation multiprocesseur.
Options supplémentaires | Options supplémentaires.
