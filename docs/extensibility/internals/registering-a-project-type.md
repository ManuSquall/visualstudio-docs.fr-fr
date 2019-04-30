---
title: L’inscription d’un Type de projet | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], new project registry entries
- registry, new project types
- registration, new project types
ms.assetid: dfc0e231-6b4e-447d-9d64-0e66dea3394a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fccd422a0f24a65532e648a1254aecedc484903e
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63425674"
---
# <a name="registering-a-project-type"></a>Inscription d’un type de projet
Lorsque vous créez un nouveau type de projet, vous devez créer les entrées de Registre qui permettent [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] à reconnaître et à travailler avec votre type de projet. En règle générale, vous créez ces entrées de Registre à l’aide d’un fichier de script (d’inscription.rgs) du Registre.

 Dans l’exemple ci-dessous, les instructions à partir du Registre fournissent des chemins d’accès par défaut et les données, le cas échéant, suivie d’une table qui contient des entrées à partir du script de Registre pour chaque instruction. Les tableaux fournissent les entrées du script et des informations supplémentaires sur les instructions.

> [!NOTE]
> Les informations de Registre suivantes sont destinées à être un exemple du type et à des fins des entrées dans les scripts de Registre que vous l’écrivez pour enregistrer votre type de projet. Vos entrées réelles et leurs utilisations peuvent varier en fonction des besoins spécifiques de votre type de projet. Vous devez passez en revue les exemples disponibles pour en trouver un qui ressemble le type de projet que vous développez et puis passez en revue le script de Registre pour cet exemple.

 Les exemples suivants proviennent de HKEY_CLASSES_ROOT.

## <a name="example"></a>Exemple

```
\.figp
   @="FigPrjFile"
   "Content Type"="text/plain"
\.figp\ShellNew
   "NullFile"=""
\FigPrjFile
   @="Figure Project File"
\DefaultIcon
   @="<Visual Studio SDK installation path>\\9.0VSIntegration\\SomeFolder\\FigPkgs\\FigPrj\\Debug\\FigPrj.dll,-206"
\shell\open
   @="&Open in Visual Studio"
\shell\open\command
   @="devenv.exe \"%1\""
```

|Nom|Type|Données|Description|
|----------|----------|----------|-----------------|
|`@`|REG_SZ|`FigPrjFile`|Nom et description des fichiers du type de projet qui ont l’extension .figp.|
|`Content Type`|REG_SZ|`Text/plain`|Type de contenu pour les fichiers de projet.|
|`NullFile`|REG_SZ|`Null`||
|`@`|REG_SZ|`%MODULE%,-206`|Icône par défaut utilisé pour le projet de ce type. L’instruction % MODULE % est terminée dans le Registre à l’emplacement par défaut du type de projet DLL.|
|`@`|REG_SZ|`&Open in Visual Studio`|Application par défaut dans lequel ce type de projet doit être ouvert.|
|`@`|REG_SZ|`devenv.exe "%1"`|Commande par défaut qui est exécutée lorsqu’un projet de ce type est ouvert.|

 Les exemples suivants sont à partir de HKEY_LOCAL_MACHINE et se trouvent dans le Registre sous la clé [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\99.0Exp\Packages].

## <a name="example"></a>Exemple

```
\{ACEF4EB2-57CF-11D2-96F4-000000000000} (The CLSID for the VSPackage)
   @="FigPrj Project Package"
   "InprocServer32"="9.0<Visual Studio SDK installation path>\\VSIntegration\\Archive\\FigPkgs\\FigPrj\\                      Debug\\FigPrj.dll"
   "CompanyName"="Microsoft"
   "ProductName"="Figure Project Sample"
   "ProductVersion"="9.0"
   "MinEdition"="professional"
   "ID"=dword:00000001
\{ACEF4EB2-57CF-11D2-96F4-000000000000}\SatelliteDLL
   "DllName"="FigPrjUI.dll"
   "Path"="9.0<Visual Studio SDK installation path>\\VSIntegration\\Archive\\FigPkgs\\FigPrj\\Debug\\"
\{ACEF4EB2-57CF-11D2-96F4-000000000000}\Automation
   "FigProjects"=""
\{ACEF4EB2-57CF-11D2-96F4-000000000000}\AutomationEvents
   "FigProjectsEvents"="Returns the FigProjectsEvents Object"
   "FigProjectItemsEvents"="Returns the FigProjectItemsEvents Object"
```

|Nom|Type|Données|Description|
|----------|----------|----------|-----------------|
|`@` (Valeur par défaut)|REG_SZ|`FigPrj Project VSPackage`|Nom localisé de ce inscrit un VSPackage (type de projet).|
|`InprocServer32`|REG_SZ|`%MODULE%`|Chemin d’accès du type de projet DLL. L’IDE se charge de cette DLL et transmet le CLSID VSPackage à `DllGetClassObject` pour obtenir <xref:Microsoft.VisualStudio.OLE.Interop.IClassFactory> pour construire le <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> objet.|
|`CompanyName`|REG_SZ|`Microsoft`|Nom de la société qui a développé le type de projet.|
|`ProductName`|REG_SZ|`Figure Project Sample`|Nom du type de projet.|
|`ProductVersion`|REG_SZ|`9.0`|Numéro de version du type de projet de mise en production.|
|`MinEdition`|REG_SZ|`professional`|Édition du VSPackage en cours d’inscription.|
|`ID`|REG_DWORD|`%IDS_PACKAGE_LOAD_KEY%`|Le package de charger la clé pour le projet VSPackage. La clé est validée quand un projet est chargé après le démarrage de l’environnement.|
|`DllName`|REG_SZ|`%RESOURCE_DLL%`|Nom de fichier de la DLL satellite contenant des ressources localisées pour le type de projet.|
|`Path`|REG_SZ|`%RESOURCE_PATH%`|Chemin d’accès de la DLL satellite.|
|`FigProjectsEvents`|REG_SZ|Consultez la déclaration de valeur.|Détermine la chaîne de texte renvoyée pour cet événement automation.|
|`FigProjectItemsEvents`|REG_SZ|Consultez la déclaration de valeur.|Détermine la chaîne de texte renvoyée pour cet événement automation.|

 Les exemples suivants se trouvent dans le Registre sous la clé [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Projects].

## <a name="example"></a>Exemple

```
\{C061DB26-5833-11D2-96F5-000000000000} (The CLSID for projects of this type)
   @="FigPrj Project"
   "DisplayName"="#2"
   "Package"="{ACEF4EB2-57CF-11D2-96F4-000000000000}"
   "ProjectTemplatesDir"="C:\\Program Files\\VSIP 9.0\\EnvSDK\\FigPkgs\\                           FigPrj\\FigPrjProjects"
   "ItemTemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\                           FigPrjProjectItems"
   "DisplayProjectFileExtensions"="#3"
   "PossibleProjectExtensions"="figp"
   "DefaultProjectExtension"=".figp"
\{C061DB26-5833-11D2-96F5-000000000000}\Filters\1       (Folder 1 contains settings for Open Files filters.)
   @="#4"
   "CommonOpenFilesFilter"=dword:00000000
   "CommonFindFilesFilter"=dword:00000000
   "NotAddExistingItemFilter"=dword:00000000
   "FindInFilesFilter"=dword:00000000
   "NotOpenFileFilter"=dword:00000000
   "SortPriority"=dword:000003e8
\{C061DB26-5833-11D2-96F5-000000000000}\Filters\2
      (Folder 2 contains settings for Find in Files filters.)
   @="#5"
   "CommonOpenFilesFilter"=dword:00000000
   "CommonFindFilesFilter"=dword:00000000
   "NotAddExistingItemFilter"=dword:00000001
   "FindInFilesFilter"=dword:00000001
   "NotOpenFileFilter"=dword:00000000
   "SortPriority"=dword:000003e8
\{C061DB26-5833-11D2-96F5-000000000000}\AddItemTemplates\TemplateDirs\ {ACEF4EB2-57CF-11D2-96F4-000000000000}\1 (Second GUID indicates the registered project type for the Add Items templates.)
   @="#6"
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\                    FigPrjProjectItems"
   "SortPriority"=dword:00000064
```

|Nom|Type|Données|Description|
|----------|----------|----------|-----------------|
|`@`|REG_SZ|`FigPrj Project`|Nom par défaut des projets de ce type.|
|`DisplayName`|REG_SZ|`#%IDS_PROJECT_TYPE%`|ID de ressource du nom doivent être extraites de la DLL satellite inscrit sous Packages.|
|`Package`|REG_SZ|`%CLSID_Package%`|ID de classe du VSPackage inscrit sous Packages.|
|`ProjectTemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|Chemin d’accès de la valeur par défaut des fichiers de modèle de projet. Il s’agit de fichiers affichés par le modèle de projet.|
|`ItemTemplatesDir`|REG_SZ|`%TEMPLATE_PATH% \FigPrjProjectItems`|Chemin d’accès de la valeur par défaut des fichiers de modèle d’élément de projet. Il s’agit de fichiers affichés par le modèle d’ajouter un nouvel élément.|
|`DisplayProjectFileExtensions`|REG_SZ|`#%IDS_DISPLAY_PROJ_FILE_EXT%`|Permet à l’IDE implémenter le **Open** boîte de dialogue.|
|`PossibleProjectExtensions`|REG_SZ|`figp`|Utilisé par l’IDE pour déterminer si le projet en cours d’ouverture est géré par ce type de projet (fabrique de projet). Le format pour plus d’une entrée est une liste délimitée par des points-virgules. Par exemple « vdproj ; vdp ».|
|`DefaultProjectExtension`|REG_SZ|`.figp`|Utilisé par l’IDE en tant que l’extension de nom de fichier par défaut pour l’opération Enregistrer sous.|
|`Filter Settings`|REG_DWORD|Différents, consultez les instructions et commentaires tableau suivant.|Ces paramètres sont utilisés pour définir les différents filtres pour afficher les fichiers dans les boîtes de dialogue de l’interface utilisateur.|
|`@`|REG_SZ|`#%IDS_ADDITEM_TEMPLATES_ENTRY%`|ID de ressource pour les modèles d’ajouter un élément.|
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjectItems`|Chemin d’accès des éléments de projet affiché dans la boîte de dialogue pour le **ajouter un nouvel élément** modèle.|
|`SortPriority`|REG_DWORD|`100 (vcprx64)`|Détermine l’ordre de tri dans le nœud d’arbre de fichiers affichés dans le **ajouter un nouvel élément** boîte de dialogue.|

 Le tableau suivant montre les options de filtres disponibles dans le segment de code précédent.

|Option de filtre|Description|
|-------------------|-----------------|
|`CommonFindFilesFilter`|Indique que le filtre est l’un des filtres courants dans le **rechercher dans les fichiers** boîte de dialogue. Les filtres courants sont répertoriés dans la liste des filtres avant les filtres ne pas marqué comme commun.|
|`CommonOpenFilesFilter`|Indique que le filtre est l’un des filtres courants dans le **ouvrir un fichier** boîte de dialogue. Les filtres courants sont répertoriés dans la liste des filtres avant les filtres ne pas marqué comme commun.|
|`FindInFilesFilter`|Indique que le filtre est l’un des filtres dans les **rechercher dans les fichiers** boîte de dialogue zone et sont répertoriés après les filtres courants.|
|`NotOpenFileFilter`|Indique que le filtre ne sera pas utilisé dans le **ouvrir un fichier** boîte de dialogue.|
|`NotAddExistingItemFilter`|Indique que le filtre ne sera pas utilisé dans la zone Ajouter **élément existant** boîte de dialogue.|

 Par défaut, si un filtre de ne pas avoir une ou plusieurs de ces indicateurs définis, le filtre est utilisé dans le **ajouter un élément existant** boîte de dialogue et le **ouvrir un fichier** boîte de dialogue une fois les filtres courants sont répertoriés. Le filtre n’est pas utilisé dans le **rechercher dans les fichiers** boîte de dialogue.

 Les exemples suivants se trouvent dans le Registre sous la clé [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Projects].

## <a name="example"></a>Exemple

```
{FE3BBBB6-72D5-11d2-9ACE-00C04F79A2A4} (The CLSID for Enterprise Projects)
\{FE3BBBB6-72D5-11d2-9ACE-00C04F79A2A4}\AddItemTemplates\TemplateDirs\ {ACEF4EB2-57CF-11D2-96F4-000000000000}\1 (CLSID for projects of this type)
   @="#7"
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPrj\\FigPrjProjects"
   "SortPriority"=dword:00000029
   "NewProjectDialogOnly"=dword:00000000
```

|Nom|Type|Données|Description|
|----------|----------|----------|-----------------|
|`@`|REG_SZ|`#%IDS_NEWPROJ_ TEMPLATES_ENTRY%`|ID de ressource pour les modèles de projet.|
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|Par défaut le chemin d’accès pour les projets du type de projet enregistré.|
|`SortPriority`|REG_DWORD|`41 (x29)`|Jeux ordre de tri des projets s’affiché dans la boîte de dialogue Assistant nouveaux projets.|
|`NewProjectDialogOnly`|REG_DWORD|`0`|0 indique que les projets de ce type sont affichés uniquement dans la boîte de dialogue Nouveau projet.|

 Les exemples suivants se trouvent dans le Registre sous la clé [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Projects].

## <a name="example"></a>Exemple

```
\{A2FE74E1-B743-11d0-AE1A-00A0C90FFFC3} (CLSID for Miscellaneous Files projects)
   @="Miscellaneous Files Project"
\AddItemTemplates\TemplateDirs\{ACEF4EB2-57CF-11D2-96F4-000000000000}\1
                                 (CLSID for Figures Project projects)
   @="#6"
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\                    FigPrjProjectItems"
   "SortPriority"=dword:00000064
```

|Nom|Type|Données|Description|
|----------|----------|----------|-----------------|
|`@`|REG_SZ|Aucun.|Valeur par défaut qui indique que les entrées suivantes sont pour les entrées de projets fichiers divers.|
|`@`|REG_SZ|`#%IDS_ADDITEM_TEMPLATES_ENTRY%`|Valeur d’ID de ressource pour les fichiers de modèle d’ajouter de nouveaux éléments.|
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjectItems`|Chemin d’accès par défaut des éléments qui s’affichera dans le **ajouter un nouvel élément** boîte de dialogue.|
|`SortPriority`|REG_DWORD|`100 (vcprx64)`|Établit l’ordre de tri pour l’affichage dans le nœud d’arbre de la **ajouter un nouvel élément** boîte de dialogue.|

 L’exemple suivant se trouve dans le Registre sous la clé [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Menus].

## <a name="example"></a>Exemple

```
"{ACEF4EB2-57CF-11D2-96F4-000000000000}"=",1000,1"
```

 L’entrée de menu pointe l’IDE à la ressource utilisée pour récupérer les informations de menu. Lorsque ces données ont été fusionnées dans la base de données de menu, la même clé sera ajoutée dans la section MenusMerged du Registre. Le VSPackage doit ne rien modifier sous la section MenusMerged directement. Dans le champ de données dans le tableau suivant, il existe trois virgules-champs séparés par des. Le premier champ identifie un chemin d’accès complet d’un fichier de ressources de menu :

- Si le premier champ est omis, la ressource de menu est chargée à partir de la DLL identifié par le GUID du VSPackage satellite.

  Le deuxième champ identifie un ID de ressource de menu du type CTMENU :

- Si l’ID de ressource est spécifié, et le chemin d’accès de fichier est fourni par le premier paramètre, une ressource de menu est chargée à partir du chemin de fichier complet.

- Si l’ID de ressource est fourni, mais le chemin d’accès de fichier n’est pas, la ressource de menu est chargée à partir de la DLL satellite.

- Si le chemin d’accès de fichier complet est fourni et l’ID de ressource est omis, le fichier à charger est censé être un fichier de directeur technique.

  Le dernier champ identifie le numéro de version pour la ressource CTMENU. Vous pouvez fusionner à nouveau le menu en modifiant le numéro de version.

|Nom|Type|Données|Description|
|----------|----------|----------|-----------------|
|%CLSID_Package%|REG_SZ|`,1000,1`|La ressource à récupérer les informations de menu.|

 Les exemples suivants se trouvent dans le Registre sous la clé [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\NewProjectTemplates].

```
\TemplateDirs\{ACEF4EB2-57CF-11D2-96F4-000000000000}\1                (CLSID for Figures Project projects)
   @="#7"
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\FigPrjProjects"
   "SortPriority"=dword:00000029
   "NewProjectDialogOnly"=dword:00000000
```

|Nom|Type|Données|Description|
|----------|----------|----------|-----------------|
|`@`|REG_SZ|`#%IDS_NEWPROJ_TEMPLATES_ENTRY%`|Valeur d’ID de ressource pour les modèles de projet Figures nouveau projet.|
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|Chemin d’accès de la valeur par défaut du répertoire de nouveaux projets. Éléments dans ce répertoire s’afficheront dans le **Assistant Nouveau projet** boîte de dialogue.|
|`SortPriority`|REG_DWORD|`41 (x29)`|Établit l’ordre dans lequel les projets seront affichera dans le nœud d’arbre de la **nouveau projet** boîte de dialogue.|
|`NewProjectDialogOnly`|REG_DWORD|`0`|0 indique que les projets de ce type sont affichés uniquement dans le **nouveau projet** boîte de dialogue.|

 L’exemple suivant se trouve dans le Registre sous la clé [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\InstalledProducts].

```
\FiguresProductSample
   "Package"="{ACEF4EB2-57CF-11D2-96F4-000000000000}"
   "UseInterface"=dword:00000001
```

|Nom|Type|Données|Description|
|----------|----------|----------|-----------------|
|`Package`|REG_SZ|`%CLSID_Package%`|ID de classe du VSPackage inscrit.|
|`UseInterface`|REG_DWORD|`1`|1 indique que l’interface utilisateur doit être utilisée pour interagir avec ce projet. 0 indique qu’il n’existe aucune interface de l’interface utilisateur.|

 Fichiers the.vsz contrôlent fréquemment de nouveaux types de projet contiennent une entrée RELATIVE_PATH. Ce chemin d’accès est relatif à chemin d’accès spécifié sous l’entrée \ProductDir du type de projet dans la clé d’installation suivante :

 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\7.0Exp\Setup

 Par exemple, les modèles de projet Enterprise Frameworks ajoutent les entrées de Registre suivantes :

 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\7.0Exp\Setup\EF\ProductDir = C:\Program Files\Microsoft Visual Studio\EnterpriseFrameworks\

 Cela signifie que si vous incluez un PROJECT_TYPE = entrée EF dans le fichier .vsz, la recherche d’environnement votre .vsz des fichiers dans le répertoire ProductDir spécifié précédemment.

## <a name="see-also"></a>Voir aussi
- [Liste de contrôle : Création de nouveaux types de projets](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Éléments d’un modèle de projet](../../extensibility/internals/elements-of-a-project-model.md)
- [Création d’instances de projets à l’aide de fabriques de projets](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)