---
title: "L’inscription des modèles de projet et élément | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio SDK], adding items
- registry, Add New Item dialog box
- Add New Item dialog box
- Add New Project dialog box
- registry, Add New Project dialog box
ms.assetid: 6b909f93-d7f5-4aec-81c6-ee9ff0f31638
caps.latest.revision: "27"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5c1cb9e31384822dddcdd3668bfb3a54bc2782d6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="registering-project-and-item-templates"></a>L’inscription des modèles de projet et élément
Types de projets doivent inscrire les répertoires où se trouvent leurs modèles de projet et d’élément de projet. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]utilise les informations d’inscription associées à vos types de projet pour déterminer les éléments à afficher dans le **ajouter un nouveau projet** et **ajouter un nouvel élément** boîtes de dialogue.  
  
 Pour plus d’informations sur les modèles, consultez [Ajout d’un projet et modèles d’élément de projet](../../extensibility/internals/adding-project-and-project-item-templates.md).  
  
## <a name="registry-entries-for-projects"></a>Entrées de Registre pour les projets  
 Les exemples suivants montrent les entrées de Registre sous HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\\<*Version*>. Les tableaux qui l’accompagne expliquent les éléments utilisés dans les exemples.  
  
```  
[Projects\{ProjectGUID}]  
@="MyProjectType"  
"DisplayName"="#2"  
"Package"="{VSPackageGUID}"  
"ProjectTemplatesDir"="C:\\MyProduct\\MyProjectTemplates"  
```  
  
|Nom|Type|Description|  
|----------|----------|-----------------|  
|@|REG_SZ|Nom par défaut des projets de ce type.|  
|DisplayName|REG_SZ|ID de ressource du nom doit être récupéré à partir de la DLL satellite inscrit sous Packages.|  
|Package|REG_SZ|ID de classe du package est enregistré sous Packages.|  
|ProjectTemplatesDir|REG_SZ|Chemin d’accès de la valeur par défaut des fichiers de modèle de projet. Les fichiers de modèle de projet sont affichés par le **nouveau projet** modèle.|  
  
### <a name="registering-item-templates"></a>L’inscription des modèles d’élément  
 Vous devez enregistrer le répertoire où vous stockez des modèles d’élément.  
  
```  
[Projects\{ProjectGUID}\AddItemTemplates\TemplateDirs\{VSPackageGUID}\1]  
@="#7"  
"TemplatesDir"="C:\\MyProduct\\MyProjectItemTemplates "  
"TemplatesLocalizedSubDir"="#10"  
"SortPriority"=dword:00000064  
```  
  
|Nom|Type|Description|  
|----------|----------|-----------------|  
|@|REG_SZ|ID de ressource pour les modèles d’ajouter un élément.|  
|TemplatesDir|REG_SZ|Chemin d’accès des éléments de projet affichés dans la boîte de dialogue pour le **ajouter un nouvel élément** Assistant.|  
|TemplatesLocalizedSubDir|REG_SZ|ID de ressource de chaîne qui désigne le sous-répertoire de TemplatesDir qui conserve les modèles localisés. Étant donné que [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] charge la ressource de chaîne à partir de DLL satellites si vous les avez, chaque DLL satellite peut contenir un nom de sous-répertoire localisés différents.|  
|SortPriority|REG_DWORD|Définissez SortPriority pour indiquer l’ordre dans lequel les modèles sont affichés dans le **ajouter un nouvel élément** boîte de dialogue. De plus grandes valeurs SortPriority apparaissent plus tôt dans la liste des modèles.|  
  
### <a name="registering-file-filters"></a>L’inscription des filtres de fichier  
 Si vous le souhaitez, vous pouvez inscrire des filtres qui [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] utilise lorsqu’il vous invite à entrer des noms de fichier. Par exemple, le [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] filtrer le le **ouvrir un fichier** boîte de dialogue est :  
  
 **Fichiers Visual c# (\*.cs,\*.resx,\*.settings,\*.xsd,\*.wsdl) ;\*. cs,\*.resx,\*.settings,\*.xsd,\*.wsdl)**  
  
 Pour prendre en charge l’inscription de plusieurs filtres, chaque filtre est enregistré dans son propre sous-clé sous HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\\<*Version*> \Projects\\{} \< *ProjectGUID*>} \Filters\\<*sous-clé*>. Le nom de la sous-clé est arbitraire ; [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ignore les nom de la sous-clé et utilise uniquement ses valeurs.  
  
 Vous pouvez contrôler les contextes dans lesquels un filtre est utilisé en définissant des indicateurs, illustrés dans le tableau suivant. Si un filtre n’a pas de définir des indicateurs, il apparaît après les filtres courants dans le **ajouter un élément existant** boîte de dialogue et les **ouvrir le fichier** boîte de dialogue, mais il ne sera pas utilisé dans le **rechercher dans les fichiers**  boîte de dialogue.  
  
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
|----------|----------|-----------------|  
|CommonFindFilesFilter|REG_DWORD|Rend le filtre à l’un des filtres courants dans les **rechercher dans les fichiers** boîte de dialogue. Filtres courants sont répertoriés dans la liste de filtres avant les filtres ne pas marqué comme commun.|  
|CommonOpenFilesFilter|REG_DWORD|Rend le filtre à l’un des filtres courants dans les **ouvrir le fichier** boîte de dialogue. Filtres courants sont répertoriés dans la liste de filtres avant les filtres ne pas marqué comme commun.|  
|FindInFilesFilter|REG_DWORD|Répertorie le filtre après les filtres courants dans les **rechercher dans les fichiers** boîte de dialogue.|  
|NotOpenFileFilter|REG_DWORD|Indique que le filtre n’est pas utilisé dans le **ouvrir le fichier** boîte de dialogue.|  
|NotAddExistingItemFilter|REG_DWORD|Indique que le filtre n’est pas utilisé dans le **ajouter un élément existant** boîte de dialogue.|  
|SortPriority|REG_DWORD|Définissez SortPriority pour indiquer l’ordre dans lequel les filtres sont affichés. De plus grandes valeurs SortPriority apparaissent plus tôt dans la liste de filtres.|  
  
## <a name="directory-structure"></a>Structure de répertoires  
 VSPackages peut placer les dossiers et fichiers de modèle de n’importe où sur un disque local ou distant, tant que l’emplacement inscrit via l’environnement de développement intégré (IDE). Toutefois, pour faciliter l’organisation, nous recommandons la structure des répertoires sous le chemin d’installation de votre produit.  
  
 \Templates  
  
 \Projects (contient les modèles de projet)  
  
 \Applications  
  
 \Components  
  
 \ ...  
  
 \ProjectItems (contient les éléments de projet)  
  
 \CLASSE  
  
 \Form  
  
 \Web Page  
  
 \HelperFiles (contient les fichiers utilisés dans les éléments de plusieurs fichiers projet)  
  
 \WizardFiles  
  
## <a name="see-also"></a>Voir aussi  
 [Ajout de projet et modèles d’élément de projet](../../extensibility/internals/adding-project-and-project-item-templates.md)   
 [Assistants](../../extensibility/internals/wizards.md)   
 [Localisation d’applications](../../ide/localizing-applications.md)   
 [CATID des objets qui sont généralement utilisés pour étendre des projets](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)