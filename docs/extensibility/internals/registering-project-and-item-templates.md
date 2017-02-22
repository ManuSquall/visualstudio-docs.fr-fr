---
title: "L’inscription de projet et mod&#232;les d’&#233;l&#233;ment | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "projets (Visual Studio SDK), ajouter des éléments"
  - "Registre, boîte de dialogue Ajouter un nouvel élément"
  - "Boîte de dialogue Ajouter un nouvel élément"
  - "Ajouter la boîte de dialogue Nouveau projet"
  - "Registre, boîte de dialogue Ajouter un nouveau projet"
ms.assetid: 6b909f93-d7f5-4aec-81c6-ee9ff0f31638
caps.latest.revision: 27
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 27
---
# L’inscription de projet et mod&#232;les d’&#233;l&#233;ment
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Types de projets doivent inscrire les répertoires où se trouvent leurs modèles de projet et d’élément de projet.[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] utilise les informations d’inscription associées aux types de votre projet afin de déterminer les éléments à afficher dans le **Ajouter un nouveau projet** et **Ajouter un nouvel élément** boîtes de dialogue.  
  
 Pour plus d’informations sur les modèles, consultez la page [Ajout de projet et modèles d'élément de projet](../../extensibility/internals/adding-project-and-project-item-templates.md).  
  
## Entrées de Registre pour les projets  
 Les exemples suivants montrent les entrées de Registre sous HKEY\_LOCAL\_MACHINE\\Software\\Microsoft\\VisualStudio\\ \<*Version*\>. Les tableaux qui accompagne cet article expliquent les éléments utilisés dans les exemples.  
  
```  
[Projects\{ProjectGUID}]  
@="MyProjectType"  
"DisplayName"="#2"  
"Package"="{VSPackageGUID}"  
"ProjectTemplatesDir"="C:\\MyProduct\\MyProjectTemplates"  
```  
  
|Nom|Type|Description|  
|---------|----------|-----------------|  
|@|REG\_SZ|Nom par défaut des projets de ce type.|  
|DisplayName|REG\_SZ|ID de ressource du nom doivent être extraites de la DLL satellite enregistrée sous Packages.|  
|Package|REG\_SZ|ID de classe du package est enregistré sous Packages.|  
|ProjectTemplatesDir|REG\_SZ|Chemin d’accès par défaut des fichiers de modèle de projet. Les fichiers de modèle de projet sont affichés par le **Nouveau projet** modèle.|  
  
### Enregistrement des modèles d’élément  
 Vous devez enregistrer le répertoire dans lequel vous stockez des modèles d’élément.  
  
```  
[Projects\{ProjectGUID}\AddItemTemplates\TemplateDirs\{VSPackageGUID}\1]  
@="#7"  
"TemplatesDir"="C:\\MyProduct\\MyProjectItemTemplates "  
"TemplatesLocalizedSubDir"="#10"  
"SortPriority"=dword:00000064  
```  
  
|Nom|Type|Description|  
|---------|----------|-----------------|  
|@|REG\_SZ|ID de ressource pour ajouter un élément modèles.|  
|TemplatesDir|REG\_SZ|Chemin d’accès des éléments de projet affiché dans la boîte de dialogue pour le **Ajouter un nouvel élément** Assistant.|  
|TemplatesLocalizedSubDir|REG\_SZ|ID de ressource de chaîne qui désigne le sous\-répertoire de TemplatesDir qui conserve des modèles localisés. Étant donné que [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] charge la ressource de chaîne à partir de DLL satellites si vous en avez, chaque DLL satellite peut contenir un nom de sous\-répertoire localisés différents.|  
|SortPriority|REG\_DWORD|Définissez SortPriority afin de déterminer l’ordre dans lequel les modèles sont affichés dans le **Ajouter un nouvel élément** boîte de dialogue. De plus grandes valeurs SortPriority apparaissent plus tôt dans la liste des modèles.|  
  
### Enregistrement de filtres de fichiers  
 Si vous le souhaitez, vous pouvez enregistrer des filtres qui [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] utilise lorsqu’il vous invite à entrer des noms de fichier. Par exemple, le [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] filtrer le le **Ouvrir le fichier** boîte de dialogue est :  
  
 **Fichiers Visual c\# \(\*.cs, \*.resx, \*.settings, \*.xsd, \*.wsdl\) ; \*.cs, \*.resx, \*.settings, \*.xsd, \*.wsdl\)**  
  
 Pour prendre en charge l’inscription de plusieurs filtres, chaque filtre est enregistré dans sa propre sous\-clé sous HKEY\_LOCAL\_MACHINE\\Software\\Microsoft\\VisualStudio\\ \<*Version*\> \\Projects\\ {\<*ProjectGUID*\>} \\Filters\\ \<*sous\-clé*\>. Le nom de la sous\-clé est arbitraire ; [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ignore les nom de la sous\-clé et utilise simplement ses valeurs.  
  
 Vous pouvez contrôler les contextes dans lesquels un filtre est utilisé par la définition d’indicateurs, illustrés dans le tableau suivant. Si un filtre n’a pas de jeu de tous les indicateurs, il sera répertorié après les filtres courants dans le **Ajouter un élément existant** boîte de dialogue et les **Ouvrir le fichier** boîte de dialogue, mais elle ne sera pas être utilisée dans le **Rechercher dans les fichiers** boîte de dialogue.  
  
```  
[Projects\{ProjectGUID}\Filters\MyLanguageFilter]  
@="#3"  
"CommonOpenFilesFilter"=dword:00000000  
"CommonFindFilesFilter"=dword:00000000  
"FindInFilesFilter"=dword:00000000  
"NotOpenFileFilter"=dword:00000000  
"NotAddExistingItemFilter"=dword:00000000  
"SortPriority"=dword:00000064  
```  
  
|Nom|Type|Description|  
|---------|----------|-----------------|  
|CommonFindFilesFilter|REG\_DWORD|Rend le filtre de l’un des filtres courants dans le **Rechercher dans les fichiers** boîte de dialogue. Filtres courants sont répertoriés dans la liste de filtres avant les filtres ne pas marqué comme commun.|  
|CommonOpenFilesFilter|REG\_DWORD|Rend le filtre de l’un des filtres courants dans le **Ouvrir le fichier** boîte de dialogue. Filtres courants sont répertoriés dans la liste de filtres avant les filtres ne pas marqué comme commun.|  
|FindInFilesFilter|REG\_DWORD|Répertorie le filtre après les filtres courants dans le **Rechercher dans les fichiers** boîte de dialogue.|  
|NotOpenFileFilter|REG\_DWORD|Indique que le filtre n’est pas utilisé dans le **Ouvrir le fichier** boîte de dialogue.|  
|NotAddExistingItemFilter|REG\_DWORD|Indique que le filtre n’est pas utilisé dans le **Ajouter un élément existant** boîte de dialogue.|  
|SortPriority|REG\_DWORD|Définissez SortPriority afin de déterminer l’ordre dans lequel les filtres s’affichent. De plus grandes valeurs SortPriority apparaissent plus tôt dans la liste de filtres.|  
  
## Structure de répertoires  
 Les VSPackages peut placer les dossiers et fichiers de modèle n’importe où sur un disque local ou distant, tant que l’emplacement est enregistré via l’environnement de développement intégré \(IDE\). Toutefois, pour faciliter l’organisation, nous recommandons la structure des répertoires sous le chemin d’installation de votre produit.  
  
 \\Templates  
  
 \\Projects \(contient les modèles de projet\)  
  
 \\Applications  
  
 \\Components  
  
 \\ ...  
  
 \\ProjectItems \(contient les éléments de projet\)  
  
 \\CLASSE  
  
 \\Form  
  
 \\Web Page  
  
 \\HelperFiles \(contient les fichiers utilisés dans les éléments de plusieurs fichiers projet\)  
  
 \\WizardFiles  
  
## Voir aussi  
 [Ajout de projet et modèles d'élément de projet](../../extensibility/internals/adding-project-and-project-item-templates.md)   
 [Assistants](../../extensibility/internals/wizards.md)   
 [Localisation d'applications](../../ide/localizing-applications.md)   
 [CATID des objets qui sont généralement utilisés pour étendre des projets](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)