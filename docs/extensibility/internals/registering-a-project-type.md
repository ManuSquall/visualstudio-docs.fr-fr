---
title: "L&#39;inscription d&#39;un Type de projet | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "projets (Visual Studio SDK), de nouvelles entrées de Registre du projet"
  - "Registre, les nouveaux types de projet"
  - "inscription, les nouveaux types de projet"
ms.assetid: dfc0e231-6b4e-447d-9d64-0e66dea3394a
caps.latest.revision: 21
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 21
---
# L&#39;inscription d&#39;un Type de projet
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Lorsque vous créez un type de projet, vous devez créer les entrées du Registre qui permet à [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pour reconnaître et utiliser votre type de projet.  Vous créez généralement ces entrées du Registre à l'aide d'un fichier de script de Registre \(.rgs\).  
  
 Dans l'exemple ci\-dessous, les instructions du Registre fournissent des chemins d'accès par défaut et des informations le cas échéant, suivi d'une table qui contient des entrées du script de Registre pour chaque instruction.  Les tables fournissent des entrées et des informations supplémentaires de script sur les instructions.  
  
> [!NOTE]
>  Les informations suivantes de Registre sont conçues pour être un exemple de type et les objectifs des entrées dans les scripts de Registre que vous écrirez pour stocker votre type de projet.  Les entrées réelle et leurs utilisations peuvent varier selon les exigences de votre type de projet.  Vous devez examiner les exemples disponibles pour rechercher un qui ressemble étroitement au type de projet que vous développez, puis pour examiner le script de Registre pour cet exemple.  
  
 les exemples suivants sont de HKEY\_CLASSES\_ROOT.  
  
## Exemple  
  
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
|---------|----------|-------------|-----------------|  
|`@`|REG\_SZ|`FigPrjFile`|Le nom et la description du type de projet les fichiers avec l'extension .figp.|  
|`Content Type`|REG\_SZ|`Text/plain`|type de contenu pour les fichiers projet.|  
|`NullFile`|REG\_SZ|`Null`||  
|`@`|REG\_SZ|`%MODULE%,-206`|icône par défaut utilisée pour le projet de ce type.  L'instruction de %MODULE% est effectuée dans le Registre à l'emplacement par défaut de la DLL du type de projet.|  
|`@`|REG\_SZ|`&Open in Visual Studio`|La cible par défaut l'application dans laquelle ce type de projet sera ouvert.|  
|`@`|REG\_SZ|`devenv.exe "%1"`|Commande par défaut qui sera exécutée lorsqu'un projet de ce type est ouvert.|  
  
 Les exemples suivants sont HKEY\_LOCAL\_MACHINE et se trouvent dans le Registre sous la clé \[HKEY\_LOCAL\_MACHINE \\SOFTWARE\\Microsoft\\VisualStudio\\99.0Exp\\Packages\].  
  
## Exemple  
  
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
|---------|----------|-------------|-----------------|  
|`@`\(valeur par défaut\)|REG\_SZ|`FigPrj Project VSPackage`|Nom localisé de ce VSPackage enregistré \(type de projet\).|  
|`InprocServer32`|REG\_SZ|`%MODULE%`|Chemin d'accès de la DLL du type de projet.  L'IDE charge cette DLL et passe le VSPackage le CLSID à `DllGetClassObject` pour obtenir <xref:Microsoft.VisualStudio.OLE.Interop.IClassFactory> de construire l'objet d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> .|  
|`CompanyName`|REG\_SZ|`Microsoft`|nom de la société qui a développé le type de projet.|  
|`ProductName`|REG\_SZ|`Figure Project Sample`|Nom du type de projet.|  
|`ProductVersion`|REG\_SZ|`9.0`|Numéro de version de la version du type de projet.|  
|`MinEdition`|REG\_SZ|`professional`|Édition du VSPackage enregistré.|  
|`ID`|REG\_DWORD|`%IDS_PACKAGE_LOAD_KEY%`|Le de commande fonctionnent de chargement de package pour le projet VSPackage.  La clé est validée lorsqu'un projet est chargé après que l'environnement a démarré.|  
|`DllName`|REG\_SZ|`%RESOURCE_DLL%`|Nom de fichier de la DLL satellite contenant les ressources localisées pour le type de projet.|  
|`Path`|REG\_SZ|`%RESOURCE_PATH%`|Chemin d'accès de la DLL satellite.|  
|`FigProjectsEvents`|REG\_SZ|Consultez l'instruction pour la valeur.|détermine la chaîne de texte retournée pour cet événement d'automation.|  
|`FigProjectItemsEvents`|REG\_SZ|Consultez l'instruction pour la valeur.|détermine la chaîne de texte retournée pour cet événement d'automation.|  
  
 Tous les exemples suivants se trouvent dans le Registre sous la clé \[HKEY\_LOCAL\_MACHINE \\SOFTWARE\\Microsoft\\VisualStudio\\9.0Exp\\Projects\].  
  
## Exemple  
  
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
|---------|----------|-------------|-----------------|  
|`@`|REG\_SZ|`FigPrj Project`|Nom par défaut des projets de ce type.|  
|`DisplayName`|REG\_SZ|`#%IDS_PROJECT_TYPE%`|L'ID de ressource du nom à récupérer de la DLL satellite est stocké sous des packages.|  
|`Package`|REG\_SZ|`%CLSID_Package%`|ID de classe du VSPackage stocké sous des packages.|  
|`ProjectTemplatesDir`|REG\_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|chemin d'accès par défaut des fichiers de modèle de projet.  Il s'agit des fichiers affichés par le nouveau modèle de projet.|  
|`ItemTemplatesDir`|REG\_SZ|`%TEMPLATE_PATH% \FigPrjProjectItems`|chemin d'accès par défaut des fichiers modèles d'élément de projet.  Il s'agit des fichiers affichés par le nouveau modèle d'élément à ajouter.|  
|`DisplayProjectFileExtensions`|REG\_SZ|`#%IDS_DISPLAY_PROJ_FILE_EXT%`|Permet à l'IDE pour implémenter la boîte de dialogue d' **Ouvrir** .|  
|`PossibleProjectExtensions`|REG\_SZ|`figp`|Utilisé par l'IDE pour déterminer si un projet étant ouvert est traité par ce type de projet \(fabrique de projet\).  Le format pour plusieurs entrée est une liste délimitée par des points\-virgules.  par exemple « vdproj ; vdp ».|  
|`DefaultProjectExtension`|REG\_SZ|`.figp`|Utilisé par l'IDE comme une extension de nom de fichier par défaut pour l'enregistrement en tant qu'opération.|  
|`Filter Settings`|REG\_DWORD|Différent, consultez les instructions et de commentaires le tableau suivant.|Ces paramètres sont utilisés pour définir les différents filtres pour afficher des fichiers dans les boîtes de dialogue de l'interface utilisateur.|  
|`@`|REG\_SZ|`#%IDS_ADDITEM_TEMPLATES_ENTRY%`|L'ID de ressource pour ajouter des modèles d'élément.|  
|`TemplatesDir`|REG\_SZ|`%TEMPLATE_PATH%\FigPrjProjectItems`|chemin d'accès des éléments de projet affichés dans la boîte de dialogue pour le modèle d' **Ajouter un nouvel élément** .|  
|`SortPriority`|REG\_DWORD|`100 (vcprx64)`|Détermine l'ordre de tri dans le nœud d'arborescence des fichiers affichés dans la boîte de dialogue d' **Ajouter un nouvel élément** .|  
  
 le tableau suivant montre les options de filtres disponibles dans le segment de code précédent.  
  
|option de filtre|Description|  
|----------------------|-----------------|  
|`CommonFindFilesFilter`|indique que le filtre est l'un des filtres communs dans la boîte de dialogue de **Rechercher dans les fichiers** .  Les filtres communs sont répertoriés dans la liste des filtres avant les filtres non marqués comme courantes.|  
|`CommonOpenFilesFilter`|indique que le filtre est l'un des filtres communs dans la boîte de dialogue d' **Ouvrir un fichier** .  Les filtres communs sont répertoriés dans la liste des filtres avant les filtres non marqués comme courantes.|  
|`FindInFilesFilter`|Indique que le filtre est l'un des filtres dans la boîte de dialogue de **Rechercher dans les fichiers** et sera répertorié après le mot commun filtre.|  
|`NotOpenFileFilter`|indique que le filtre ne sera pas utilisé dans la boîte de dialogue d' **Ouvrir un fichier** .|  
|`NotAddExistingItemFilter`|indique que le filtre ne sera pas utilisé dans la boîte de dialogue d' **Élément existant** d'ajouter.|  
  
 Par défaut, si un filtre n'a pas un ou plusieurs de ces indicateurs définies, le filtre est utilisé dans la boîte de dialogue d' **Ajouter un élément existant** et la boîte de dialogue d' **Ouvrir un fichier** une fois les filtres communs sont répertoriés.  le filtre n'est pas utilisé dans la boîte de dialogue de **Rechercher dans les fichiers** .  
  
 Tous les exemples suivants se trouvent dans le Registre sous la clé \[HKEY\_LOCAL\_MACHINE \\SOFTWARE\\Microsoft\\VisualStudio\\9.0Exp\\Projects\].  
  
## Exemple  
  
```  
{FE3BBBB6-72D5-11d2-9ACE-00C04F79A2A4} (The CLSID for Enterprise Projects)  
\{FE3BBBB6-72D5-11d2-9ACE-00C04F79A2A4}\AddItemTemplates\TemplateDirs\ {ACEF4EB2-57CF-11D2-96F4-000000000000}\1 (CLSID for projects of this type)  
   @="#7"  
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPrj\\FigPrjProjects"  
   "SortPriority"=dword:00000029  
   "NewProjectDialogOnly"=dword:00000000  
```  
  
|Nom|Type|Données|Description|  
|---------|----------|-------------|-----------------|  
|`@`|REG\_SZ|`#%IDS_NEWPROJ_ TEMPLATES_ENTRY%`|ID de ressource pour de nouveaux modèles de projet.|  
|`TemplatesDir`|REG\_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|Chemin d'accès par défaut pour les projets du type stocké de projet.|  
|`SortPriority`|REG\_DWORD|`41 (x29)`|Définit l'ordre de tri de projets affichent dans la boîte de dialogue Assistant de projets.|  
|`NewProjectDialogOnly`|REG\_DWORD|`0`|0 indique que les projets de ce type sont affichés uniquement dans la boîte de dialogue nouveau projet.|  
  
 Tous les exemples suivants se trouvent dans le Registre sous la clé \[HKEY\_LOCAL\_MACHINE \\SOFTWARE\\Microsoft\\VisualStudio\\9.0Exp\\Projects\].  
  
## Exemple  
  
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
|---------|----------|-------------|-----------------|  
|`@`|REG\_SZ|Aucun|Valeur par défaut qui indique que les entrées suivantes concernent les entrées de projets Fichiers divers.|  
|`@`|REG\_SZ|`#%IDS_ADDITEM_TEMPLATES_ENTRY%`|Valeur d'ID de ressource pour les nouveaux fichiers modèles d'éléments à ajouter.|  
|`TemplatesDir`|REG\_SZ|`%TEMPLATE_PATH%\FigPrjProjectItems`|Chemin d'accès par défaut des éléments qui sont affichés dans la boîte de dialogue d' **Ajouter un nouvel élément** .|  
|`SortPriority`|REG\_DWORD|`100 (vcprx64)`|Définit l'ordre de tri pour l'afficher dans le nœud d'arbre de la boîte de dialogue d' **Ajouter un nouvel élément** .|  
  
 L'exemple suivant se trouve dans le Registre sous la clé \[HKEY\_LOCAL\_MACHINE \\SOFTWARE\\Microsoft\\VisualStudio\\9.0Exp\\Menus\].  
  
## Exemple  
  
```  
"{ACEF4EB2-57CF-11D2-96F4-000000000000}"=",1000,1"  
```  
  
 Les points d'entrée de menu IDE à la ressource utilisée pour récupérer des informations de menu.  Lorsque ces données a été fusionné dans la base de données de menu, la même clé sera ajoutée dans la section de MenusMerged du Registre.  Le VSPackage ne doit aucune modification dans la section de MenusMerged directement.  Dans le champ de données dans le tableau suivant, il existe trois virgule\-séparer\-champs.  Le premier champ identifie un chemin complet d'un fichier de ressources menu :  
  
-   Si le premier champ est omis, la ressource menu est chargée de la DLL satellite identifié par le VSPackage GUID.  
  
 Le deuxième champ identifie un ID de ressource menu du type CTMENU :  
  
-   Si l'ID de ressource est spécifié, et le chemin d'accès de fichier est fourni par le premier paramètre, une ressource menu est débitée du chemin d'accès de fichier complet.  
  
-   Si l'ID de ressource est fourni, mais le chemin d'accès de fichier n'est pas le cas, la ressource menu est chargée de la DLL satellite.  
  
-   Si le chemin d'accès de fichier complet est fourni et l'ID de ressource est omis, il est recommandé que le fichier à charger est un fichier de CTO.  
  
 Le dernier champ identifie le numéro de version pour la ressource de CTMENU.  vous pouvez fusionner le menu de nouveau en modifiant le numéro de version.  
  
|Nom|Type|Données|Description|  
|---------|----------|-------------|-----------------|  
|%CLSID\_Package%|REG\_SZ|`,1000,1`|La ressource pour récupérer des informations de menu.|  
  
 Tous les exemples suivants se trouvent dans le Registre sous la clé \[HKEY\_LOCAL\_MACHINE \\SOFTWARE\\Microsoft\\VisualStudio\\9.0Exp\\NewProjectTemplates\].  
  
```  
\TemplateDirs\{ACEF4EB2-57CF-11D2-96F4-000000000000}\1                (CLSID for Figures Project projects)  
   @="#7"  
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\FigPrjProjects"  
   "SortPriority"=dword:00000029  
   "NewProjectDialogOnly"=dword:00000000  
```  
  
|Nom|Type|Données|Description|  
|---------|----------|-------------|-----------------|  
|`@`|REG\_SZ|`#%IDS_NEWPROJ_TEMPLATES_ENTRY%`|Valeur d'ID de ressource pour modèles de projet de nombres les nouveaux.|  
|`TemplatesDir`|REG\_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|chemin d'accès par défaut du nouveau répertoire de projets.  Les éléments de ce répertoire pourront affichés dans la boîte de dialogue de **L'Assistant nouveau projet** .|  
|`SortPriority`|REG\_DWORD|`41 (x29)`|Établit l'ordre dans lequel les projets sont affichés dans le nœud d'arborescence de la boîte de dialogue de **Nouveau projet** .|  
|`NewProjectDialogOnly`|REG\_DWORD|`0`|0 indique que les projets de ce type sont affichés uniquement dans la boîte de dialogue de **Nouveau projet** .|  
  
 L'exemple suivant se trouve dans le Registre sous la clé \[HKEY\_LOCAL\_MACHINE \\SOFTWARE\\Microsoft\\VisualStudio\\9.0Exp\\InstalledProducts\].  
  
```  
\FiguresProductSample  
   "Package"="{ACEF4EB2-57CF-11D2-96F4-000000000000}"  
   "UseInterface"=dword:00000001  
```  
  
|Nom|Type|Données|Description|  
|---------|----------|-------------|-----------------|  
|`Package`|REG\_SZ|`%CLSID_Package%`|ID de classe du VSPackage enregistré.|  
|`UseInterface`|REG\_DWORD|`1`|1 indique que l'interface utilisateur est utilisé pour interagir avec ce projet.  0 indique qu'il n'y a aucune interface utilisateur.|  
  
 Les fichiers de The.vsz qui contrôlent de nouveaux types de projets contiennent fréquemment une entrée de RELATIVE\_PATH.  ce chemin d'accès est à chemin d'accès relatif spécifié sous la clé de \\ProductDir entry of the project type in the following Setup :  
  
 HKEY\_LOCAL\_MACHINE \\SOFTWARE\\Microsoft\\VisualStudio\\7.0Exp\\Setup  
  
 Par exemple, les modèles de projet et d'Infrastructure d'entreprise d'ajouter des entrées du Registre suivantes :  
  
 HKEY\_LOCAL\_MACHINE \\ \\SOFTWARE\\Microsoft\\VisualStudio\\7.0Exp\\Setup\\EF\\ProductDir \= C:\\Program Files\\Microsoft Visual Studio\\EnterpriseFrameworks  
  
 Ces signifie que si vous incluez une entrée de PROJECT\_TYPE\=EF dans le fichier .vsz, l'environnement a détecté vos fichiers .vsz dans le répertoire de ProductDir spécifié précédemment.  
  
## Voir aussi  
 [Liste de vérification : Créer de nouveaux Types de projet](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Éléments d'un modèle de projet](../../extensibility/internals/elements-of-a-project-model.md)   
 [Création d'Instances de projet à l'aide de fabriques de projet](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)