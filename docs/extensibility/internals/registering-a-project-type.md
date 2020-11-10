---
title: Inscription d’un type de projet | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], new project registry entries
- registry, new project types
- registration, new project types
ms.assetid: dfc0e231-6b4e-447d-9d64-0e66dea3394a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7267060f2207b0842885dc3001c3926874be30a9
ms.sourcegitcommit: 023f52f10fb91850824558478cbfd2ec965054f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94407729"
---
# <a name="registering-a-project-type"></a>Inscription d’un type de projet
Lorsque vous créez un nouveau type de projet, vous devez créer des entrées de Registre qui permettent [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] à de reconnaître et d’utiliser votre type de projet. En général, vous créez ces entrées de Registre à l’aide d’un fichier de script de Registre (. RGS).

 Dans l’exemple ci-dessous, les instructions du Registre fournissent des chemins d’accès et des données par défaut, le cas échéant, suivis d’une table qui contient des entrées du script de Registre pour chaque instruction. Les tables fournissent les entrées de script et des informations supplémentaires sur les instructions.

> [!NOTE]
> Les informations de Registre suivantes sont destinées à illustrer le type et les objectifs des entrées dans les scripts de registre que vous allez écrire pour inscrire votre type de projet. Vos entrées réelles et leurs utilisations peuvent varier en fonction des exigences spécifiques de votre type de projet. Vous devez examiner les exemples disponibles pour en trouver un qui ressemble de près au type de projet que vous développez, puis examiner le script de Registre pour cet exemple.

 Les exemples suivants proviennent de HKEY_CLASSES_ROOT.

## <a name="example-1"></a>Exemple 1

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
|`@`|REG_SZ|`FigPrjFile`|Nom et description des fichiers de type de projet avec l’extension. figp.|
|`Content Type`|REG_SZ|`Text/plain`|Type de contenu pour les fichiers projet.|
|`NullFile`|REG_SZ|`Null`||
|`@`|REG_SZ|`%MODULE%,-206`|Icône par défaut utilisée pour le projet de ce type. L’instruction% MODULE% est effectuée dans le registre à l’emplacement par défaut de la DLL du type de projet.|
|`@`|REG_SZ|`&Open in Visual Studio`|Application par défaut dans laquelle ce type de projet sera ouvert.|
|`@`|REG_SZ|`devenv.exe "%1"`|Commande par défaut qui est exécutée quand un projet de ce type est ouvert.|

 Les exemples suivants proviennent de HKEY_LOCAL_MACHINE et sont situés dans le Registre sous la clé [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\99.0Exp\Packages].

## <a name="example-2"></a>Exemple 2

```
\{ACEF4EB2-57CF-11D2-96F4-000000000000} (The CLSID for the VSPackage)
   @="FigPrj Project Package"
   "InprocServer32"="9.0<Visual Studio SDK installation path>\\VSIntegration\\Archive\\FigPkgs\\FigPrj\\                      Debug\\FigPrj.dll"
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
|`@` (valeur par défaut)|REG_SZ|`FigPrj Project VSPackage`|Nom localisable de ce VSPackage inscrit (type de projet).|
|`InprocServer32`|REG_SZ|`%MODULE%`|Chemin d’accès de la DLL du type de projet. L’IDE charge cette DLL et transmet le CLSID du VSPackage à `DllGetClassObject` pour <xref:Microsoft.VisualStudio.OLE.Interop.IClassFactory> créer l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> objet.|
|`CompanyName`|REG_SZ|`Microsoft`|Nom de la société qui a développé le type de projet.|
|`ProductName`|REG_SZ|`Figure Project Sample`|Nom du type de projet.|
|`ProductVersion`|REG_SZ|`9.0`|Numéro de version de la version du type de projet.|
|`MinEdition`|REG_SZ|`professional`|Édition du VSPackage en cours d’inscription.|
|`ID`|REG_DWORD|`%IDS_PACKAGE_LOAD_KEY%`|Clé de chargement du package pour le VSPackage du projet. La clé est validée lorsqu’un projet est chargé après le démarrage de l’environnement.|
|`DllName`|REG_SZ|`%RESOURCE_DLL%`|Nom de fichier de la DLL satellite qui contient les ressources localisées pour le type de projet.|
|`Path`|REG_SZ|`%RESOURCE_PATH%`|Chemin d’accès de la DLL satellite.|
|`FigProjectsEvents`|REG_SZ|Consultez l’instruction pour value.|Détermine la chaîne de texte retournée pour cet événement Automation.|
|`FigProjectItemsEvents`|REG_SZ|Consultez l’instruction pour value.|Détermine la chaîne de texte retournée pour cet événement Automation.|

 Tous les exemples suivants se trouvent dans le Registre sous la clé [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Projects].

## <a name="example-3"></a>Exemple 3

```
\{C061DB26-5833-11D2-96F5-000000000000} (The CLSID for projects of this type)
   @="FigPrj Project"
   "DisplayName"="#2"
   "Package"="{ACEF4EB2-57CF-11D2-96F4-000000000000}"
   "ProjectTemplatesDir"="C:\\Program Files\\VSIP 9.0\\EnvSDK\\FigPkgs\\                           FigPrj\\FigPrjProjects"
   "ItemTemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\                           FigPrjProjectItems"
   "DisplayProjectFileExtensions"="#3"
   "PossibleProjectExtensions"="figp"
   "DefaultProjectExtension"=".figp"
\{C061DB26-5833-11D2-96F5-000000000000}\Filters\1       (Folder 1 contains settings for Open Files filters.)
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
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\                    FigPrjProjectItems"
   "SortPriority"=dword:00000064
```

|Nom|Type|Données|Description|
|----------|----------|----------|-----------------|
|`@`|REG_SZ|`FigPrj Project`|Nom par défaut des projets de ce type.|
|`DisplayName`|REG_SZ|`#%IDS_PROJECT_TYPE%`|ID de ressource du nom à récupérer à partir de la DLL satellite inscrite sous packages.|
|`Package`|REG_SZ|`%CLSID_Package%`|ID de classe du VSPackage inscrit sous packages.|
|`ProjectTemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|Chemin d’accès par défaut des fichiers de modèles de projet. Il s’agit des fichiers affichés par le nouveau modèle de projet.|
|`ItemTemplatesDir`|REG_SZ|`%TEMPLATE_PATH% \FigPrjProjectItems`|Chemin d’accès par défaut des fichiers de modèle d’élément de projet. Il s’agit des fichiers affichés par le modèle ajouter un nouvel élément.|
|`DisplayProjectFileExtensions`|REG_SZ|`#%IDS_DISPLAY_PROJ_FILE_EXT%`|Permet à l’IDE d’implémenter la boîte de dialogue **ouvrir** .|
|`PossibleProjectExtensions`|REG_SZ|`figp`|Utilisé par l’IDE pour déterminer si le projet en cours d’ouverture est géré par ce type de projet (fabrique de projets). Le format de plusieurs entrées est une liste délimitée par des points-virgules. Par exemple, « vdproj ; VDP ».|
|`DefaultProjectExtension`|REG_SZ|`.figp`|Utilisé par l’IDE comme extension de nom de fichier par défaut pour l’opération Enregistrer sous.|
|`Filter Settings`|REG_DWORD|Divers, consultez le tableau instructions et commentaires suivant.|Ces paramètres sont utilisés pour définir les différents filtres d’affichage des fichiers dans les boîtes de dialogue de l’interface utilisateur.|
|`@`|REG_SZ|`#%IDS_ADDITEM_TEMPLATES_ENTRY%`|ID de ressource pour ajouter des modèles d’élément.|
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjectItems`|Chemin d’accès des éléments de projet affichés dans la boîte de dialogue pour le modèle **Ajouter un nouvel élément** .|
|`SortPriority`|REG_DWORD|`100 (vcprx64)`|Détermine l’ordre de tri dans le nœud d’arbre des fichiers affichés dans la boîte de dialogue **Ajouter un nouvel élément** .|

 Le tableau suivant présente les options de filtres disponibles dans le segment de code précédent.

|Option de filtre|Description|
|-------------------|-----------------|
|`CommonFindFilesFilter`|Indique que le filtre est l’un des filtres les plus courants de la boîte de dialogue **Rechercher dans les fichiers** . Les filtres courants sont répertoriés dans la liste de filtres avant les filtres qui ne sont pas marqués comme communs.|
|`CommonOpenFilesFilter`|Indique que le filtre est l’un des filtres les plus courants de la boîte de dialogue **ouvrir un fichier** . Les filtres courants sont répertoriés dans la liste de filtres avant les filtres qui ne sont pas marqués comme communs.|
|`FindInFilesFilter`|Indique que le filtre sera l’un des filtres de la boîte de dialogue **Rechercher dans les fichiers** et sera listé après les filtres courants.|
|`NotOpenFileFilter`|Indique que le filtre ne sera pas utilisé dans la boîte de dialogue **ouvrir un fichier** .|
|`NotAddExistingItemFilter`|Indique que le filtre ne sera pas utilisé dans la boîte de dialogue Ajouter un **élément existant** .|

 Par défaut, si un ou plusieurs de ces indicateurs ne sont pas définis pour un filtre, le filtre est utilisé dans la boîte de dialogue **Ajouter un élément existant** et la boîte de dialogue **ouvrir un fichier** , une fois les filtres communs répertoriés. Le filtre n’est pas utilisé dans la boîte de dialogue **Rechercher dans les fichiers** .

 Tous les exemples suivants se trouvent dans le Registre sous la clé [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Projects].

## <a name="example-4"></a>Exemple 4

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
|`@`|REG_SZ|`#%IDS_NEWPROJ_ TEMPLATES_ENTRY%`|ID de ressource pour les nouveaux modèles de projet.|
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|Chemin d’accès par défaut des projets du type de projet inscrit.|
|`SortPriority`|REG_DWORD|`41 (x29)`|Définit l’ordre de tri des projets affichés dans la boîte de dialogue Assistant nouveaux projets.|
|`NewProjectDialogOnly`|REG_DWORD|`0`|0 indique que les projets de ce type s’affichent uniquement dans la boîte de dialogue Nouveau projet.|

 Tous les exemples suivants se trouvent dans le Registre sous la clé [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Projects].

## <a name="example-5"></a>Exemple 5

```
\{A2FE74E1-B743-11d0-AE1A-00A0C90FFFC3} (CLSID for Miscellaneous Files projects)
   @="Miscellaneous Files Project"
\AddItemTemplates\TemplateDirs\{ACEF4EB2-57CF-11D2-96F4-000000000000}\1
                                 (CLSID for Figures Project projects)
   @="#6"
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\                    FigPrjProjectItems"
   "SortPriority"=dword:00000064
```

|Nom|Type|Données|Description|
|----------|----------|----------|-----------------|
|`@`|REG_SZ|Aucun|Valeur par défaut qui indique que les entrées suivantes sont destinées aux entrées des projets fichiers divers.|
|`@`|REG_SZ|`#%IDS_ADDITEM_TEMPLATES_ENTRY%`|Valeur d’ID de ressource pour les fichiers de modèle d’ajout de nouveaux éléments.|
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjectItems`|Chemin d’accès par défaut des éléments qui seront affichés dans la boîte de dialogue **Ajouter un nouvel élément** .|
|`SortPriority`|REG_DWORD|`100 (vcprx64)`|Établit l’ordre de tri pour l’affichage dans le nœud de l’arborescence de la boîte de dialogue **Ajouter un nouvel élément** .|

 L’exemple suivant se trouve dans le Registre sous la clé [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Menus].

## <a name="example-6"></a>Exemple 6

```
"{ACEF4EB2-57CF-11D2-96F4-000000000000}"=",1000,1"
```

 L’entrée de menu pointe l’IDE vers la ressource utilisée pour récupérer les informations de menu. Lorsque ces données ont été fusionnées dans la base de données de menu, la même clé est ajoutée à la section MenusMerged du Registre. Le VSPackage ne doit pas modifier directement les éléments situés dans la section MenusMerged. Dans le champ de données du tableau suivant, il existe trois champs séparés par des virgules. Le premier champ identifie le chemin d’accès complet d’un fichier de ressources de menu :

- Si le premier champ est omis, la ressource de menu est chargée à partir de la DLL satellite identifiée par le GUID du VSPackage.

  Le deuxième champ identifie un ID de ressource de menu de type CTMENU :

- Si l’ID de ressource est spécifié et que le chemin d’accès du fichier est fourni par le premier paramètre, une ressource de menu est chargée à partir du chemin d’accès complet au fichier.

- Si l’ID de ressource est fourni, mais que le chemin d’accès au fichier n’est pas, la ressource de menu est chargée à partir de la DLL satellite.

- Si le chemin d’accès complet au fichier est fourni et que l’ID de ressource est omis, le fichier à charger est supposé être un fichier de directeur technique.

  Le dernier champ identifie le numéro de version de la ressource CTMENU. Vous pouvez fusionner à nouveau le menu en modifiant le numéro de version.

|Nom|Type|Données|Description|
|----------|----------|----------|-----------------|
|% CLSID_Package%|REG_SZ|`,1000,1`|Ressource permettant de récupérer les informations de menu.|

 Tous les exemples suivants se trouvent dans le Registre sous la clé [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\NewProjectTemplates].

```
\TemplateDirs\{ACEF4EB2-57CF-11D2-96F4-000000000000}\1                (CLSID for Figures Project projects)
   @="#7"
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\FigPrjProjects"
   "SortPriority"=dword:00000029
   "NewProjectDialogOnly"=dword:00000000
```

|Nom|Type|Données|Description|
|----------|----------|----------|-----------------|
|`@`|REG_SZ|`#%IDS_NEWPROJ_TEMPLATES_ENTRY%`|Valeur d’ID de ressource pour les figures projet de nouveaux modèles de projet.|
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|Chemin d’accès par défaut du nouveau répertoire de projets. Les éléments de ce répertoire s’affichent dans la boîte de dialogue **Assistant Nouveau projet** .|
|`SortPriority`|REG_DWORD|`41 (x29)`|Établit l’ordre dans lequel les projets seront affichés dans le nœud de l’arborescence de la boîte de dialogue **nouveau projet** .|
|`NewProjectDialogOnly`|REG_DWORD|`0`|0 indique que les projets de ce type s’affichent uniquement dans la boîte de dialogue **nouveau projet** .|

 L’exemple suivant se trouve dans le Registre sous la clé [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\InstalledProducts].

```
\FiguresProductSample
   "Package"="{ACEF4EB2-57CF-11D2-96F4-000000000000}"
   "UseInterface"=dword:00000001
```

|Nom|Type|Données|Description|
|----------|----------|----------|-----------------|
|`Package`|REG_SZ|`%CLSID_Package%`|ID de classe du VSPackage inscrit.|
|`UseInterface`|REG_DWORD|`1`|1 indique que l’interface utilisateur sera utilisée pour interagir avec ce projet. 0 indique qu’il n’y a pas d’interface d’interface utilisateur.|

 Les fichiers. vsz qui contrôlent de nouveaux types de projets contiennent fréquemment une entrée RELATIVE_PATH. Ce chemin d’accès est relatif au chemin d’accès spécifié sous l’entrée \ProductDir du type de projet dans la clé d’installation suivante :

 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\7.0Exp\Setup

 Par exemple, les modèles de projet Enterprise frameworks ajoutent les entrées de Registre suivantes :

 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\7.0Exp\Setup\EF\ProductDir = C:\Program Files\Microsoft Visual Studio\EnterpriseFrameworks\

 Cela signifie que si vous incluez une entrée PROJECT_TYPE = EF dans le fichier. vsz, l’environnement recherche les fichiers. vsz dans le répertoire ProductDir spécifié précédemment.

## <a name="see-also"></a>Voir aussi
- [Checklist : création de types de projets](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Éléments d’un modèle de projet](../../extensibility/internals/elements-of-a-project-model.md)
- [Création d’instances de projets à l’aide de fabriques de projets](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)
