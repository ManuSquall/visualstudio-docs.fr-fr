---
title: Tâche CL | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
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
- MSBuild (Visual C++), CL task
- CL task (MSBuild (Visual C++))
ms.assetid: 651ba971-b755-4f03-a549-4816beb3cc0d
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f6035e9024b7c81d3d9d5fc7b4d482aa2aae7c06
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49844716"
---
# <a name="cl-task"></a>CL, tâche
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Encapsule l’outil Compilateur Visual C++, cl.exe. Le compilateur produit des fichiers exécutables (.exe), des fichiers de bibliothèque de liens dynamiques (.dll) ou des fichiers de module de code (.netmodule). Pour plus d’informations, consultez l’article [Options du compilateur](http://msdn.microsoft.com/library/ed3376c8-bef4-4c9a-80e9-3b5da232644c).  
  
## <a name="parameters"></a>Paramètres  
 Le tableau ci-dessous décrit les paramètres de la tâche **CL**. La plupart des paramètres de tâche, et quelques ensembles de paramètres, correspondent à une option de ligne de commande.  
  
- **AdditionalIncludeDirectories**  
  
   Paramètre String[] facultatif.  
  
   Ajoute un répertoire à la liste des répertoires dans lesquels sont recherchés les fichiers include.  
  
   Pour plus d’informations, consultez l’article [/I (Autres répertoires Include)](http://msdn.microsoft.com/library/3e9add2a-5ed8-4d15-ad79-5b411e313a49).  
  
- **AdditionalOptions**  
  
   Paramètre de chaîne facultatif.  
  
   Liste des options de ligne de commande. Exemple : « /*option1* /*option2* /*option#*  ». Utilisez ce paramètre pour spécifier des options de ligne de commande qui ne sont pas représentées par un autre paramètre de tâche.  
  
   Pour plus d’informations, consultez l’article [Options du compilateur](http://msdn.microsoft.com/library/ed3376c8-bef4-4c9a-80e9-3b5da232644c).  
  
- **AdditionalUsingDirectories**Paramètre String[] facultatif.  
  
   Spécifie un répertoire dans lequel le compilateur doit faire une recherche en vue de résoudre les références de fichiers transmises à la directive **#using**.  
  
   Pour plus d’informations, consultez l’article [/AI (Spécifier les répertoires des métadonnées)](http://msdn.microsoft.com/library/fb9c1846-504c-4a3b-bb39-c8696de32f6f).  
  
- **AlwaysAppend**  
  
   Paramètre de chaîne facultatif.  
  
   Chaîne qui toujours est émise sur la ligne de commande. Sa valeur par défaut est «  **/c** ».  
  
- **AssemblerListingLocation**  
  
   Crée un fichier listing qui contient le code de l’assembly.  
  
   Pour plus d’informations, consultez l’option **/Fa** dans l’article [/FA, /Fa (Fichier listing)](http://msdn.microsoft.com/library/c7507d0e-c69d-44f9-b8e2-d2c398697402).  
  
- **AssemblerOutput**  
  
   Paramètre de chaîne facultatif.  
  
   Crée un fichier listing qui contient le code de l’assembly.  
  
   Spécifiez l'une des valeurs suivantes, chacune d'elles correspondant à une option de ligne de commande.  
  
  - **NoListing** - *\<aucun>*  
  
  - **AssemblyCode** - **/FA**  
  
  - **AssemblyAndMachineCode** - **/FAc**  
  
  - **AssemblyAndSourceCode** - **/FAs**  
  
  - **All** - **/FAcs**  
  
    Pour plus d’informations, consultez les options **/FA**, **/FAc**, **/FAs** et **/FAcs** dans l’article [/FA, /Fa (Fichier listing)](http://msdn.microsoft.com/library/c7507d0e-c69d-44f9-b8e2-d2c398697402).  
  
- **BasicRuntimeChecks**  
  
   Paramètre de chaîne facultatif.  
  
   Active et désactive la fonctionnalité de vérification des erreurs d’exécution, conjointement avec le pragma [runtime_checks](http://msdn.microsoft.com/library/ae50b43f-f88d-47ad-a2db-3389e9e7df5b).  
  
   Spécifiez l'une des valeurs suivantes, chacune d'elles correspondant à une option de ligne de commande.  
  
  - **Default** -                          *\<aucune>*  
  
  - **StackFrameRuntimeCheck** - **/RTCs**  
  
  - **UninitializedLocalUsageCheck** - **/RTCu**  
  
  - **EnableFastChecks** -                          **/RTC1**  
  
    Pour plus d’informations, consultez l’article [/RTC (Vérifications des erreurs au moment de l’exécution)](http://msdn.microsoft.com/library/9702c558-412c-4004-acd5-80761f589368).  
  
- **BrowseInformation**  
  
   Paramètre booléen facultatif.  
  
   Si `true`, crée un fichier d’informations de consultation.  
  
   Pour plus d’informations, consultez l’option **/FR** dans l’article [/FR, /Fr (Créer un fichier .sbr)](http://msdn.microsoft.com/library/3fd8f88b-3924-4feb-9393-287036a28896).  
  
- **BrowseInformationFile**  
  
   Paramètre de chaîne facultatif.  
  
   Spécifie un nom pour le fichier d’informations de consultation.  
  
   Pour plus d’informations, consultez le paramètre **BrowseInformation** dans ce tableau ainsi que l’article [/FR, /Fr (Créer un fichier .sbr)](http://msdn.microsoft.com/library/3fd8f88b-3924-4feb-9393-287036a28896).  
  
- **BufferSecurityCheck**  
  
   Paramètre booléen facultatif.  
  
   Si `true`, détecte des dépassements de mémoire tampon qui remplacent l’adresse de retour, une technique courante pour exploiter le code qui n’applique pas les restrictions de taille de la mémoire tampon.  
  
   Pour plus d’informations, consultez l’article [/GS (vérification de la sécurité des mémoires tampons)](http://msdn.microsoft.com/library/8d8a5ea1-cd5e-42e1-bc36-66e1cd7e731e).  
  
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
  
    Pour plus d’informations, voir l’article [/Gd, /Gr, /Gv, /Gz (Convention d’appel)](http://msdn.microsoft.com/library/fd3110cb-2d77-49f2-99cf-a03f9ead00a3).  
  
- **CompileAs**  
  
   Paramètre de chaîne facultatif.  
  
   Spécifie s’il convient de compiler le fichier d’entrée en tant que fichier source C ou C++.  
  
   Spécifiez l'une des valeurs suivantes, chacune d'elles correspondant à une option de ligne de commande.  
  
  - **Default** - *\<aucune>*  
  
  - **CompileAsC** - **/TC**  
  
  - **CompileAsCpp** - **/TP**  
  
    Pour plus d’informations, consultez l’article [/Tc, /Tp, /TC, /TP (Spécifier le type de fichier source)](http://msdn.microsoft.com/library/7d9d0a65-338b-427c-8b48-fff30e2f9d2b).  
  
- **CompileAsManaged**  
  
   Paramètre de chaîne facultatif.  
  
   Permet aux applications et aux composants d’utiliser les fonctionnalités du Common Language Runtime (CLR).  
  
   Spécifiez l'une des valeurs suivantes, chacune d'elles correspondant à une option de ligne de commande.  
  
  - **false** - *\<aucune>*  
  
  - **true** - **/clr**  
  
  - **Pure** - **/clr:pure**  
  
  - **Safe** - **/clr:safe**  
  
  - **OldSyntax** - **/clr:oldSyntax**  
  
    Pour plus d’informations, consultez l’article [/clr (Compilation pour le Common Language Runtime)](http://msdn.microsoft.com/library/fec5a8c0-40ec-484c-a213-8dec918c1d6c).  
  
- **CreateHotpatchableImage**  
  
   Paramètre booléen facultatif.  
  
   Si `true`, indique au compilateur de préparer une image pour la *création d’images corrigeables en mémoire*. Ce paramètre vérifie que la première instruction de chaque fonction utilise deux octets, comme cela est requis pour la création d’images corrigeables en mémoire.  
  
   Pour plus d’informations, consultez l’article [/hotpatch (Créer une image corrigeable en mémoire)](http://msdn.microsoft.com/library/aad539b6-c053-4c78-8682-853d98327798).  
  
- **DebugInformationFormat**  
  
   Paramètre de chaîne facultatif.  
  
   Sélectionne le type d’informations de débogage créées pour votre programme et spécifie si ces informations doivent être conservées dans des fichiers objets (.obj) ou dans une base de données de programme (PDB).  
  
   Spécifiez l'une des valeurs suivantes, chacune d'elles correspondant à une option de ligne de commande.  
  
  - **OldStyle** - **/Z7**  
  
  - **ProgramDatabase** - **/Zi**  
  
  - **EditAndContinue** - **/ZI**  
  
    Pour plus d’informations, consultez l’article [/Z7, /Zi, /ZI (Format des informations de débogage)](http://msdn.microsoft.com/library/ce9fa7e1-0c9b-47e3-98ea-26d1a16257c8).  
  
- **DisableLanguageExtensions**  
  
   Paramètre booléen facultatif.  
  
   Si **true**, indique au compilateur d’émettre une erreur pour les constructions de langage qui ne sont compatibles ni avec ANSI C ni avec ANSI C++.  
  
   Pour plus d’informations, consultez l’option **/Za** dans l’article [/Za, /Ze (Désactiver les extensions de langage)](http://msdn.microsoft.com/library/65e49258-7161-4289-a176-7c5c0656b1a2).  
  
- **DisableSpecificWarnings**  
  
   Paramètre String[] facultatif.  
  
   Désactive les numéros d’avertissement spécifiés dans une liste séparée par des points-virgules.  
  
   Pour plus d’informations, consultez l’option `/wd` dans l’article [/w, /W0, /W1, /W2, /W3, /W4, /w1, /w2, /w3, /w4, /Wall, /wd, /we, /wo, /Wv, /WX (Niveau d’avertissement)](http://msdn.microsoft.com/library/d6bc7bf5-c754-4879-909c-8e3a67e2629f).  
  
- **EnableEnhancedInstructionSet**  
  
   Paramètre de chaîne facultatif.  
  
   Spécifie l’architecture de génération de code qui utilise les instructions des extensions Streaming SIMD (SSE) et des extensions Streaming SIMD 2 (SSE2).  
  
   Spécifiez l'une des valeurs suivantes, chacune d'elles correspondant à une option de ligne de commande.  
  
  - **StreamingSIMDExtensions** - **/arch:SSE**  
  
  - **StreamingSIMDExtensions2** - **/arch:SSE2**  
  
    Pour plus d’informations, consultez l’article [/arch (x86)](http://msdn.microsoft.com/library/9dd5a75d-06e4-4674-aade-33228486078d).  
  
- **EnableFiberSafeOptimizations**  
  
   Paramètre booléen facultatif.  
  
   Si `true`, prend en charge la sécurité des fibres pour les données allouées en utilisant un stockage local des threads de type statique, autrement dit les données allouées en utilisant `__declspec(thread)`.  
  
   Pour plus d’informations, consultez l’article [/GT (Prendre en charge le stockage local des threads avec fibres sécurisées)](http://msdn.microsoft.com/library/071fec79-c701-432b-9970-457344133159).  
  
- **EnablePREfast**  
  
   Paramètre booléen facultatif.  
  
   Si `true`, active l’analyse du code.  
  
   Pour plus d’informations, consultez l’article [/analyze (analyse de code)](http://msdn.microsoft.com/library/81da536a-e030-4bd4-be18-383927597d08).  
  
- **ErrorReporting**  
  
   Paramètre de chaîne facultatif.  
  
   Vous permet de signaler les erreurs internes du compilateur (ICE) directement à Microsoft. Par défaut, dans les générations en mode IDE, le paramètre est **Prompt** tandis que dans les générations en mode ligne de commande, il s’agit du paramètre **Queue**.  
  
   Spécifiez l'une des valeurs suivantes, chacune d'elles correspondant à une option de ligne de commande.  
  
  - **None** - **/errorReport:none**  
  
  - **Prompt** - **/errorReport:prompt**  
  
  - **Queue** - **/errorReport:queue**  
  
  - **Send** - **/errorReport:send**  
  
    Pour plus d’informations, consultez l’article [/errorReport (Signaler les erreurs internes du compilateur)](http://msdn.microsoft.com/library/819828f8-b0a5-412c-9c57-bf822f17e667).  
  
- **ExceptionHandling**  
  
   Paramètre de chaîne facultatif.  
  
   Spécifie le modèle de gestion des exceptions à utiliser par le compilateur.  
  
   Spécifiez l'une des valeurs suivantes, chacune d'elles correspondant à une option de ligne de commande.  
  
  - **false** - *\<aucune>*  
  
  - **Async** - **/EHa**  
  
  - **Sync** - **/EHsc**  
  
  - **SyncCThrow** - **/EHs**  
  
    Pour plus d’informations, consultez l’article [/EH (Modèle de gestion des exceptions)](http://msdn.microsoft.com/library/754b916f-d206-4472-b55a-b6f1b0f2cb4d).  
  
- **ExpandAttributedSource**  
  
   Paramètre booléen facultatif.  
  
   Si `true`, crée un fichier listing dont les attributs développés sont injectés dans le fichier source.  
  
   Pour plus d’informations, consultez l’article [/Fx (Fusionner le code injecté)](http://msdn.microsoft.com/library/14f0e301-3bab-45a3-bbdf-e7ce66f20560).  
  
- **FavorSizeOrSpeed**  
  
   Paramètre de chaîne facultatif.  
  
   Spécifie s’il convient de privilégier la vitesse du code ou sa taille.  
  
   Spécifiez l'une des valeurs suivantes, chacune d'elles correspondant à une option de ligne de commande.  
  
  - **Neither** - *\<aucune>*  
  
  - **Size** - **/Os**  
  
  - **Speed** - **/Ot**  
  
    Pour plus d’informations, consultez l’article [/Os, /Ot (Favoriser la taille du code, Favoriser la vitesse du code)](http://msdn.microsoft.com/library/9a340806-fa15-4308-892c-355d83cac0f2).  
  
- **FloatingPointExceptions**  
  
   Paramètre booléen facultatif.  
  
   Si `true`, active le modèle de virgule flottante fiable. Des exceptions sont levées dès leur déclenchement.  
  
   Pour plus d’informations, consultez l’option /**fp:except** dans l’article [/fp (Spécifier le comportement de virgule flottante)](http://msdn.microsoft.com/library/10469d6b-e68b-4268-8075-d073f4f5d57e).  
  
- **FloatingPointModel**  
  
   Paramètre de chaîne facultatif.  
  
   Définit le modèle de virgule flottante.  
  
   Spécifiez l'une des valeurs suivantes, chacune d'elles correspondant à une option de ligne de commande.  
  
  - **Precise** - **/fp:precise**  
  
  - **Strict** - **/fp:strict**  
  
  - **Fast** - **/fp:fast**  
  
    Pour plus d’informations, consultez l’article [/fp (Spécifier le comportement de virgule flottante)](http://msdn.microsoft.com/library/10469d6b-e68b-4268-8075-d073f4f5d57e).  
  
- **ForceConformanceInForLoopScope**  
  
   Paramètre booléen facultatif.  
  
   Si `true`, implémente un comportement C++ standard dans les boucles [for](http://msdn.microsoft.com/library/6c7d01b3-c4c1-4c6a-aa58-e2d198f33d4a) utilisant les extensions Microsoft ([/Ze](http://msdn.microsoft.com/library/65e49258-7161-4289-a176-7c5c0656b1a2)).  
  
   Pour plus d’informations, consultez l’article [/Zc:forScope (Forcer la conformité à la portée de la boucle for)](http://msdn.microsoft.com/library/3031f02d-3b14-4ad0-869e-22b0110c3aed).  
  
- **ForcedIncludeFiles**  
  
   Paramètre `String[]` facultatif.  
  
   Entraîne le traitement d’un ou de plusieurs fichiers d’en-tête spécifiés par le préprocesseur.  
  
   Pour plus d’informations, consultez l’article [/FI (Nom du fichier Include imposé)](http://msdn.microsoft.com/library/07e79577-8152-4df9-a64c-aae08c603397).  
  
- **ForcedUsingFiles**  
  
   Paramètre **String[]** facultatif.  
  
   Entraîne le traitement d’un ou de plusieurs fichiers **#using** spécifiés par le préprocesseur.  
  
   Pour plus d’informations, consultez l’article [/FU (Nom du fichier #using imposé)](http://msdn.microsoft.com/library/698f8603-457f-435a-baff-5ac9243d6ca1).  
  
- **FunctionLevelLinking**  
  
   Paramètre `Boolean` facultatif.  
  
   Si `true`, permet au compilateur d’empaqueter des fonctions individuelles sous la forme de fonctions empaquetées (COMDATs).  
  
   Pour plus d’informations, consultez l’article [/Gy (Activer la liaison au niveau des fonctions)](http://msdn.microsoft.com/library/0d3cf14c-ed7d-4ad3-b4b6-104e56f61046).  
  
- **GenerateXMLDocumentationFiles**  
  
   Paramètre `Boolean` facultatif.  
  
   Si `true`, le compilateur traite les commentaires de la documentation dans les fichiers de code source, et crée un fichier .xdc pour chaque fichier de code source qui comporte de tels commentaires.  
  
   Pour plus d’informations, consultez l’article [/doc (Traiter les commentaires de documentation) (C/C++)](http://msdn.microsoft.com/library/b54f7e2c-f28f-4f46-9ed6-0db09be2cc63). Consultez également le paramètre **XMLDocumentationFileName** dans ce tableau.  
  
- **IgnoreStandardIncludePath**  
  
   Paramètre `Boolean` facultatif.  
  
   Si `true`, empêche le compilateur de rechercher des fichiers include dans les répertoires spécifiés dans les variables d’environnement PATH et INCLUDE.  
  
   Pour plus d’informations, consultez l’article [/X (Ignorer les chemins d’accès Include standard)](http://msdn.microsoft.com/library/16bdf2cc-c8dc-46e4-bdcc-f3caeba5e1ef).  
  
- **InlineFunctionExpansion**  
  
   Paramètre **String** facultatif.  
  
   Spécifie le niveau d’expansion des fonctions inline pour la génération.  
  
   Spécifiez l'une des valeurs suivantes, chacune d'elles correspondant à une option de ligne de commande.  
  
  - **Default** - *\<aucune>*  
  
  - **Disabled** - **/Ob0**  
  
  - **OnlyExplicitInline** - **/Ob1**  
  
  - **AnySuitable** - **/Ob2**  
  
    Pour plus d’informations, consultez l’article [/Ob (Expansion des fonctions Inline)](http://msdn.microsoft.com/library/f134e6df-e939-4980-a01d-47425dbc562a).  
  
- **IntrinsicFunctions**  
  
   Paramètre `Boolean` facultatif.  
  
   Si `true`, remplace certains appels de fonction par une forme intrinsèque ou par d’autres formes spéciales de la fonction qui contribuent à une exécution plus rapide de votre application.  
  
   Pour plus d’informations, consultez l’article [/Oi (Générer des fonctions intrinsèques)](http://msdn.microsoft.com/library/fa4a3bf6-0ed8-481b-91c0-add7636132b4).  
  
- **MinimalRebuild**  
  
   Paramètre `Boolean` facultatif.  
  
   Si `true`, permet une régénération minimale, qui détermine si les fichiers sources C++ qui incluent des définitions de classe C++ modifiées (stockées dans des fichiers d’en-tête [.h]) doivent être recompilés.  
  
   Pour plus d’informations, consultez l’article [/Gm (Activer la régénération minimale)](http://msdn.microsoft.com/library/d8869ce0-d2ea-40eb-8dae-6d2cdb61dd59).  
  
- **MultiProcessorCompilation**  
  
   Paramètre `Boolean` facultatif.  
  
   Si `true`, utilise plusieurs processeurs pour procéder à la compilation. Ce paramètre crée un processus pour chaque processeur effectif de votre ordinateur.  
  
   Pour plus d’informations, consultez l’article [/MP (Générer avec plusieurs processus)](http://msdn.microsoft.com/library/a932b14a-74fe-4b45-84e4-6bf53f0f5e07). Consultez également le paramètre **ProcessorNumber** dans ce tableau.  
  
- **ObjectFileName**  
  
   Paramètre **String** facultatif.  
  
   Spécifie un nom de fichier objet (.obj) ou un répertoire à utiliser à la place de la valeur par défaut.  
  
   Pour plus d’informations, consultez l’article [/Fo (Nom de fichier objet)](http://msdn.microsoft.com/library/0e6d593e-4e7f-4990-9e6e-92e1dcbcf6e6).  
  
- **ObjectFiles**  
  
   Paramètre **String[]** facultatif.  
  
   Liste des fichiers objets.  
  
- **OmitDefaultLibName**  
  
   Paramètre `Boolean` facultatif.  
  
   Si `true`, omet le nom de la bibliothèque runtime C par défaut du fichier objet (.obj). Par défaut, le compilateur place le nom de la bibliothèque dans le fichier .obj afin de diriger l’éditeur de liens vers la bibliothèque appropriée.  
  
   Pour plus d’informations, consultez l’article [/Zl (Omettre le nom de la bibliothèque par défaut)](http://msdn.microsoft.com/library/b27d39d0-44d6-498c-84ae-27c1326fee59).  
  
- **OmitFramePointers**  
  
   Paramètre `Boolean` facultatif.  
  
   Si `true`, empêche la création des pointeurs de frame sur la pile des appels.  
  
   Pour plus d’informations, consultez l’article [/Oy (Omission du pointeur frame)](http://msdn.microsoft.com/library/c451da86-5297-4c5a-92bc-561d41379853).  
  
- **OpenMPSupport**  
  
   Paramètre `Boolean` facultatif.  
  
   Si `true`, le compilateur traite les clauses et directives OpenMP.  
  
   Pour plus d’informations, consultez l’article [/openmp (Activer la prise en charge OpenMP 2.0)](http://msdn.microsoft.com/library/9082b175-18d3-4378-86a7-c0eb95664e13).  
  
- **Optimization**  
  
   Paramètre **String** facultatif.  
  
   Spécifie différentes optimisations de code en termes de vitesse et de taille.  
  
   Spécifiez l'une des valeurs suivantes, chacune d'elles correspondant à une option de ligne de commande.  
  
  - **Disabled** - **/Od**  
  
  - **MinSpace** - **/O1**  
  
  - **MaxSpeed** - **/O2**  
  
  - **Full** - **/Ox**  
  
    Pour plus d’informations, consultez l’article [/O Options (Optimize Code) (Options /O [optimiser le code])](http://msdn.microsoft.com/library/77997af9-5555-4b3d-aa57-6615b27d4d5d).  
  
- **PrecompiledHeader**  
  
   Paramètre **String** facultatif.  
  
   Crée ou utilise un fichier d’en-tête précompilé (.pch) pendant la génération.  
  
   Spécifiez l'une des valeurs suivantes, chacune d'elles correspondant à une option de ligne de commande.  
  
  - **NotUsing** - *\<aucune>*  
  
  - **Create** - **/Yc**  
  
  - **Use** - **/Yu**  
  
    Pour plus d’informations, consultez les articles [/Yc (Créer un fichier d’en-tête précompilé)](http://msdn.microsoft.com/library/47c2e555-b4f5-46e6-906e-ab5cf21f0678) et [/Yu (Utiliser un fichier d’en-tête précompilé)](http://msdn.microsoft.com/library/24f1bd0e-b624-4296-a17e-d4b53e374e1f). Consultez également les paramètres **PrecompiledHeaderFile** et **PrecompiledHeaderOutputFile** dans ce tableau.  
  
- **PrecompiledHeaderFile**  
  
   Paramètre **String** facultatif.  
  
   Spécifie un nom de fichier d’en-tête précompilé à créer ou utiliser.  
  
   Pour plus d’informations, consultez les articles [/Yc (Créer un fichier d’en-tête précompilé)](http://msdn.microsoft.com/library/47c2e555-b4f5-46e6-906e-ab5cf21f0678) et [/Yu (Utiliser un fichier d’en-tête précompilé)](http://msdn.microsoft.com/library/24f1bd0e-b624-4296-a17e-d4b53e374e1f).  
  
- **PrecompiledHeaderOutputFile**  
  
   Paramètre **String** facultatif.  
  
   Spécifie un nom de chemin d’accès pour un en-tête précompilé au lieu d’utiliser le nom du chemin d’accès par défaut.  
  
   Pour plus d’informations, consultez l’article [/Fp (Nom de fichier .pch)](http://msdn.microsoft.com/library/0fcd9cbd-e09f-44d3-9715-b41efb5d0be2).  
  
- **PreprocessKeepComments**  
  
   Paramètre `Boolean` facultatif.  
  
   Si `true`, conserve les commentaires pendant le prétraitement.  
  
   Pour plus d’informations, consultez l’article [/C (Conserver les commentaires pendant le prétraitement)](http://msdn.microsoft.com/library/944567ca-16bc-4728-befe-d414a7787f26).  
  
- **PreprocessorDefinitions**  
  
   Paramètre `String[]` facultatif.  
  
   Définit un symbole de prétraitement pour votre fichier source.  
  
   Pour plus d'informations, consultez [/D (Preprocessor Definitions)](http://msdn.microsoft.com/library/b53fdda7-8da1-474f-8811-ba7cdcc66dba).  
  
- **PreprocessOutput**  
  
   Paramètre `ITaskItem[]` facultatif.  
  
   Définit un tableau d’éléments de sortie de préprocesseur pouvant être consommés et émis par des tâches.  
  
- **PreprocessOutputPath**  
  
   Paramètre `String` facultatif.  
  
   Spécifie le nom du fichier de sortie dans lequel le paramètre **PreprocessToFile** écrit la sortie prétraitée.  
  
   Pour plus d’informations, consultez l’article [/Fi (prétraiter le nom du fichier de sortie)](http://msdn.microsoft.com/library/6d0ba983-a8b7-41ec-84f5-b4688ef8efee).  
  
- **PreprocessSuppressLineNumbers**  
  
   Paramètre `Boolean` facultatif.  
  
   Si `true`, prétraite les fichiers sources C et C++ et copie les fichiers prétraités sur le périphérique de sortie standard.  
  
   Pour plus d’informations, consultez l’article [/EP (Prétraiter dans stdout sans directive #line)](http://msdn.microsoft.com/library/6ec411ae-e33d-4ef5-956e-0054635eabea).  
  
- **PreprocessToFile**  
  
   Paramètre `Boolean` facultatif.  
  
   Si `true`, prétraite les fichiers sources C et C++ et copie la sortie prétraitée dans un fichier.  
  
   Pour plus d’informations, consultez l’article [/P (Prétraiter dans un fichier)](http://msdn.microsoft.com/library/123ee54f-8219-4a6f-9876-4227023d83fc).  
  
- **ProcessorNumber**  
  
   Paramètre `Integer` facultatif.  
  
   Spécifie le nombre maximal de processeurs à utiliser dans une compilation multiprocesseur. Utilisez ce paramètre conjointement avec le paramètre **MultiProcessorCompilation**.  
  
- **ProgramDataBaseFileName**  
  
   Paramètre `String` facultatif.  
  
   Spécifie un nom pour le fichier de base de données du programme (PDB).  
  
   Pour plus d’informations, consultez l’article [/Fd (Nom de fichier PDB)](http://msdn.microsoft.com/library/3977a9ed-f0ac-45df-bf06-01cedd2ba85a).  
  
- **RuntimeLibrary**  
  
   Paramètre `String` facultatif.  
  
   Indique si un module multithread est une DLL et sélectionne les versions retail ou debug de la bibliothèque runtime.  
  
   Spécifiez l'une des valeurs suivantes, chacune d'elles correspondant à une option de ligne de commande.  
  
  - **MultiThreaded** - **/MT**  
  
  - **MultiThreadedDebug** - **/MTd**  
  
  - **MultiThreadedDLL** - **/MD**  
  
  - **MultiThreadedDebugDLL** - **/MDd**  
  
    Pour plus d’informations, consultez l’article [/MD, /MT, /LD (Utiliser la bibliothèque Runtime)](http://msdn.microsoft.com/library/cf7ed652-dc3a-49b3-aab9-ad60e5395579).  
  
- **RuntimeTypeInfo**  
  
   Paramètre `Boolean` facultatif.  
  
   Si `true`, ajoute le code pour vérifier les types d’objet C++ à l’exécution (informations de type au moment de l’exécution).  
  
   Pour plus d’informations, consultez l’article [/GR (Activer les informations de type au moment de l’exécution)](http://msdn.microsoft.com/library/d1f9f850-dcec-49fd-96ef-e72d01148906).  
  
- **ShowIncludes**  
  
   Paramètre `Boolean` facultatif.  
  
   Si `true`, le compilateur sort la liste des fichiers include.  
  
   Pour plus d’informations, consultez l’article [/showIncludes (Liste des fichiers Include)](http://msdn.microsoft.com/library/0b74b052-f594-45a6-a7c7-09e1a319547d).  
  
- **SmallerTypeCheck**  
  
   Paramètre `Boolean` facultatif.  
  
   Si `true`, signale une erreur d’exécution si une valeur est affectée à un type de données inférieur et provoque une perte de données.  
  
   Pour plus d’informations, consultez l’option **/RTCc** dans [/RTC (Vérifications des erreurs au moment de l’exécution)](http://msdn.microsoft.com/library/9702c558-412c-4004-acd5-80761f589368).  
  
- **Sources**  
  
   Paramètre `ITaskItem[]` requis.  
  
   Spécifie la liste des fichiers sources séparés par des espaces.  
  
- **StringPooling**  
  
   Paramètre `Boolean` facultatif.  
  
   Si `true`, permet au compilateur de créer une copie de chaînes identiques dans l’image du programme.  
  
   Pour plus d’informations, consultez l’article [/GF (Supprimer les doublons)](http://msdn.microsoft.com/library/bb7b5d1c-8e1f-453b-9298-8fcebf37d16c).  
  
- **StructMemberAlignment**  
  
   Paramètre `String` facultatif.  
  
   Spécifie l’alignement des octets pour tous les membres d’une structure.  
  
   Spécifiez l'une des valeurs suivantes, chacune d'elles correspondant à une option de ligne de commande.  
  
  - **Default** - **/Zp1**  
  
  - **1Byte** - **/Zp1**  
  
  - **2Bytes** - **/Zp2**  
  
  - **4Bytes** - **/Zp4**  
  
  - **8Bytes** - **/Zp8**  
  
  - **16Bytes** - **/Zp16**  
  
    Pour plus d’informations, consultez l’article [/Zp (Alignement des membres de la structure)](http://msdn.microsoft.com/library/5242f656-ed9b-48a3-bc73-cfcf3ed2520f).  
  
- **SuppressStartupBanner**  
  
   Paramètre `Boolean` facultatif.  
  
   Si la valeur est `true`, empêche l'affichage du message de copyright et de numéro de version quand la tâche démarre.  
  
   Pour plus d’informations, consultez l’article [/nologo (Suppression de la bannière de démarrage) (C/C++)](http://msdn.microsoft.com/library/75930d8b-b11c-4db8-99e5-b52f97da0693).  
  
- **TrackerLogDirectory**  
  
   Paramètre `String` facultatif.  
  
   Spécifie le répertoire intermédiaire dans lequel sont stockés les fichiers journaux de suivi de cette tâche.  
  
   Pour plus d’informations, consultez les paramètres **TLogReadFiles** et **TLogWriteFiles** dans ce tableau.  
  
- **TreatSpecificWarningsAsErrors**  
  
   Paramètre **String[]** facultatif.  
  
   Traite la liste spécifiée des avertissements du compilateur comme des erreurs.  
  
   Pour plus d’informations, consultez l’option **/we**`n` dans l’article [/w, /W0, /W1, /W2, /W3, /W4, /w1, /w2, /w3, /w4, /Wall, /wd, /we, /wo, /Wv, /WX (Niveau d’avertissement)](http://msdn.microsoft.com/library/d6bc7bf5-c754-4879-909c-8e3a67e2629f).  
  
- **TreatWarningAsError**  
  
   Paramètre `Boolean` facultatif.  
  
   Si `true`, considère tous les avertissements du compilateur comme des erreurs.  
  
   Pour plus d’informations, consultez l’option **/WX** dans l’article [/w, /W0, /W1, /W2, /W3, /W4, /w1, /w2, /w3, /w4, /Wall, /wd, /we, /wo, /Wv, /WX (Niveau d’avertissement)](http://msdn.microsoft.com/library/d6bc7bf5-c754-4879-909c-8e3a67e2629f).  
  
- **TreatWChar_tAsBuiltInType**  
  
   Paramètre `Boolean` facultatif.  
  
   Si `true`, considère le type `wchar_t` comme un type natif.  
  
   Pour plus d’informations, consultez [/Zc:wchar_t (wchar_t est un type natif)](http://msdn.microsoft.com/library/b0de5a84-da72-4e5a-9a4e-541099f939e0).  
  
- **UndefineAllPreprocessorDefinitions**  
  
   Paramètre `Boolean` facultatif.  
  
   Si `true`, annule la définition des symboles propres à Microsoft que le compilateur définit.  
  
   Pour plus d’informations, consultez l’option **/u** dans l’article [/U, /u (Annuler la définition des symboles)](http://msdn.microsoft.com/library/7bc0474f-6d1f-419b-807d-0d8816763b2a).  
  
- **UndefinePreprocessorDefinitions**  
  
   Paramètre `String[]` facultatif.  
  
   Indique une liste d’un ou de plusieurs symboles de préprocesseur dont la définition va être annulée.  
  
   Pour plus d’informations, consultez l’option **/U** dans l’article [/U, /u (Annuler la définition des symboles)](http://msdn.microsoft.com/library/7bc0474f-6d1f-419b-807d-0d8816763b2a).  
  
- **UseFullPaths**  
  
   Paramètre `Boolean` facultatif.  
  
   Si `true`, affiche le chemin d’accès complet des fichiers de code source transmis au compilateur dans les diagnostics.  
  
   Pour plus d’informations, consultez l’article [/FC (Chemin d’accès complet du fichier de code source dans les diagnostics)](http://msdn.microsoft.com/library/1f11414e-cb42-421b-be68-9d369aab036b).  
  
- **UseUnicodeForAssemblerListing**  
  
   Paramètre `Boolean` facultatif.  
  
   Si `true`, entraîne la création du fichier de sortie au format UTF-8.  
  
   Pour plus d’informations, consultez l’option **/FAu** dans l’article [/FA, /Fa (Fichier listing)](http://msdn.microsoft.com/library/c7507d0e-c69d-44f9-b8e2-d2c398697402).  
  
- **WarningLevel**  
  
   Paramètre `String` facultatif.  
  
   Spécifie le niveau d’avertissement le plus élevé devant être généré par le compilateur.  
  
   Spécifiez l'une des valeurs suivantes, chacune d'elles correspondant à une option de ligne de commande.  
  
  - **TurnOffAllWarnings** - **/W0**  
  
  - **Level1** - **/W1**  
  
  - **Level2** - **/W2**  
  
  - **Level3** - **/W3**  
  
  - **Level4** - **/W4**  
  
  - **EnableAllWarnings** - **/Wall**  
  
    Pour plus d’informations, consultez l’option **/W**_n_ dans l’article [/w, /W0, /W1, /W2, /W3, /W4, /w1, /w2, /w3, /w4, /Wall, /wd, /we, /wo, /Wv, /WX (Niveau d’avertissement)](http://msdn.microsoft.com/library/d6bc7bf5-c754-4879-909c-8e3a67e2629f).  
  
- **WholeProgramOptimization**  
  
   Paramètre `Boolean` facultatif.  
  
   Si `true`, active l’optimisation de l’ensemble du programme.  
  
   Pour plus d’informations, consultez l’article [/GL (Optimisation de l’ensemble du programme)](http://msdn.microsoft.com/library/09d51e2d-9728-4bd0-b5dc-3b8284aca1d1).  
  
- **XMLDocumentationFileName**  
  
   Paramètre `String` facultatif.  
  
   Spécifie le nom des fichiers de documentation XML générés. Ce paramètre peut être un nom de fichier ou de répertoire.  
  
   Pour plus d’informations, consultez l’argument `name` dans l’article [/doc (Traiter les commentaires de documentation) (C/C++)](http://msdn.microsoft.com/library/b54f7e2c-f28f-4f46-9ed6-0db09be2cc63). Consultez également le paramètre **GenerateXMLDocumentationFiles** dans ce tableau.  
  
- **MinimalRebuildFromTracking**  
  
   Paramètre `Boolean` facultatif.  
  
   Si `true`, une génération incrémentielle suivie est exécutée ; si `false`, une régénération est exécutée.  
  
- **TLogReadFiles**  
  
   Paramètre `ITaskItem[]` facultatif.  
  
   Spécifie un tableau des éléments qui représentent les *journaux de suivi des fichiers lus*.  
  
   Un journal de suivi des fichiers lus (.tlog) contient les noms des fichiers d’entrée qui sont lus par une tâche. Il est utilisé par le système de conception de projet pour prendre en charge des générations incrémentielles. Pour plus d’informations, consultez les paramètres **TrackerLogDirectory** et **TrackFileAccess** dans ce tableau.  
  
- **TLogWriteFiles**  
  
   Paramètre `ITaskItem[]` facultatif.  
  
   Spécifie un tableau des éléments qui représentent les *journaux de suivi des fichiers écrits*.  
  
   Un journal de suivi des fichiers écrits (.tlog) contient les noms des fichiers d’entrée qui sont écrits par une tâche. Il est utilisé par le système de conception de projet pour prendre en charge des générations incrémentielles. Pour plus d’informations, consultez les paramètres **TrackerLogDirectory** et **TrackFileAccess** dans ce tableau.  
  
- **TrackFileAccess**  
  
   Paramètre `Boolean` facultatif.  
  
   Si `true`, effectue le suivi des modèles d’accès au fichier.  
  
   Pour plus d’informations, consultez les paramètres **TLogReadFiles** et **TLogWriteFiles** dans ce tableau.  
  
## <a name="remarks"></a>Notes  
  
## <a name="see-also"></a>Voir aussi  
 [Task Reference (Informations de référence sur les tâches MSBuild)](../msbuild/msbuild-task-reference.md)



