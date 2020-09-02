---
title: Tâche MIDL | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- VC.Project.VCMidlTool.ServerStubFile
- VC.Project.VCMidlTool.ApplicationConfigurationMode
- VC.Project.VCMidlTool.GenerateServerFiles
- VC.Project.VCMidlTool.ClientStubFile
- VC.Project.VCMidlTool.LocaleID
- VC.Project.VCMidlTool.GenerateClientFiles
- VC.Project.VCMidlTool.SuppressCompilerWarnings
- VC.Project.VCMidlTool.TypeLibFormat
- vc.task.midl
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild (Visual C++), MIDL task
- MIDL task (MSBuild (Visual C++))
ms.assetid: 727efa8c-3336-40b8-8bef-ae6cbd77a422
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 336a02927374e856a2d6f5a55eb03c5ae1ac7037
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75845188"
---
# <a name="midl-task"></a>Tâche MIDL
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Encapsule l’outil Compilateur MIDL (Microsoft Interface Definition Language), midl.exe. Pour plus d’informations, consultez « MIDL Command-Line Reference (Informations de référence sur les lignes de commande MIDL) » sur le site web [MSDN](https://msdn.microsoft.com/).  
  
## <a name="parameters"></a>Paramètres  
 Le tableau ci-après décrit les paramètres de la tâche **MIDL**. La plupart des paramètres de tâche, et quelques ensembles de paramètres, correspondent à une option de ligne de commande.  
  
- **AdditionalIncludeDirectories**  
  
     Paramètre **String []** facultatif.  
  
     Ajoute un répertoire à la liste des répertoires dans lesquels sont recherchés les fichiers IDL importés, y compris les fichiers d’en-tête, et les fichiers de configuration d’application (ACF).  
  
     Pour plus d’informations, consultez l’option **/I** dans la page « MIDL Command-Line Reference (Informations de référence sur les lignes de commande MIDL) » sur le site web [MSDN](https://msdn.microsoft.com/).  
  
- **AdditionalOptions**  
  
     Paramètre de **chaîne** facultatif.  
  
     Liste des options de ligne de commande. Par exemple, **«**_/option1/option2/option #_». Utilisez ce paramètre pour spécifier des options de ligne de commande qui ne sont pas représentées par un autre paramètre de tâche MIDL.  
  
     Pour plus d’informations, consultez « MIDL Command-Line Reference (Informations de référence sur les lignes de commande MIDL) » sur le site web [MSDN](https://msdn.microsoft.com/).  
  
- **ApplicationConfigurationMode**  
  
     Paramètre **booléen** facultatif.  
  
     Si `true`, vous permet d’utiliser certains mots clés ACF dans le fichier IDL.  
  
     Pour plus d’informations, consultez l’option **/app_config** dans la page « MIDL Command-Line Reference (Informations de référence sur les lignes de commande MIDL) » sur le site web [MSDN](https://msdn.microsoft.com/).  
  
- **ClientStubFile**  
  
     Paramètre de **chaîne** facultatif.  
  
     Spécifie le nom du fichier stub client d’une interface RPC.  
  
     Pour plus d’informations, consultez l’option **/cstub** dans la page « MIDL Command-Line Reference (Informations de référence sur les lignes de commande MIDL) » sur le site web [MSDN](https://msdn.microsoft.com/). Reportez-vous également au paramètre **ServerStubFile** de ce tableau.  
  
- **CPreprocessOptions**  
  
     Paramètre de **chaîne** facultatif.  
  
     Spécifie les options à transmettre au préprocesseur C/C++. Spécifiez une liste d’options de préprocesseur séparées par des espaces.  
  
     Pour plus d’informations, consultez l’option **/cpp_opt** dans la page « MIDL Command-Line Reference (Informations de référence sur les lignes de commande MIDL) » sur le site web [MSDN](https://msdn.microsoft.com/).  
  
- **DefaultCharType**  
  
     Paramètre de **chaîne** facultatif.  
  
     Spécifie le type de caractère par défaut que le compilateur C utilisera pour compiler le code généré.  
  
     Spécifiez l'une des valeurs suivantes, chacune d'elles correspondant à une option de ligne de commande.  
  
    |Valeur|Option de ligne de commande|  
    |-----------|--------------------------|  
    |**Abonné**|**/char signed**|  
    |**Non signé**|**/char unsigned**|  
    |**R**|**/char ascii7**|  
  
     Pour plus d’informations, consultez l’option **/char** dans la page « MIDL Command-Line Reference (Informations de référence sur les lignes de commande MIDL) » sur le site web [MSDN](https://msdn.microsoft.com/).  
  
- **DllDataFileName**  
  
     Paramètre de **chaîne** facultatif.  
  
     Spécifie le nom du fichier *dlldata* généré pour une DLL de proxy.  
  
     Pour plus d’informations, consultez l’option **/dlldata** dans la page « MIDL Command-Line Reference (Informations de référence sur les lignes de commande MIDL) » sur le site web [MSDN](https://msdn.microsoft.com/).  
  
- **EnableErrorChecks**  
  
     Paramètre de **chaîne** facultatif.  
  
     Spécifie le type de vérification des erreurs que les stubs générés exécutent au moment de l’exécution.  
  
     Spécifiez l'une des valeurs suivantes, chacune d'elles correspondant à une option de ligne de commande.  
  
    |Valeur|Option de ligne de commande|  
    |-----------|--------------------------|  
    |**Aucun**|**/error none**|  
    |**EnableCustom**|**/Error**|  
    |**Tout**|**/error all**|  
  
     Pour plus d’informations, consultez l’option **/error** dans la page « MIDL Command-Line Reference (Informations de référence sur les lignes de commande MIDL) » sur le site web [MSDN](https://msdn.microsoft.com/).  
  
- **ErrorCheckAllocations**  
  
     Paramètre **booléen** facultatif.  
  
     Si `true`, vérifie les erreurs de mémoire insuffisante.  
  
     Pour plus d’informations, consultez l’option **/error allocation** dans la page « MIDL Command-Line Reference (Informations de référence sur les lignes de commande MIDL) » sur le site web [MSDN](https://msdn.microsoft.com/).  
  
- **ErrorCheckBounds**  
  
     Paramètre **booléen** facultatif.  
  
     Si `true`, vérifie la taille des tableaux ouverts et variables par rapport aux spécifications de durée de transmission.  
  
     Pour plus d’informations, consultez l’option **/error bounds_check** dans la page « MIDL Command-Line Reference (Informations de référence sur les lignes de commande MIDL) » sur le site web [MSDN](https://msdn.microsoft.com/).  
  
- **ErrorCheckEnumRange**  
  
     Paramètre **booléen** facultatif.  
  
     Si `true`, vérifie que les valeurs enum sont comprises dans une plage autorisée.  
  
     Pour plus d’informations, consultez l’option **/Error enum** dans l’aide de la ligne de commande (**/ ?**) pour midl.exe.  
  
- **ErrorCheckRefPointers**  
  
     Paramètre **booléen** facultatif.  
  
     Si `true`, vérifie qu’aucun pointeur de référence null n’a été transmis à des stubs clients.  
  
     Pour plus d’informations, consultez l’option **/error ref** dans la page « MIDL Command-Line Reference (Informations de référence sur les lignes de commande MIDL) » sur le site web [MSDN](https://msdn.microsoft.com/).  
  
- **ErrorCheckStubData**  
  
     Paramètre **booléen** facultatif.  
  
     Si `true`, génère un stub qui intercepte les exceptions d’unmarshaling côté serveur et les propage de nouveau vers le client.  
  
     Pour plus d’informations, consultez l’option **/error stub_data** dans la page « MIDL Command-Line Reference (Informations de référence sur les lignes de commande MIDL) » sur le site web [MSDN](https://msdn.microsoft.com/).  
  
- **GenerateClientFiles**  
  
     Paramètre de **chaîne** facultatif.  
  
     Spécifie si le compilateur génère les fichiers sources C côté client pour une interface RPC.  
  
     Spécifiez l'une des valeurs suivantes, chacune d'elles correspondant à une option de ligne de commande.  
  
    |Valeur|Option de ligne de commande|  
    |-----------|--------------------------|  
    |**Aucun**|**/client none**|  
    |**Talon**|**/client stub**|  
  
     Pour plus d’informations, consultez l’option **/client** dans la page « MIDL Command-Line Reference (Informations de référence sur les lignes de commande MIDL) » sur le site web [MSDN](https://msdn.microsoft.com/).  
  
- **GenerateServerFiles**  
  
     Paramètre de **chaîne** facultatif.  
  
     Spécifie si le compilateur génère les fichiers sources C côté serveur pour une interface RPC.  
  
     Spécifiez l'une des valeurs suivantes, chacune d'elles correspondant à une option de ligne de commande.  
  
    |Valeur|Option de ligne de commande|  
    |-----------|--------------------------|  
    |**Aucun**|**/server none**|  
    |**Talon**|**/server stub**|  
  
     Pour plus d’informations, consultez l’option **/server** dans la page « MIDL Command-Line Reference (Informations de référence sur les lignes de commande MIDL) » sur le site web [MSDN](https://msdn.microsoft.com/).  
  
- **GenerateStublessProxies**  
  
     Paramètre **booléen** facultatif.  
  
     Si `true`, génère des stubs entièrement interprétés avec des proxies sans stub pour les interfaces objet.  
  
     Pour plus d’informations, consultez l’option **/Oicf** dans la page « MIDL Command-Line Reference (Informations de référence sur les lignes de commande MIDL) » sur le site web [MSDN](https://msdn.microsoft.com/).  
  
- **GenerateTypeLibrary**  
  
     Paramètre **booléen** facultatif.  
  
     Si `true`, aucun fichier bibliothèque de types (.tlb) n’est généré.  
  
     Pour plus d’informations, consultez l’option **/notlb** dans la page « MIDL Command-Line Reference (Informations de référence sur les lignes de commande MIDL) » sur le site web [MSDN](https://msdn.microsoft.com/).  
  
- **HeaderFileName**  
  
     Paramètre de **chaîne** facultatif.  
  
     Spécifie le nom du fichier d’en-tête généré.  
  
     Pour plus d’informations, consultez l’option **/h** ou **/header** dans la page « MIDL Command-Line Reference (Informations de référence sur les lignes de commande MIDL) » sur le site web [MSDN](https://msdn.microsoft.com/).  
  
- **IgnoreStandardIncludePath**  
  
     Paramètre **booléen** facultatif.  
  
     Si `true`, la tâche MIDL effectue des recherches uniquement dans les répertoires spécifiés à l’aide du commutateur **AdditionalIncludeDirectories**, et ignore le répertoire actuel ainsi que les répertoires spécifiés par la variable d’environnement INCLUDE.  
  
     Pour plus d’informations, consultez l’option **/no_def_idir** dans la page « MIDL Command-Line Reference (Informations de référence sur les lignes de commande MIDL) » sur le site web [MSDN](https://msdn.microsoft.com/).  
  
- **InterfaceIdentifierFileName**  
  
     Paramètre de **chaîne** facultatif.  
  
     Spécifie le nom du *fichier identificateur d’interface* d’une interface COM. Cette opération remplace le nom par défaut obtenu en ajoutant « _i.c » au nom de fichier IDL.  
  
     Pour plus d’informations, consultez l’option **/iid** dans la page « MIDL Command-Line Reference (Informations de référence sur les lignes de commande MIDL) » sur le site web [MSDN](https://msdn.microsoft.com/).  
  
- **LocaleID**  
  
     Paramètre **Entier** facultatif.  
  
     Spécifie l’*identificateur de paramètres régionaux* qui permet d’utiliser des caractères internationaux dans les fichiers d’entrée, les noms de fichier et les chemins d’accès aux répertoires. Spécifiez un identificateur de paramètres régionaux décimaux.  
  
     Pour plus d’informations, consultez l’option **/lcid** dans la page « MIDL Command-Line Reference (Informations de référence sur les lignes de commande MIDL) » sur le site web [MSDN](https://msdn.microsoft.com/). Reportez-vous également à la page « Locale IDs Assigned by Microsoft » (ID de paramètres régionaux attribués par Microsoft) sur le site web MSDN.  
  
- **MkTypLibCompatible**  
  
     Paramètre **booléen** facultatif.  
  
     Si `true`, requiert que le format du fichier d’entrée soit compatible avec mktyplib.exe, version 2.03.  
  
     Pour plus d’informations, consultez l’option **/mktyplib203** dans la page « MIDL Command-Line Reference (Informations de référence sur les lignes de commande MIDL) » sur le site web [MSDN](https://msdn.microsoft.com/). Reportez-vous également à la page « ODL File Syntax » (Syntaxe du fichier ODL) sur le site web MSDN.  
  
- **OutputDirectory**  
  
     Paramètre de **chaîne** facultatif.  
  
     Spécifie le répertoire par défaut dans lequel la tâche MIDL écrit les fichiers de sortie.  
  
     Pour plus d’informations, consultez l’option **/out** dans la page « MIDL Command-Line Reference (Informations de référence sur les lignes de commande MIDL) » sur le site web [MSDN](https://msdn.microsoft.com/).  
  
- **PreprocessorDefinitions**  
  
     Paramètre **String []** facultatif.  
  
     Spécifie un ou plusieurs *définitions*, autrement dit, un nom et une valeur facultative à transmettre au préprocesseur C comme s’ils l’étaient par une directive `#define`. Forme de chaque définition : *name[=value]*.  
  
     Pour plus d’informations, consultez l’option **/D** dans la page « MIDL Command-Line Reference (Informations de référence sur les lignes de commande MIDL) » sur le site web [MSDN](https://msdn.microsoft.com/). Reportez-vous également au paramètre **UndefinePreprocessorDefinitions** de ce tableau.  
  
- **ProxyFileName**  
  
     Paramètre de **chaîne** facultatif.  
  
     Spécifie le nom du fichier proxy d’une interface COM.  
  
     Pour plus d’informations, consultez l’option **/proxy** dans la page « MIDL Command-Line Reference (Informations de référence sur les lignes de commande MIDL) » sur le site web [MSDN](https://msdn.microsoft.com/).  
  
- **RedirectOutputAndErrors**  
  
     Paramètre de **chaîne** facultatif.  
  
     Redirige le résultat, par exemple les messages d’erreur et les avertissements, de la sortie standard vers le fichier spécifié.  
  
     Pour plus d’informations, consultez l’option **/o** dans la page « MIDL Command-Line Reference (Informations de référence sur les lignes de commande MIDL) » sur le site web [MSDN](https://msdn.microsoft.com/).  
  
- **ServerStubFile**  
  
     Paramètre de **chaîne** facultatif.  
  
     Spécifie le nom du fichier stub serveur d’une interface RPC.  
  
     Pour plus d’informations, consultez l’option **/sstub** dans la page « MIDL Command-Line Reference (Informations de référence sur les lignes de commande MIDL) » sur le site web [MSDN](https://msdn.microsoft.com/). Reportez-vous également au paramètre **ClientStubFile** de ce tableau.  
  
- **Source**  
  
     Paramètre `ITaskItem[]` requis.  
  
     Spécifie la liste des fichiers sources séparés par des espaces.  
  
- **StructMemberAlignment**  
  
     Paramètre de **chaîne** facultatif.  
  
     Spécifie l’alignement (*niveau de compression*) des structures sur le système cible.  
  
     Spécifiez l'une des valeurs suivantes, chacune d'elles correspondant à une option de ligne de commande.  
  
    |Valeur|Option de ligne de commande|  
    |-----------|--------------------------|  
    |**NotSet**|*\<none>*|  
    |**1**|**/Zp1**|  
    |**2**|**/Zp2**|  
    |**4**|**/Zp4**|  
    |**8**|**/Zp8**|  
  
     Pour plus d’informations, consultez l’option **/Zp** dans la page « MIDL Command-Line Reference (Informations de référence sur les lignes de commande MIDL) » sur le site web [MSDN](https://msdn.microsoft.com/). L’option **/Zp** est équivalente à l’option **/pack** et à l’ancienne option **/align**.  
  
- **SuppressCompilerWarnings**  
  
     Paramètre **booléen** facultatif.  
  
     Si `true`, supprime les messages d’avertissement de la tâche MIDL.  
  
     Pour plus d’informations, consultez l’option **/no_warn** dans la page « MIDL Command-Line Reference (Informations de référence sur les lignes de commande MIDL) » sur le site web [MSDN](https://msdn.microsoft.com/).  
  
- **SuppressStartupBanner**  
  
     Paramètre `Boolean` facultatif.  
  
     Si la valeur est `true`, empêche l'affichage du message de copyright et de numéro de version quand la tâche démarre.  
  
     Pour plus d’informations, consultez l’option **/nologo** dans la page « MIDL Command-Line Reference (Informations de référence sur les lignes de commande MIDL) » sur le site web [MSDN](https://msdn.microsoft.com/).  
  
- **TargetEnvironment**  
  
     Paramètre de **chaîne** facultatif.  
  
     Spécifie l’environnement dans lequel l’application s’exécute.  
  
     Spécifiez l'une des valeurs suivantes, chacune d'elles correspondant à une option de ligne de commande.  
  
    |Valeur|Option de ligne de commande|  
    |-----------|--------------------------|  
    |**NotSet**|*\<none>*|  
    |**Win32**|**/env win32**|  
    |**Itanium**|**/env ia64**|  
    |**64x**|**/env x64**|  
  
     Pour plus d’informations, consultez l’option **/env** dans la page « MIDL Command-Line Reference (Informations de référence sur les lignes de commande MIDL) » sur le site web [MSDN](https://msdn.microsoft.com/).  
  
- **TrackerLogDirectory**  
  
     Paramètre `String` facultatif.  
  
     Spécifie le répertoire intermédiaire dans lequel sont stockés les fichiers journaux de suivi de cette tâche.  
  
- **TypeLibFormat**  
  
     Paramètre de **chaîne** facultatif.  
  
     Spécifie le format du fichier bibliothèque de types.  
  
     Spécifiez l'une des valeurs suivantes, chacune d'elles correspondant à une option de ligne de commande.  
  
    |Valeur|Option de ligne de commande|  
    |-----------|--------------------------|  
    |**NewFormat**|**/newtlb**|  
    |**OldFormat**|**/oldtlb**|  
  
     Pour plus d’informations, consultez les options **/newtlb** et **/oldtlb** dans la page « MIDL Command-Line Reference (Informations de référence sur les lignes de commande MIDL) » sur le site web [MSDN](https://msdn.microsoft.com/).  
  
- **TypeLibraryName**  
  
     Paramètre de **chaîne** facultatif.  
  
     Spécifie le nom du fichier bibliothèque de types.  
  
     Pour plus d’informations, consultez l’option **/tlb** dans la page « MIDL Command-Line Reference (Informations de référence sur les lignes de commande MIDL) » sur le site web [MSDN](https://msdn.microsoft.com/).  
  
- **UndefinePreprocessorDefinitions**  
  
     Paramètre **String []** facultatif.  
  
     Supprime toute définition précédente d’un nom en le transmettant au préprocesseur C comme si c’était par l’action d’une directive `#undefine`. Spécifiez un ou plusieurs noms définis précédemment.  
  
     Pour plus d’informations, consultez l’option **/U** dans la page « MIDL Command-Line Reference (Informations de référence sur les lignes de commande MIDL) » sur le site web [MSDN](https://msdn.microsoft.com/). Reportez-vous également au paramètre **PreprocessorDefinitions** de ce tableau.  
  
- **ValidateAllParameters**  
  
     Paramètre `Boolean` facultatif.  
  
     Si `true`, génère des informations supplémentaires de vérification des erreurs qui permettent d’effectuer des contrôles d’intégrité au moment de l’exécution. Si `false`, aucune information de vérification des erreurs n’est générée.  
  
     Pour plus d’informations, consultez les options **/robust** et **/no_robust** dans la page « MIDL Command-Line Reference (Informations de référence sur les lignes de commande MIDL) » sur le site web [MSDN](https://msdn.microsoft.com/).  
  
- **WarnAsError**  
  
     Paramètre `Boolean` facultatif.  
  
     Si `true`, traite tous les avertissements comme des erreurs.  
  
     Si le paramètre de tâche MIDL **WarningLevel** n’est pas spécifié, les avertissements du niveau par défaut, le niveau 1, sont considérés comme des erreurs.  
  
     Pour plus d’informations, consultez l’option **/WX** dans la page « MIDL Command-Line Reference (Informations de référence sur les lignes de commande MIDL) » sur le site web [MSDN](https://msdn.microsoft.com/). Reportez-vous également au paramètre **WarningLevel** de ce tableau.  
  
- **WarningLevel**  
  
     Paramètre de **chaîne** facultatif.  
  
     Spécifie la gravité (*niveau d’avertissement*) des avertissements à émettre. Aucun avertissement n’est émis pour la valeur 0. Un avertissement est émis si son niveau est numériquement inférieur ou égal à la valeur spécifiée.  
  
     Spécifiez l'une des valeurs suivantes, chacune d'elles correspondant à une option de ligne de commande.  
  
    |Valeur|Option de ligne de commande|  
    |-----------|--------------------------|  
    |**0**|**/W0**|  
    |**1**|**/W1**|  
    |**2**|**/W2**|  
    |**3**|**/W3**|  
    |**4**|**/W4**|  
  
     Pour plus d’informations, consultez l’option **/W** dans la page « MIDL Command-Line Reference (Informations de référence sur les lignes de commande MIDL) » sur le site web [MSDN](https://msdn.microsoft.com/). Reportez-vous également au paramètre **WarnAsError** de ce tableau.  
  
## <a name="remarks"></a>Notes  
  
## <a name="see-also"></a>Voir aussi  
 [Référence de tâche](../msbuild/msbuild-task-reference.md)
