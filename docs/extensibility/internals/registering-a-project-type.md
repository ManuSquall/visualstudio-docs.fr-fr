---
title: Enregistrement d’un type de projet Microsoft Docs
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
ms.openlocfilehash: 05ac1f393632934f193f5f4efaaf9e5459ffbb14
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705869"
---
# <a name="registering-a-project-type"></a>Inscription d’un type de projet
Lorsque vous créez un nouveau type de projet, vous devez créer des entrées de registre qui permettent [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] de reconnaître et de travailler avec votre type de projet. Vous créez généralement ces entrées de registre en utilisant un fichier de script de registre (.rgs).

 Dans l’exemple ci-dessous, les relevés du registre fournissent des trajectoires et des données par défaut, le cas échéant, suivis d’un tableau qui contient les entrées du script du registre pour chaque relevé. Les tableaux fournissent les entrées de script et des informations supplémentaires sur les instructions.

> [!NOTE]
> Les renseignements suivants sur le registre sont destinés à être un exemple du type et des objectifs des inscriptions dans les scripts du registre que vous écrira pour enregistrer votre type de projet. Vos entrées réelles et leurs utilisations peuvent varier en fonction des exigences spécifiques de votre type de projet. Vous devriez examiner les échantillons disponibles pour en trouver un qui ressemble beaucoup au type de projet que vous développez, puis examiner le script du registre pour cet échantillon.

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
|`@`|REG_SZ|`FigPrjFile`|Nom et description des fichiers de type projet qui ont l’extension .figp.|
|`Content Type`|REG_SZ|`Text/plain`|Type de contenu pour les fichiers de projet.|
|`NullFile`|REG_SZ|`Null`||
|`@`|REG_SZ|`%MODULE%,-206`|Icône par défaut utilisée pour le projet de ce type. L’énoncé de % MODULE % est rempli dans le registre à l’emplacement par défaut du type de projet DLL.|
|`@`|REG_SZ|`&Open in Visual Studio`|Application par défaut dans laquelle ce type de projet sera ouvert.|
|`@`|REG_SZ|`devenv.exe "%1"`|Commande par défaut qui sera exécutée lorsqu’un projet de ce type est ouvert.|

 Les exemples suivants proviennent de HKEY_LOCAL_MACHINE et sont situés dans le registre sous la clé [HKEY_LOCAL_MACHINE-SOFTWARE-Microsoft-VisualStudio-99.0Exp-Packages].

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
|`@` (valeur par défaut)|REG_SZ|`FigPrj Project VSPackage`|Nom localisable de ce VSPackage enregistré (type de projet).|
|`InprocServer32`|REG_SZ|`%MODULE%`|Chemin du type de projet DLL. L’IDE charge ce DLL et passe le `DllGetClassObject` CLSID VSPackage pour arriver <xref:Microsoft.VisualStudio.OLE.Interop.IClassFactory> à construire l’objet. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>|
|`CompanyName`|REG_SZ|`Microsoft`|Nom de l’entreprise qui a développé le type de projet.|
|`ProductName`|REG_SZ|`Figure Project Sample`|Nom du type de projet.|
|`ProductVersion`|REG_SZ|`9.0`|Numéro de version de la version type de projet.|
|`MinEdition`|REG_SZ|`professional`|Edition de l’enregistrement du VSPackage.|
|`ID`|REG_DWORD|`%IDS_PACKAGE_LOAD_KEY%`|La clé de charge du paquet pour le projet VSPackage. La clé est validée lorsqu’un projet est chargé après le début de l’environnement.|
|`DllName`|REG_SZ|`%RESOURCE_DLL%`|Nom de fichier du satellite DLL qui contient des ressources localisées pour le type de projet.|
|`Path`|REG_SZ|`%RESOURCE_PATH%`|Chemin du satellite DLL.|
|`FigProjectsEvents`|REG_SZ|Voir l’énoncé de valeur.|Détermine la chaîne de texte retournée pour cet événement d’automatisation.|
|`FigProjectItemsEvents`|REG_SZ|Voir l’énoncé de valeur.|Détermine la chaîne de texte retournée pour cet événement d’automatisation.|

 Tous les exemples suivants sont situés dans le registre sous la clé [HKEY_LOCAL_MACHINE-SOFTWARE-Microsoft-VisualStudio-9.0Exp-Projets].

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
|`DisplayName`|REG_SZ|`#%IDS_PROJECT_TYPE%`|Id de ressources du nom à récupérer à partir du satellite DLL enregistré sous paquets.|
|`Package`|REG_SZ|`%CLSID_Package%`|Id de classe du VSPackage enregistré sous les paquets.|
|`ProjectTemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|Voie par défaut des fichiers Project Template. Ce sont les fichiers affichés par le modèle Du nouveau projet.|
|`ItemTemplatesDir`|REG_SZ|`%TEMPLATE_PATH% \FigPrjProjectItems`|Voie par défaut des fichiers Project Item Template. Ce sont les fichiers affichés par le modèle Add New Item.|
|`DisplayProjectFileExtensions`|REG_SZ|`#%IDS_DISPLAY_PROJ_FILE_EXT%`|Permet à l’IDE d’implémenter la boîte de dialogue **Open.**|
|`PossibleProjectExtensions`|REG_SZ|`figp`|Utilisé par l’IDE pour déterminer si le projet en cours d’ouverture est géré par ce type de projet (usine de projet). Le format de plus d’une entrée est une liste délimitée au point-virgule. Par exemple "vdproj;vdp".|
|`DefaultProjectExtension`|REG_SZ|`.figp`|Utilisé par l’IDE comme extension de nom de fichier par défaut pour l’opération Save As.|
|`Filter Settings`|REG_DWORD|Divers, voir les déclarations et les commentaires suivant le tableau.|Ces paramètres sont utilisés pour définir les différents filtres pour afficher des fichiers dans les boîtes de dialogue de l’interface utilisateur.|
|`@`|REG_SZ|`#%IDS_ADDITEM_TEMPLATES_ENTRY%`|ID de ressource pour les modèles d’objets ajoutés.|
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjectItems`|Chemin des éléments du projet affichés dans la boîte de dialogue pour le modèle **Ajouter un nouvel élément.**|
|`SortPriority`|REG_DWORD|`100 (vcprx64)`|Détermine l’ordre de tri dans le nœud d’arbre des fichiers affichés dans la boîte de dialogue **Add New Item.**|

 Le tableau suivant affiche les options Filtres disponibles dans le segment de code précédent.

|Option filtre|Description|
|-------------------|-----------------|
|`CommonFindFilesFilter`|Indique que le filtre est l’un des filtres courants dans la boîte de dialogue **Trouver dans les fichiers.** Les filtres communs sont répertoriés dans la liste de filtre avant que les filtres ne soient marqués comme communs.|
|`CommonOpenFilesFilter`|Indique que le filtre est l’un des filtres courants dans la boîte de dialogue **Open File.** Les filtres communs sont répertoriés dans la liste de filtre avant que les filtres ne soient marqués comme communs.|
|`FindInFilesFilter`|Indique que le filtre sera l’un des filtres dans la boîte de dialogue **Trouver dans les fichiers** et sera répertorié après les filtres courants.|
|`NotOpenFileFilter`|Indique que le filtre ne sera pas utilisé dans la boîte de dialogue **Open File.**|
|`NotAddExistingItemFilter`|Indique que le filtre ne sera pas utilisé dans la boîte de dialogue **Add Existing Item.**|

 Par défaut, si un filtre n’a pas un ou plusieurs de ces drapeaux ensemble, le filtre est utilisé dans la boîte de dialogue **Add Existing Item** et la boîte de dialogue Open **File** après que les filtres communs sont énumérés. Le filtre n’est pas utilisé dans la boîte de dialogue **Find in Files.**

 Tous les exemples suivants sont situés dans le registre sous la clé [HKEY_LOCAL_MACHINE-SOFTWARE-Microsoft-VisualStudio-9.0Exp-Projets].

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
|`@`|REG_SZ|`#%IDS_NEWPROJ_ TEMPLATES_ENTRY%`|ID de ressources pour les nouveaux modèles de projet.|
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|Chemin par défaut pour les projets du type de projet enregistré.|
|`SortPriority`|REG_DWORD|`41 (x29)`|Définit l’ordre de tri des projets affichés dans la boîte de dialogue assistant De Nouveaux Projets.|
|`NewProjectDialogOnly`|REG_DWORD|`0`|0 indique que les projets de ce type ne sont affichés que dans la boîte de dialogue du nouveau projet.|

 Tous les exemples suivants sont situés dans le registre sous la clé [HKEY_LOCAL_MACHINE-SOFTWARE-Microsoft-VisualStudio-9.0Exp-Projets].

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
|`@`|REG_SZ|None|Valeur par défaut qui indique que les entrées suivantes sont pour les entrées de projets De fichiers divers.|
|`@`|REG_SZ|`#%IDS_ADDITEM_TEMPLATES_ENTRY%`|Valeur d’identification des ressources pour les fichiers de modèle Add New Items.|
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjectItems`|Chemin par défaut des éléments qui seront affichés dans la boîte de dialogue **Add New Item.**|
|`SortPriority`|REG_DWORD|`100 (vcprx64)`|Établit l’ordre de tri pour l’affichage dans le nœud d’arbre de la boîte de dialogue **Add New Item.**|

 L’exemple suivant est situé dans le registre sous la clé [HKEY_LOCAL_MACHINE-SOFTWARE-Microsoft-VisualStudio-9.0Exp-Menus].

## <a name="example"></a>Exemple

```
"{ACEF4EB2-57CF-11D2-96F4-000000000000}"=",1000,1"
```

 L’entrée du menu indique l’IDE à la ressource utilisée pour récupérer les informations du menu. Lorsque ces données ont été fusionnées dans la base de données du menu, la même clé sera ajoutée dans la section MenusMerged du registre. Le VSPackage ne doit pas modifier directement quoi que ce soit sous la section MenusMerged. Dans le domaine des données dans le tableau suivant, il y a trois champs séparés par virgule. Le premier champ identifie un chemin complet d’un fichier de ressources de menu :

- Si le premier champ est omis, la ressource de menu est chargée à partir du satellite DLL identifié par le GUID VSPackage.

  Le deuxième champ identifie une pièce d’identité de ressource de menu du type CTMENU :

- Si l’ID de ressource est spécifié et que le chemin de fichier est fourni par le premier paramètre, une ressource de menu est chargée à partir de la trajectoire complète du fichier.

- Si l’ID de ressource est fourni, mais que le chemin de fichier ne l’est pas, la ressource de menu est chargée à partir du satellite DLL.

- Si la trajectoire complète du dossier est fournie et que l’ID de ressource est omis, le fichier à charger devrait être un fichier CTO.

  Le dernier champ identifie le numéro de version de la ressource CTMENU. Vous pouvez fusionner le menu à nouveau en changeant le numéro de version.

|Nom|Type|Données|Description|
|----------|----------|----------|-----------------|
|% CLSID_Package %|REG_SZ|`,1000,1`|La ressource pour récupérer les informations du menu.|

 Tous les exemples suivants sont situés dans le registre sous la clé [HKEY_LOCAL_MACHINE-SOFTWARE-Microsoft-VisualStudio-9.0Exp-NewProjectTemplates].

```
\TemplateDirs\{ACEF4EB2-57CF-11D2-96F4-000000000000}\1                (CLSID for Figures Project projects)
   @="#7"
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\FigPrjProjects"
   "SortPriority"=dword:00000029
   "NewProjectDialogOnly"=dword:00000000
```

|Nom|Type|Données|Description|
|----------|----------|----------|-----------------|
|`@`|REG_SZ|`#%IDS_NEWPROJ_TEMPLATES_ENTRY%`|Valeur d’identification des ressources pour les modèles de projets nouveaux de figures.|
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|Chemin par défaut du répertoire Des nouveaux projets. Les articles de ce répertoire seront affichés dans la boîte de dialogue **des sorciers du nouveau projet.**|
|`SortPriority`|REG_DWORD|`41 (x29)`|Établit l’ordre dans lequel les projets seront affichés dans le nœud d’arbre de la boîte de dialogue **du nouveau projet.**|
|`NewProjectDialogOnly`|REG_DWORD|`0`|0 indique que les projets de ce type ne sont affichés que dans la boîte de dialogue **du nouveau projet.**|

 L’exemple suivant est situé dans le registre sous la clé [HKEY_LOCAL_MACHINE-SOFTWARE-Microsoft-VisualStudio-9.0Exp-InstalledProducts].

```
\FiguresProductSample
   "Package"="{ACEF4EB2-57CF-11D2-96F4-000000000000}"
   "UseInterface"=dword:00000001
```

|Nom|Type|Données|Description|
|----------|----------|----------|-----------------|
|`Package`|REG_SZ|`%CLSID_Package%`|Id de classe du VSPackage enregistré.|
|`UseInterface`|REG_DWORD|`1`|1 indique que l’interface utilisateur sera utilisée pour interagir avec ce projet. 0 indique qu’il n’y a pas d’interface d’interface d’interface utilisateur.|

 Les fichiers.vsz qui contrôlent de nouveaux types de projets contiennent fréquemment une entrée RELATIVE_PATH. Ce chemin est relatif au chemin spécifié sous l’entrée de 'ProductDir du type de projet dans la clé de configuration suivante :

 HKEY_LOCAL_MACHINE-SOFTWARE-Microsoft-VisualStudio 7.0Exp-Setup

 Par exemple, les modèles de projets Cadres d’entreprise ajoutent les entrées de registre suivantes :

 HKEY_LOCAL_MACHINE-SOFTWARE-Microsoft-VisualStudio-7.0Exp-Setup-EF-ProductDir ' C: 'Program Files’Microsoft Visual Studio’EnterpriseFrameworks

 Cela signifie que si vous incluez une entrée PROJECT_TYPE-EF dans le fichier .vsz, l’environnement trouve vos fichiers .vsz dans l’annuaire ProductDir spécifié précédemment.

## <a name="see-also"></a>Voir aussi
- [Liste de vérification : création de nouveaux types de projets](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Éléments d’un modèle de projet](../../extensibility/internals/elements-of-a-project-model.md)
- [Création d’instances de projets à l’aide de fabriques de projets](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)
