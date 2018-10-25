---
title: Tâche Link | Microsoft Docs
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
- VC.Project.VCLinkerTool.ForceFileOutput
- VC.Project.VCLinkerTool.LinkStatus
- VC.Project.VCLinkerTool.CLRUnmanagedCodeCheck
- VC.Project.VCLinkerTool.SpecifySectionAttributes
- VC.Project.VCLinkerTool.SupportNobindOfDelayLoadedDLL
- VC.Project.VCLinkerTool.MinimumRequiredVersion
- VC.Project.VCLinkerTool.PerUserRedirection
- VC.Project.VCLinkerTool.CreateHotPatchableImage
- VC.Project.VCLinkerTool.DataExecutionPrevention
- VC.Project.VCLinkerTool.TreatLinkerWarningsAsErrors
- vc.task.link
- VC.Project.VCLinkerTool.ImageHasSafeExceptionHandlers
- VC.Project.VCLinkerTool.CLRSupportLastError
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild (Visual C++), Link task
- Link task (MSBuild (Visual C++))
ms.assetid: 0a61f168-3113-4fa7-83a3-d9142e2a33f8
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ab3e3238e78062bc1193a6d81b3f74749a263968
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49897717"
---
# <a name="link-task"></a>Lier la tâche
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Encapsule l’outil Éditeur de liens Visual C++, link.exe. L’outil Éditeur de liens lie des bibliothèques et des fichiers objets COFF (Common Object File Format) pour créer un fichier exécutable (.exe) ou une bibliothèque de liens dynamiques (DLL). Pour plus d’informations, consultez l’article [Options de l’Éditeur de liens](http://msdn.microsoft.com/library/c1d51b8a-bd23-416d-81e4-900e02b2c129).  
  
## <a name="parameters"></a>Paramètres  
 Le tableau ci-dessous décrit les paramètres de la tâche **Link**. La plupart des paramètres de tâche, et quelques ensembles de paramètres, correspondent à une option de ligne de commande.  
  
- **AdditionalDependencies**  
  
   Paramètre **String[]** facultatif.  
  
   Spécifie une liste de fichiers d’entrée à ajouter à la commande.  
  
   Pour plus d’informations, consultez l’article [Fichiers d’entrée LINK](http://msdn.microsoft.com/library/bb26fcc5-509a-4620-bc3e-b6c6e603a412).  
  
- **AdditionalLibraryDirectories**  
  
   Paramètre **String[]** facultatif.  
  
   Substitue le chemin d’accès de la bibliothèque d’environnement. Spécifiez un nom de répertoire.  
  
   Pour plus d’informations, consultez l’article [/LIBPATH (Autre chemin de bibliothèque)](http://msdn.microsoft.com/library/7240af0b-9a3d-4d53-8169-2a92cd6958ba).  
  
- **AdditionalManifestDependencies**  
  
   Paramètre **String[]** facultatif.  
  
   Spécifie les attributs qui sont placés dans la section `dependency` du fichier manifeste.  
  
   Pour plus d’informations, consultez l’article [/MANIFESTDEPENDENCY (Spécifier les dépendances de manifeste)](http://msdn.microsoft.com/library/e4b68313-33a2-4c3e-908e-ac2b9f7d6a73). Consultez également la page « Publisher Configuration Files » (Fichiers de configuration des serveurs de publication) sur le site web [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).  
  
- **AdditionalOptions**  
  
   Paramètre **String** facultatif.  
  
   Liste des options de l’Éditeur de liens indiquées sur la ligne de commande. Par exemple, **«** _/option1 /option2 /option#_  ». Utilisez ce paramètre pour spécifier des options de l’Éditeur de liens qui ne sont pas représentées par un autre paramètre de tâche **Link**.  
  
   Pour plus d’informations, consultez l’article [Options de l’Éditeur de liens](http://msdn.microsoft.com/library/c1d51b8a-bd23-416d-81e4-900e02b2c129).  
  
- **AddModuleNamesToAssembly**  
  
   Paramètre **String[]** facultatif.  
  
   Ajoute une référence de module à un assembly.  
  
   Pour plus d’informations, consultez l’article [/ASSEMBLYMODULE (Ajouter un module MSIL à l’assembly)](http://msdn.microsoft.com/library/67357da8-e4b6-49fd-932c-329a5777f143).  
  
- **AllowIsolation**  
  
   Paramètre **Boolean** facultatif.  
  
   Si `true`, le système d’exploitation recherche et charge le manifeste. Si `false`, indique que les DLL sont chargées comme s’il n’existait pas de manifeste.  
  
   Pour plus d’informations, consultez l’article [/ALLOWISOLATION (Recherche de manifeste)](http://msdn.microsoft.com/library/6d41851e-b3c1-4bdf-beaa-031773089d6f).  
  
- **AssemblyDebug**  
  
   Paramètre **Boolean** facultatif.  
  
   Si `true`, émet l’attribut **DebuggableAttribute** avec le suivi des informations de débogage, et désactive les optimisations JIT. Si `false`, émet l’attribut **DebuggableAttribute**, mais désactive le suivi des informations de débogage et active les optimisations JIT.  
  
   Pour plus d’informations, consultez l’article [/ASSEMBLYDEBUG (Ajouter DebuggableAttribute)](http://msdn.microsoft.com/library/94443af3-470c-41d7-83a0-7434563d7982).  
  
- **AssemblyLinkResource**  
  
   Paramètre **String[]** facultatif.  
  
   Crée un lien à une ressource .NET Framework dans le fichier de sortie ; le fichier de ressources n’est pas placé dans le fichier de sortie. Spécifiez le nom de la ressource.  
  
   Pour plus d’informations, consultez l’article [/ASSEMBLYLINKRESOURCE (Lien vers une ressource du .NET Framework)](http://msdn.microsoft.com/library/8b6ad184-1b33-47a4-8513-4803cf915b64).  
  
- **AttributeFileTracking**  
  
   Paramètre **booléen** implicite.  
  
   Active le suivi plus approfondi des fichiers pour capturer le comportement de liaison incrémentielle. Retourne toujours `true`.  
  
- **BaseAddress**  
  
   Paramètre **String** facultatif.  
  
   Définit une adresse de base pour le programme ou la DLL en cours de génération. Spécifiez `{address[,size] | @filename,key}`.  
  
   Pour plus d’informations, consultez l’article [/BASE (Adresse de base)](http://msdn.microsoft.com/library/00b9f6fe-0bd2-4772-a69c-7365eb199069).  
  
- **BuildingInIDE**  
  
   Paramètre **Boolean** facultatif.  
  
   Si true, indique que MSBuild est appelé à partir de l’IDE. Dans le cas contraire, indique que MSBuild est appelé à partir de la ligne de commande.  
  
   Ce paramètre n’a aucune option équivalente dans l’Éditeur de liens.  
  
- **CLRImageType**  
  
   Paramètre **String** facultatif.  
  
   Définit le type d’image CLR (Common Language Runtime).  
  
   Spécifiez l’une des valeurs suivantes, chacune d’elles correspondant à une option de l’Éditeur de liens.  
  
  - **Default** - *\<aucune>*  
  
  - **ForceIJWImage** - **/CLRIMAGETYPE:IJW**  
  
  - **ForcePureILImage** - **/CLRIMAGETYPE:PURE**  
  
  - **ForceSafeILImage** - **/CLRIMAGETYPE:SAFE**  
  
    Pour plus d’informations, consultez l’article [/CLRIMAGETYPE (Spécifier le type d’une image CLR)](http://msdn.microsoft.com/library/04c60ee6-9dd7-4391-bc03-6926ad0fa116).  
  
- **CLRSupportLastError**  
  
   Paramètre **String** facultatif.  
  
   Préserve le dernier code d’erreur des fonctions appelées via le mécanisme P/Invoke.  
  
   Spécifiez l’une des valeurs suivantes, chacune d’elles correspondant à une option de l’Éditeur de liens.  
  
  - **Enabled** - **/CLRSupportLastError**  
  
  - **Disabled** - **/CLRSupportLastError:NO**  
  
  - **SystemDlls** - **/CLRSupportLastError:SYSTEMDLL**  
  
    Pour plus d’informations, consultez l’article [/CLRSUPPORTLASTERROR (Conserver le dernier code d’erreur pour les appels PInvoke)](http://msdn.microsoft.com/library/b7057990-4154-4b1d-9fc9-6236f7be7575).  
  
- **CLRThreadAttribute**  
  
   Paramètre **String** facultatif.  
  
   Spécifie explicitement l’attribut de thread pour le point d’entrée de votre programme CLR.  
  
   Spécifiez l’une des valeurs suivantes, chacune d’elles correspondant à une option de l’Éditeur de liens.  
  
  - **DefaultThreadingAttribute** - **/CLRTHREADATTRIBUTE:NONE**  
  
  - **MTAThreadingAttribute** - **/CLRTHREADATTRIBUTE:MTA**  
  
  - **STAThreadingAttribute** - **/CLRTHREADATTRIBUTE:STA**  
  
    Pour plus d’informations, consultez l’article [/CLRTHREADATTRIBUTE (Définir l’attribut de thread CLR)](http://msdn.microsoft.com/library/4907e9ef-5031-446c-aecf-0a0b32fae1e8).  
  
- **CLRUnmanagedCodeCheck**  
  
   Paramètre **Boolean** facultatif.  
  
   Spécifie si l’Éditeur de liens applique **SuppressUnmanagedCodeSecurityAttribute** aux appels P/Invoke générés par l’Éditeur de liens à partir du code managé dans les DLL natives.  
  
   Pour plus d’informations, consultez l’article [/CLRUNMANAGEDCODECHECK (Ajouter SupressUnmanagedCodeSecurityAttribute)](http://msdn.microsoft.com/library/73abc426-dab0-45e2-be85-0f9a14206cc2).  
  
- **CreateHotPatchableImage**  
  
   Paramètre **String** facultatif.  
  
   Prépare une image corrigeable en mémoire.  
  
   Spécifiez l’une des valeurs suivantes, qui correspond à une option de l’Éditeur de liens.  
  
  - **Enabled** - **/FUNCTIONPADMIN**  
  
  - **X86Image** - **/FUNCTIONPADMIN:5**  
  
  - **X64Image** - **/FUNCTIONPADMIN:6**  
  
  - **ItaniumImage** - **/FUNCTIONPADMIN:16**  
  
    Pour plus d’informations, consultez l’article [/FUNCTIONPADMIN (Créer une image corrigeable en mémoire)](http://msdn.microsoft.com/library/25b02c13-1add-4fbd-add9-fcb30eb2cae7).  
  
- **DataExecutionPrevention**  
  
   Paramètre **Boolean** facultatif.  
  
   Si `true`, indique que la compatibilité d’un exécutable avec la fonctionnalité Prévention de l’exécution des données Windows a été testée.  
  
   Pour plus d’informations, consultez l’article [/NXCOMPAT (compatible avec la prévention de l’exécution des données)](http://msdn.microsoft.com/library/5858e7ff-24d3-4ac3-9046-af2c9e220d9b).  
  
- **DelayLoadDLLs**  
  
   Paramètre **String[]** facultatif.  
  
   Ce paramètre entraîne le *chargement différé* des DLL. Spécifiez le nom d’une DLL dont vous voulez différer le chargement.  
  
   Pour plus d’informations, consultez l’article [/DELAYLOAD (Différer le chargement de l’importation)](http://msdn.microsoft.com/library/39ea0f1e-5c01-450f-9c75-2d9761ff9b28).  
  
- **DelaySign**  
  
   Paramètre **Boolean** facultatif.  
  
   Si `true`, signe partiellement un assembly. Par défaut, la valeur est définie sur `false`.  
  
   Pour plus d’informations, consultez l’article [/DELAYSIGN (Signer partiellement un assembly)](http://msdn.microsoft.com/library/15244d30-3ecb-492f-a408-ffe81f38de20).  
  
- **Driver**  
  
   Paramètre **String** facultatif.  
  
   Spécifiez ce paramètre pour générer un pilote en mode noyau Windows NT.  
  
   Spécifiez l’une des valeurs suivantes, chacune d’elles correspondant à une option de l’Éditeur de liens.  
  
  - **NotSet** - *\<aucune>*  
  
  - **Driver** - **/Driver**  
  
  - **UpOnly** - **/DRIVER:UPONLY**  
  
  - **WDM** - **/DRIVER:WDM**  
  
    Pour plus d’informations, consultez l’article [/DRIVER (Pilote Windows NT en mode noyau)](http://msdn.microsoft.com/library/aeee8e28-5d97-40f5-ba16-9f370fe8a1b8).  
  
- **EmbedManagedResourceFile**  
  
   Paramètre **String[]** facultatif.  
  
   Incorpore un fichier de ressources dans un assembly. Spécifiez le nom du fichier de ressources requis. Spécifiez éventuellement le nom logique, qui permet de charger la ressource, ainsi que l’option **PRIVATE**, qui indique dans le manifeste de l’assembly que le fichier de ressources est privé.  
  
   Pour plus d’informations, consultez l’article [/ASSEMBLYRESOURCE (Incorporer une ressource managée)](http://msdn.microsoft.com/library/0ce6e1fb-921b-4b1b-a59c-d35388d789f2).  
  
- **EnableCOMDATFolding**  
  
   Paramètre **Boolean** facultatif.  
  
   Si `true`, active le pliage COMDAT identique.  
  
   Pour plus d’informations, consultez l’argument `ICF[= iterations]` de l’article [/OPT (Optimisations)](http://msdn.microsoft.com/library/8f229863-5f53-48a8-9478-243a647093ac).  
  
- **EnableUAC**  
  
   Paramètre **Boolean** facultatif.  
  
   Si `true`, indique que les informations de contrôle de compte d’utilisateur sont incorporées dans le manifeste du programme.  
  
   Pour plus d’informations, consultez l’article [/MANIFESTUAC (Incorporer des informations sur le contrôle de compte d’utilisateur dans le manifeste)](http://msdn.microsoft.com/library/2d243c39-fa13-493c-b56f-d0d972a1603a).  
  
- **EntryPointSymbol**  
  
   Paramètre **String** facultatif.  
  
   Spécifie une fonction de point d’entrée comme adresse de départ d’un fichier .exe ou d’une DLL. Spécifiez un nom de fonction comme valeur du paramètre.  
  
   Pour plus d’informations, consultez l’article [/ENTRY (Symbole de point d’entrée)](http://msdn.microsoft.com/library/26c62ba2-4f52-4882-a7bd-7046a0abf445).  
  
- **FixedBaseAddress**  
  
   Paramètre **Boolean** facultatif.  
  
   Si `true`, crée un programme ou une DLL qui peuvent être chargés uniquement à leur adresse de base préférée.  
  
   Pour plus d’informations, consultez l’article [/BASE (Adresse de base fixe)](http://msdn.microsoft.com/library/929bba5e-b7d8-40ed-943e-056aa3710fc5).  
  
- **ForceFileOutput**  
  
   Paramètre **String** facultatif.  
  
   Indique à l’Éditeur de liens de créer un fichier .exe ou une DLL valide même si un symbole est référencé sans être défini ou s’il est défini plusieurs fois.  
  
   Spécifiez l'une des valeurs suivantes, chacune d'elles correspondant à une option de ligne de commande.  
  
  - **Enabled** - **/FORCE**  
  
  - **MultiplyDefinedSymbolOnly** - **/FORCE:MULTIPLE**  
  
  - **UndefinedSymbolOnly** - **/FORCE:UNRESOLVED**  
  
    Pour plus d’informations, consultez l’article [/FORCE (Forcer la sortie d’un fichier)](http://msdn.microsoft.com/library/b1e9a218-a5eb-4e60-a4a4-65b4be15e5da).  
  
- **ForceSymbolReferences**  
  
   Paramètre **String[]** facultatif.  
  
   Ce paramètre indique à l’Éditeur de liens d’ajouter un symbole spécifié à la table de symboles.  
  
   Pour plus d’informations, consultez l’article [/INCLUDE (Forcer les références des symboles)](http://msdn.microsoft.com/library/4a039677-360a-480f-bd0b-448e239b449c).  
  
- **FunctionOrder**  
  
   Paramètre **String** facultatif.  
  
   Ce paramètre optimise votre programme en plaçant les fonctions empaquetées spécifiées (COMDAT) dans l’image dans un ordre prédéterminé.  
  
   Pour plus d’informations, consultez l’article [/ORDER (Mettre les fonctions dans l’ordre)](http://msdn.microsoft.com/library/ecf5eb3e-e404-4e86-9a91-4e5ec157261a).  
  
- **GenerateDebugInformation**  
  
   Paramètre **Boolean** facultatif.  
  
   Si `true`, crée des informations de débogage pour le fichier .exe ou la DLL.  
  
   Pour plus d’informations, consultez l’article [/DEBUG (Générer les informations de débogage)](http://msdn.microsoft.com/library/1af389ae-3f8b-4d76-a087-1cdf861e9103).  
  
- **GenerateManifest**  
  
   Paramètre **Boolean** facultatif.  
  
   Si `true`, crée un fichier manifeste côte à côte.  
  
   Pour plus d’informations, consultez l’article [/MANIFEST (Créer un manifeste d’assembly côte à côte)](http://msdn.microsoft.com/library/98c52e1e-712c-4f49-b149-4d0a3501b600).  
  
- **GenerateMapFile**  
  
   Paramètre **Boolean** facultatif.  
  
   Si `true`, crée un *fichier de mappage*. L’extension de nom du fichier de mappage est .map.  
  
   Pour plus d’informations, consultez l’article [/MAP (Générer fichier de mappage)](http://msdn.microsoft.com/library/9ccce53d-4e36-43da-87b0-7603ddfdea63).  
  
- **HeapCommitSize**  
  
   Paramètre **String** facultatif.  
  
   Spécifie la quantité de mémoire physique sur le tas à allouer à la fois.  
  
   Pour plus d’informations, consultez l’argument `commit` dans l’article [/HEAP (Définir la taille des tas)](http://msdn.microsoft.com/library/a3f71927-7f1d-492c-9fdb-dfccb1a043da). Reportez-vous également au paramètre **HeapReserveSize**.  
  
- **HeapReserveSize**  
  
   Paramètre **String** facultatif.  
  
   Spécifie l’allocation totale des tas dans la mémoire virtuelle.  
  
   Pour plus d’informations, consultez l’argument `reserve` dans l’article [/HEAP (Définir la taille des tas)](http://msdn.microsoft.com/library/a3f71927-7f1d-492c-9fdb-dfccb1a043da). Reportez-vous également au paramètre **HeapCommitSize** dans ce tableau.  
  
- **IgnoreAllDefaultLibraries**  
  
   Paramètre **Boolean** facultatif.  
  
   Si `true`, indique à l’Éditeur de liens de supprimer une ou plusieurs bibliothèques par défaut de la liste de recherche des bibliothèques lors de la résolution des références externes.  
  
   Pour plus d’informations, consultez l’article [/NODEFAULTLIB (Ignorer les bibliothèques)](http://msdn.microsoft.com/library/7270b673-6711-468e-97a7-c2925ac2be6e).  
  
- **IgnoreEmbeddedIDL**  
  
   Paramètre **Boolean** facultatif.  
  
   Si `true`, spécifie que les attributs IDL définis dans le code source ne doivent pas être traités dans un fichier .idl.  
  
   Pour plus d’informations, consultez l’article [/IGNOREIDL (Ne pas traiter les attributs dans MIDL)](http://msdn.microsoft.com/library/29514098-6a1c-4317-af2f-1dc268972780).  
  
- **IgnoreImportLibrary**  
  
   Paramètre **Boolean** facultatif.  
  
   Si `true`, spécifie que la bibliothèque d’importation générée par cette configuration ne doit pas être importée dans des projets dépendants.  
  
   Ce paramètre ne correspond pas à une option de l’Éditeur de liens.  
  
- **IgnoreSpecificDefaultLibraries**  
  
   Paramètre **String[]** facultatif.  
  
   Spécifie un ou plusieurs noms de bibliothèques par défaut à ignorer. Séparez plusieurs bibliothèques à l’aide de points-virgules.  
  
   Pour plus d’informations, consultez l’article [/NODEFAULTLIB (Ignorer les bibliothèques)](http://msdn.microsoft.com/library/7270b673-6711-468e-97a7-c2925ac2be6e).  
  
- **ImageHasSafeExceptionHandlers**  
  
   Paramètre **Boolean** facultatif.  
  
   Si `true`, l’Éditeur de liens produit une image uniquement s’il peut également produire un tableau des gestionnaires d’exceptions sécurisés de l’image.  
  
   Pour plus d’informations, consultez l’article [/SAFESEH (L’image est dotée de gestionnaires d’exceptions sécurisés)](http://msdn.microsoft.com/library/7722ff99-b833-4c65-a855-aaca902ffcb7).  
  
- **ImportLibrary**  
  
   Nom de bibliothèque d’importation spécifié par l’utilisateur qui remplace le nom de bibliothèque par défaut.  
  
   Pour plus d’informations, consultez l’article [/IMPLIB (Nommer la bibliothèque d’importation)](http://msdn.microsoft.com/library/fe8f71ab-7055-41b5-8ef8-2b97cfa4a432).  
  
- **KeyContainer**  
  
   Paramètre **String** facultatif.  
  
   Conteneur qui contient la clé d’un assembly signé.  
  
   Pour plus d’informations, consultez l’article [/KEYCONTAINER (Spécifier un conteneur de clé pour signer un assembly)](http://msdn.microsoft.com/library/94882d12-b77a-49c7-96d0-18a31aee001e). Reportez-vous également au paramètre **KeyFile** de ce tableau.  
  
- **KeyFile**  
  
   Paramètre **String** facultatif.  
  
   Spécifie un fichier qui contient la clé d’un assembly signé.  
  
   Pour plus d’informations, consultez l’article [/KEYFILE (Spécifier une clé ou une paire de clés pour signer un assembly)](http://msdn.microsoft.com/library/9b71f8c0-541c-4fe5-a0c7-9364f42ecb06). Reportez-vous également au paramètre **KeyContainer**.  
  
- **LargeAddressAware**  
  
   Paramètre **Boolean** facultatif.  
  
   Si `true`, l’application peut gérer des adresses supérieures à 2 gigaoctets.  
  
   Pour plus d’informations, consultez l’article [/LARGEADDRESSAWARE (Gérer les longues adresses)](http://msdn.microsoft.com/library/a29756c8-e893-47a9-9750-1f0d25359385).  
  
- **LinkDLL**  
  
   Paramètre **Boolean** facultatif.  
  
   Si `true`, génère une DLL comme fichier de sortie principal.  
  
   Pour plus d’informations, consultez l’article [/DLL (Générer une DLL)](http://msdn.microsoft.com/library/c7685aec-31d0-490f-9503-fb5171a23609).  
  
- **LinkErrorReporting**  
  
   Paramètre **String** facultatif.  
  
   Vous permet de signaler les erreurs internes du compilateur (ICE) directement à Microsoft.  
  
   Spécifiez l'une des valeurs suivantes, chacune d'elles correspondant à une option de ligne de commande.  
  
  - **NoErrorReport** - **/ERRORREPORT:NONE**  
  
  - **PromptImmediately** - **/ERRORREPORT:PROMPT**  
  
  - **QueueForNextLogin** - **/ERRORREPORT:QUEUE**  
  
  - **SendErrorReport** - **/ERRORREPORT:SEND**  
  
    Pour plus d’informations, consultez l’article [/ERRORREPORT (Signaler les erreurs internes de l’Éditeur de liens)](http://msdn.microsoft.com/library/f5fab595-a2f1-4eb0-ab5c-1c0fbd3d8c28).  
  
- **LinkIncremental**  
  
   Paramètre **Boolean** facultatif.  
  
   Si `true`, active les liens incrémentiels.  
  
   Pour plus d’informations, consultez l’article [/INCREMENTAL (Lier par incrément)](http://msdn.microsoft.com/library/135656ff-94fa-4ad4-a613-22e1a2a5d16b).  
  
- **LinkLibraryDependencies**  
  
   Paramètre **Boolean** facultatif.  
  
   Si la valeur est `true`, spécifie que les sorties de bibliothèque émanant des dépendances du projet sont automatiquement liées.  
  
   Ce paramètre ne correspond pas à une option de l’Éditeur de liens.  
  
- **LinkStatus**  
  
   Paramètre **Boolean** facultatif.  
  
   Si `true`, spécifie que l’Éditeur de liens doit afficher un indicateur de progression qui montre le pourcentage d’exécution du lien.  
  
   Pour plus d’informations, consultez l’argument `STATUS` dans l’article [LTCG (Génération de code durant l’édition de liens)](http://msdn.microsoft.com/library/788c6f52-fdb8-40c2-90af-4026ea2cf2e2).  
  
- **LinkTimeCodeGeneration**  
  
   Paramètre **String** facultatif.  
  
   Spécifie des options pour l’optimisation guidée par profil.  
  
   Spécifiez l'une des valeurs suivantes, chacune d'elles correspondant à une option de ligne de commande.  
  
  - **Default** - *\<aucune>*  
  
  - **UseLinkTimeCodeGeneration** - **/LTCG**  
  
  - **PGInstrument** - **/LTCG:PGInstrument**  
  
  - **PGOptimization** - **/LTCG:PGOptimize**  
  
  - **PGUpdate**  
  
     \- **/LTCG:PGUpdate**  
  
    Pour plus d’informations, consultez l’article [LTCG (Génération de code durant l’édition de liens)](http://msdn.microsoft.com/library/788c6f52-fdb8-40c2-90af-4026ea2cf2e2).  
  
- **ManifestFile**  
  
   Paramètre **String** facultatif.  
  
   Remplace le nom du fichier manifeste par défaut par le nom du fichier spécifié.  
  
   Pour plus d’informations, consultez l’article [/MANIFESTFILE (Nommer le fichier manifeste)](http://msdn.microsoft.com/library/befa5ab2-a9cf-4c9b-969a-e7b4a930f08d).  
  
- **MapExports**  
  
   Paramètre **Boolean** facultatif.  
  
   Si `true`, indique à l’Éditeur de liens d’inclure les fonctions exportées dans un fichier de mappage.  
  
   Pour plus d’informations, consultez l’argument `EXPORTS` dans l’article [/MAPINFO (Inclure des informations dans le fichier de mappage)](http://msdn.microsoft.com/library/533d2bce-f9b7-4fea-ae1c-0b4864c9d10b).  
  
- **MapFileName**  
  
   Paramètre **String** facultatif.  
  
   Remplace le nom du fichier de mappage par défaut par le nom du fichier spécifié.  
  
- **MergedIDLBaseFileName**  
  
   Paramètre **String** facultatif.  
  
   Indique le nom et l’extension de nom du fichier .idl.  
  
   Pour plus d’informations, consultez l’article [/IDLOUT (Nommer les fichiers de sortie MIDL)](http://msdn.microsoft.com/library/10d00a6a-85b4-4de1-8732-e422c6931509).  
  
- **MergeSections**  
  
   Paramètre **String** facultatif.  
  
   Combine des sections dans une image. Spécifiez `from-section=to-section`.  
  
   Pour plus d’informations, consultez l’article [/MERGE (Combiner des sections)](http://msdn.microsoft.com/library/10fb20c2-0b3f-4c8d-98a8-f69aedf03d52).  
  
- **MidlCommandFile**  
  
   Paramètre **String** facultatif.  
  
   Spécifiez le nom d’un fichier qui contient les options de ligne de commande MIDL.  
  
   Pour plus d’informations, consultez l’article [/MIDL (Spécification d’options de ligne de commande MIDL)](http://msdn.microsoft.com/library/22dc259e-b34c-4ed3-a380-4beb734482c1).  
  
- **MinimumRequiredVersion**  
  
   Paramètre **String** facultatif.  
  
   Spécifie la version minimale requise du sous-système. Les arguments sont des nombres décimaux compris entre 0 et 65 535.  
  
- **ModuleDefinitionFile**  
  
   Paramètre **String** facultatif.  
  
   Spécifie le nom d’un [fichier de définition de module](http://msdn.microsoft.com/library/08c0bc28-c5d2-47aa-9624-7fc68bcaa4d8).  
  
   Pour plus d’informations, consultez l’article [/DEF (Spécifier le fichier de définition de module)](http://msdn.microsoft.com/library/6497fa68-65f0-48ca-8f66-b87166fc631a).  
  
- **MSDOSStubFileName**  
  
   Paramètre **String** facultatif.  
  
   Attache le programme stub MS-DOS spécifié à un programme Win32.  
  
   Pour plus d’informations, consultez l’article [/STUB (Nom du fichier stub MS-DOS)](http://msdn.microsoft.com/library/65221ffe-4f9a-4a14-ac69-3cfb79b40b5f).  
  
- **NoEntryPoint**  
  
   Paramètre **Boolean** facultatif.  
  
   Si `true`, crée une DLL de ressource uniquement.  
  
   Pour plus d’informations, consultez l’article [/NOENTRY (Aucun point d’entrée)](http://msdn.microsoft.com/library/0214dd41-35ad-43ab-b892-e636e038621a).  
  
- **ObjectFiles**  
  
   Paramètre **String[]** implicite.  
  
   Spécifie les fichiers objets liés.  
  
- **OptimizeReferences**  
  
   Paramètre **Boolean** facultatif.  
  
   Si `true`, élimine les fonctions et/ou les données qui ne sont jamais référencées.  
  
   Pour plus d’informations, consultez l’argument `REF` dans l’article [/OPT (Optimisations)](http://msdn.microsoft.com/library/8f229863-5f53-48a8-9478-243a647093ac).  
  
- **OutputFile**  
  
   Paramètre **String** facultatif.  
  
   Remplace le nom et l’emplacement par défaut du programme créé par l’Éditeur de liens.  
  
   Pour plus d’informations, consultez l’article [/OUT (Nom du fichier de sortie)](http://msdn.microsoft.com/library/976210a4-e51f-4cfb-af5e-c16344455834).  
  
- **PerUserRedirection**  
  
   Paramètre **Boolean** facultatif.  
  
   Si `true` et si l’inscription de la sortie est activée, force les entrées de Registre écrites dans **HKEY_CLASSES_ROOT** à être redirigées vers **HKEY_CURRENT_USER**.  
  
- **PreprocessOutput**  
  
   Paramètre `ITaskItem[]` facultatif.  
  
   Définit un tableau d’éléments de sortie de préprocesseur pouvant être consommés et émis par des tâches.  
  
- **PreventDllBinding**  
  
   Paramètre **Boolean** facultatif.  
  
   Si `true`, indique à Bind.exe que l’image liée ne doit pas être associée.  
  
   Pour plus d’informations, consultez l’article [/ALLOWBIND (Éviter la liaison DLL)](http://msdn.microsoft.com/library/30e37e24-12e4-407e-988a-39d357403598).  
  
- **Profile**  
  
   Paramètre **booléen** facultatif.  
  
   Si `true`, génère un fichier de sortie utilisable avec le profileur **Outils d’analyse des performances**.  
  
   Pour plus d’informations, consultez l’article [/PROFILE (Profileur des outils d’analyse des performances)](http://msdn.microsoft.com/library/e676baa1-5063-47a3-a357-ba0d1f0d1699).  
  
- **ProfileGuidedDatabase**  
  
   Paramètre **String** facultatif.  
  
   Spécifie le nom du fichier .pgd qui permet de conserver les informations sur le programme en cours d’exécution.  
  
   Pour plus d’informations, consultez l’article [/PGD (Spécifier la base de données pour les optimisations guidées par profil)](http://msdn.microsoft.com/library/9f312498-493b-461f-886f-92652257e443).  
  
- **ProgramDatabaseFile**  
  
   Paramètre **String** facultatif.  
  
   Spécifie le nom de la base de données du programme (PDB) créée par l’Éditeur de liens.  
  
   Pour plus d’informations, consultez l’article [/PDB (Utiliser la base de données du programme)](http://msdn.microsoft.com/library/d23db0ce-10cb-427a-bc60-d6b2a852723d).  
  
- **RandomizedBaseAddress**  
  
   Paramètre **Boolean** facultatif.  
  
   Si `true`, génère une image exécutable qui peut être redéfinie de façon aléatoire au moment du chargement en utilisant la fonctionnalité de *randomisation du format d’espace d’adresse* (ASLR) de Windows.  
  
   Pour plus d’informations, consultez l’article [/DYNAMICBASE (Utiliser la randomisation du format d’espace d’adresse)](http://msdn.microsoft.com/library/6c0ced8e-fe9c-4b63-b956-eb8a55fbceb2).  
  
- **RegisterOutput**  
  
   Paramètre **Boolean** facultatif.  
  
   Si `true`, inscrit la sortie principale de cette génération.  
  
- **SectionAlignment**  
  
   Paramètre **entier** facultatif.  
  
   Spécifie l’alignement de chaque section dans l’espace d’adressage linéaire du programme. La valeur du paramètre est un numéro d’unité d’octets et une puissance de deux.  
  
   Pour plus d’informations, consultez l’article [/ALIGN (Alignement des sections)](http://msdn.microsoft.com/library/f2f8ac24-e90e-4bea-8205-f2960a3b1740).  
  
- **SetChecksum**  
  
   Paramètre **Boolean** facultatif.  
  
   Si `true`, définit la somme de contrôle dans l’en-tête d’un fichier .exe.  
  
   Pour plus d’informations, consultez l’article [/RELEASE (Définir le total de Checksum)](http://msdn.microsoft.com/library/93bcadf4-29ac-4824-914b-6997e3751d22).  
  
- **ShowProgress**  
  
   Paramètre **String** facultatif.  
  
   Spécifie le niveau de détail des rapports de progression de l’opération de liaison.  
  
   Spécifiez l'une des valeurs suivantes, chacune d'elles correspondant à une option de ligne de commande.  
  
  - **NotSet** - *\<aucune>*  
  
  - **LinkVerbose** - **/VERBOSE**  
  
  - **LinkVerboseLib** - **/VERBOSE:Lib**  
  
  - **LinkVerboseICF** - **/VERBOSE:ICF**  
  
  - **LinkVerboseREF** - **/VERBOSE:REF**  
  
  - **LinkVerboseSAFESEH** - **/VERBOSE:SAFESEH**  
  
  - **LinkVerboseCLR** - **/VERBOSE:CLR**  
  
    Pour plus d’informations, consultez l’article [/VERBOSE (Imprimer les messages d’avancement)](http://msdn.microsoft.com/library/9c347d98-4c37-4724-a39e-0983934693ab).  
  
- **Sources**  
  
   Paramètre `ITaskItem[]` requis.  
  
   Définit un tableau d’éléments de fichier source MSBuild pouvant être consommés et émis par des tâches.  
  
- **SpecifySectionAttributes**  
  
   Paramètre **String** facultatif.  
  
   Indique les attributs d’une section. Il remplace les attributs qui ont été définis lorsque le fichier .obj correspondant à la section a été compilé.  
  
   Pour plus d’informations, consultez l’article [/SECTION (Spécifier les attributs de section)](http://msdn.microsoft.com/library/92b69d81-e421-462e-b46f-7d0dff9b9d16).  
  
- **StackCommitSize**  
  
   Paramètre **String** facultatif.  
  
   Spécifie la quantité de mémoire physique contenue dans chaque allocation lorsque de la mémoire supplémentaire est allouée.  
  
   Pour plus d’informations, consultez l’argument `commit` dans l’article [/STACK (Allocations de la pile)](http://msdn.microsoft.com/library/73283660-e4bd-47cc-b5ca-04c5d739034c).  
  
- **StackReserveSize**  
  
   Paramètre **String** facultatif.  
  
   Spécifie la taille totale d’allocation de piles dans la mémoire virtuelle.  
  
   Pour plus d’informations, consultez l’argument `reserve` dans l’article [/STACK (Allocations de la pile)](http://msdn.microsoft.com/library/73283660-e4bd-47cc-b5ca-04c5d739034c).  
  
- **StripPrivateSymbols**  
  
   Paramètre **String** facultatif.  
  
   Crée un second fichier de base de données du programme (PDB) qui omet les symboles que vous ne souhaitez pas distribuer à vos clients. Spécifiez le nom du second fichier PDB.  
  
   Pour plus d’informations, consultez l’article [/PDBSTRIPPED (Supprimer les symboles privés)](http://msdn.microsoft.com/library/9b9e0070-6a13-4142-8180-19c003fbbd55).  
  
- **SubSystem**  
  
   Paramètre **String** facultatif.  
  
   Spécifie l'environnement pour l'exécutable.  
  
   Spécifiez l'une des valeurs suivantes, chacune d'elles correspondant à une option de ligne de commande.  
  
  - **NotSet** - *\<aucune>*  
  
  - **Console** - **/SUBSYSTEM:CONSOLE**  
  
  - **Windows** - **/SUBSYSTEM:WINDOWS**  
  
  - **Native** - **/SUBSYSTEM:NATIVE**  
  
  - **EFI Application** - **/SUBSYSTEM:EFI_APPLICATION**  
  
  - **EFI Boot Service Driver** - **/SUBSYSTEM:EFI_BOOT_SERVICE_DRIVER**  
  
  - **EFI ROM** - **/SUBSYSTEM:EFI_ROM**  
  
  - **EFI Runtime** - **/SUBSYSTEM:EFI_RUNTIME_DRIVER**  
  
  - **WindowsCE** - **/SUBSYSTEM:WINDOWSCE**  
  
  - **POSIX** - **/SUBSYSTEM:POSIX**  
  
    Pour plus d’informations, consultez l’article [/SUBSYSTEM (Spécifier le sous-système)](http://msdn.microsoft.com/library/d7b133cf-cf22-4da8-ab46-6552702c0b9b).  
  
- **SupportNobindOfDelayLoadedDLL**  
  
   Paramètre **Boolean** facultatif.  
  
   Si `true`, indique à l’Éditeur de liens de ne pas inclure dans l’image finale de table IAT (Import Address Table).  
  
   Pour plus d’informations, consultez l’argument `NOBIND` dans l’article [/DELAY (Paramètres d’importation à chargement différé)](http://msdn.microsoft.com/library/9334b332-cc58-4dae-b10f-a4c75972d50c).  
  
- **SupportUnloadOfDelayLoadedDLL**  
  
   Paramètre **Boolean** facultatif.  
  
   Si `true`, indique à la fonction d’assistance de chargement différé de prendre en charge le déchargement explicite de la DLL.  
  
   Pour plus d’informations, consultez l’argument `UNLOAD` dans l’article [/DELAY (Paramètres d’importation à chargement différé)](http://msdn.microsoft.com/library/9334b332-cc58-4dae-b10f-a4c75972d50c).  
  
- **SuppressStartupBanner**  
  
   Paramètre **Boolean** facultatif.  
  
   Si la valeur est `true`, empêche l'affichage du message de copyright et de numéro de version quand la tâche démarre.  
  
   Pour plus d’informations, consultez l’article [/NOLOGO (Suppression de la bannière de démarrage) (Éditeur de liens)](http://msdn.microsoft.com/library/3b20dddd-eca6-4545-a331-9f70bf720197).  
  
- **SwapRunFromCD**  
  
   Paramètre **Boolean** facultatif.  
  
   Si `true`, indique au système d’exploitation de copier tout d’abord la sortie de l’Éditeur de liens dans un fichier d’échange, puis d’y exécuter l’image.  
  
   Pour plus d’informations, consultez l’argument `CD` dans l’article [/SWAPRUN (Charger la sortie de l’Éditeur de liens dans le fichier d’échange)](http://msdn.microsoft.com/library/4a1e7f46-4399-4161-8dfc-d6a71beaf683). Consultez également le paramètre **SwapRunFromNET**.  
  
- **SwapRunFromNET**  
  
   Paramètre **Boolean** facultatif.  
  
   Si `true`, indique au système d’exploitation de copier tout d’abord la sortie de l’Éditeur de liens dans un fichier d’échange, puis d’y exécuter l’image.  
  
   Pour plus d’informations, consultez l’argument `NET` dans l’article [/SWAPRUN (Charger la sortie de l’Éditeur de liens dans le fichier d’échange)](http://msdn.microsoft.com/library/4a1e7f46-4399-4161-8dfc-d6a71beaf683). Reportez-vous également au paramètre **SwapRunFromCD** de ce tableau.  
  
- **TargetMachine**  
  
   Paramètre **String** facultatif.  
  
   Spécifie la plateforme cible du programme ou de la DLL.  
  
   Spécifiez l'une des valeurs suivantes, chacune d'elles correspondant à une option de ligne de commande.  
  
  - **NotSet** - *\<aucune>*  
  
  - **MachineARM** - **/MACHINE:ARM**  
  
  - **MachineEBC** - **/MACHINE:EBC**  
  
  - **MachineIA64** - **/MACHINE:IA64**  
  
  - **MachineMIPS** - **/MACHINE:MIPS**  
  
  - **MachineMIPS16** - **/MACHINE:MIPS16**  
  
  - **MachineMIPSFPU** - **/MACHINE:MIPSFPU**  
  
  - **MachineMIPSFPU16** - **/MACHINE:MIPSFPU16**  
  
  - **MachineSH4** - **/MACHINE:SH4**  
  
  - **MachineTHUMB** - **/MACHINE:THUMB**  
  
  - **MachineX64** - **/MACHINE:X64**  
  
  - **MachineX86** - **/MACHINE:X86**  
  
    Pour plus d’informations, consultez l’article [/MACHINE (Spécifier la plateforme cible)](http://msdn.microsoft.com/library/8d41bf4b-7e53-4ab9-9085-d852b08d31c2).  
  
- **TerminalServerAware**  
  
   Paramètre **Boolean** facultatif.  
  
   Si `true`, définit un indicateur dans le champ DllCharacteristics IMAGE_OPTIONAL_HEADER de l’en-tête facultatif de l’image du programme. Si cet indicateur est défini, le serveur Terminal Server n’apportera aucune modification à l’application.  
  
   Pour plus d’informations, consultez l’article [/TSAWARE (Créer une application sensible à Terminal Server)](http://msdn.microsoft.com/library/fe1c1846-de5b-4839-b562-93fbfe36cd29).  
  
- **TrackerLogDirectory**  
  
   Paramètre **String** facultatif.  
  
   Spécifie le répertoire du journal de Tracker.  
  
- **TreatLinkerWarningAsErrors**  
  
   Paramètre **Boolean** facultatif.  
  
   Si `true`, aucun fichier de sortie n’est créé lorsque l’Éditeur de liens génère un avertissement.  
  
   Pour plus d’informations, consultez l’article [/WX (Traiter les avertissements de l’Éditeur de liens comme des erreurs)](http://msdn.microsoft.com/library/e4ba97c7-93f7-43ae-a4bb-d866790926c9).  
  
- **TurnOffAssemblyGeneration**  
  
   Paramètre **Boolean** facultatif.  
  
   Si `true`, crée une image du fichier de sortie actif sans générer un assembly .NET Framework.  
  
   Pour plus d’informations, consultez l’article [/NOASSEMBLY (Créer un module MSIL)](http://msdn.microsoft.com/library/3cea4e70-f451-4395-a626-1930b1b127fe).  
  
- **TypeLibraryFile**  
  
   Paramètre **String** facultatif.  
  
   Indique le nom et l’extension de nom du fichier .tlb. Spécifiez un nom de fichier, ou un chemin d’accès et un nom de fichier.  
  
   Pour plus d’informations, consultez l’article [/TLBOUT (Nommer le fichier .TLB)](http://msdn.microsoft.com/library/0df6d078-2e48-46c9-a1a5-02674d85dce8).  
  
- **TypeLibraryResourceID**  
  
   Paramètre **entier** facultatif.  
  
   Désigne une valeur spécifiée par l’utilisateur pour une bibliothèque de types créé par l’Éditeur de liens. Spécifiez une valeur comprise entre 1 et 65535.  
  
   Pour plus d’informations, consultez l’article [/TLBID (Spécifier l’ID de ressource de TypeLib)](http://msdn.microsoft.com/library/434b28a2-4656-4d52-ac82-8b18bf486fb2).  
  
- **UACExecutionLevel**  
  
   Paramètre **String** facultatif.  
  
   Spécifie le niveau d’exécution demandé pour l’application lorsqu’elle est exécutée avec le Contrôle de compte d’utilisateur.  
  
   Spécifiez l'une des valeurs suivantes, chacune d'elles correspondant à une option de ligne de commande.  
  
  - **AsInvoker** - `level='asInvoker'`  
  
  - **HighestAvailable** - `level='highestAvailable'`  
  
  - **RequireAdministrator** - `level='requireAdministrator'`  
  
    Pour plus d’informations, consultez l’argument `level` dans l’article [/MANIFESTUAC (Incorporer des informations sur le contrôle de compte d’utilisateur dans le manifeste)](http://msdn.microsoft.com/library/2d243c39-fa13-493c-b56f-d0d972a1603a).  
  
- **UACUIAccess**  
  
   Paramètre **Boolean** facultatif.  
  
   Si `true`, l’application ignore les niveaux de protection de l’interface utilisateur et exécute l’entrée vers des fenêtres d’autorisations supérieures sur le Bureau. Dans le cas contraire, `false`.  
  
   Pour plus d’informations, consultez l’argument `uiAccess` dans l’article [/MANIFESTUAC (Incorporer des informations sur le contrôle de compte d’utilisateur dans le manifeste)](http://msdn.microsoft.com/library/2d243c39-fa13-493c-b56f-d0d972a1603a).  
  
- **UseLibraryDependencyInputs**  
  
   Paramètre **Boolean** facultatif.  
  
   Si `true`, les entrées de l’outil Générateur de bibliothèques sont utilisées à la place du fichier bibliothèque lors de la liaison des sorties de bibliothèque des dépendances du projet.  
  
- **Version**  
  
   Paramètre **String** facultatif.  
  
   Insère un numéro de version dans l’en-tête du fichier .exe ou .dll. Spécifiez « `major[.minor]` ». Les arguments `major` et `minor` sont des nombres décimaux compris entre 0 et 65535.  
  
   Pour plus d’informations, consultez l’article [/VERSION (Informations de version)](http://msdn.microsoft.com/library/b86d0e86-dca6-4316-aee2-d863ccb9f223).  
  
## <a name="see-also"></a>Voir aussi  
 [Task Reference (Informations de référence sur les tâches MSBuild)](../msbuild/msbuild-task-reference.md)



