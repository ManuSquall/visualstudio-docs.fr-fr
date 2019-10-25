---
title: Inscription de modèles de projet et d’élément | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], adding items
- registry, Add New Item dialog box
- Add New Item dialog box
- Add New Project dialog box
- registry, Add New Project dialog box
ms.assetid: 6b909f93-d7f5-4aec-81c6-ee9ff0f31638
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2e35a476ab8fe8d8de3ce11dd117de4c84a3befa
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72724625"
---
# <a name="registering-project-and-item-templates"></a>Inscription de modèles de projet et d’élément
Les types de projets doivent inscrire les répertoires dans lesquels se trouvent les modèles de projet et d’élément de projet. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] utilise les informations d’inscription associées à vos types de projets pour déterminer les éléments à afficher dans les boîtes de dialogue **Ajouter un nouveau projet** et **Ajouter un nouvel élément** .

 Pour plus d’informations sur les modèles, consultez [Ajout de modèles de projet et d’élément de projet](../../extensibility/internals/adding-project-and-project-item-templates.md).

## <a name="registry-entries-for-projects"></a>Entrées de Registre pour les projets
 Les exemples suivants montrent des entrées de Registre sous HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio \\ <*Version*>. Les tableaux qui l’accompagnent expliquent les éléments utilisés dans les exemples.

```
[Projects\{ProjectGUID}]
@="MyProjectType"
"DisplayName"="#2"
"Package"="{VSPackageGUID}"
"ProjectTemplatesDir"="C:\\MyProduct\\MyProjectTemplates"
```

|Name|Tapez|Description|
|----------|----------|-----------------|
|@|REG_SZ|Nom par défaut des projets de ce type.|
|DisplayName|REG_SZ|ID de ressource du nom à récupérer à partir de la DLL satellite inscrite sous packages.|
|Package|REG_SZ|ID de classe du package enregistré sous packages.|
|ProjectTemplatesDir|REG_SZ|Chemin d’accès par défaut des fichiers de modèles de projet. Les fichiers de modèles de projet sont affichés par le nouveau modèle de **projet** .|

### <a name="registering-item-templates"></a>Inscription des modèles d’élément
 Vous devez inscrire le répertoire dans lequel vous stockez les modèles d’élément.

```
[Projects\{ProjectGUID}\AddItemTemplates\TemplateDirs\{VSPackageGUID}\1]
@="#7"
"TemplatesDir"="C:\\MyProduct\\MyProjectItemTemplates "
"TemplatesLocalizedSubDir"="#10"
"SortPriority"=dword:00000064
```

| Name | Tapez | Description |
|--------------------------|-----------| - |
| @ | REG_SZ | ID de ressource pour ajouter des modèles d’élément. |
| TemplatesDir | REG_SZ | Chemin d’accès aux éléments de projet affichés dans la boîte de dialogue de l’Assistant **Ajout d’un nouvel élément** . |
| TemplatesLocalizedSubDir | REG_SZ | ID de ressource d’une chaîne qui nomme le sous-répertoire de TemplatesDir qui contient les modèles localisés. Étant donné que [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] charge la ressource de chaîne à partir de dll satellites si vous en avez, chaque DLL satellite peut contenir un nom de sous-répertoire localisé différent. |
| SortPriority | REG_DWORD | Définissez SortPriority pour régir l’ordre dans lequel les modèles sont affichés dans la boîte de dialogue **Ajouter un nouvel élément** . Les valeurs SortPriority plus grandes apparaissent plus haut dans la liste des modèles. |

### <a name="registering-file-filters"></a>Inscription des filtres de fichiers
 Si vous le souhaitez, vous pouvez inscrire des filtres que [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] utilise lorsqu’il demande des noms de fichiers. Par exemple, le filtre [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] de la boîte de dialogue **ouvrir un fichier** est le suivant :

 **Fichiers C# visuels (\*. cs, \*. resx, \*. Settings, \*. xsd, \*. WSDL); \*. cs, \*. resx, \*. Settings, 0. xsd, 1. WSDL)**

 Pour prendre en charge l’inscription de plusieurs filtres, chaque filtre est inscrit dans sa propre sous-clé sous HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio \\ <*Version*> \projets \\ {\<*ProjectGuid*>} \Filters \\ <*sous-clé*>. Le nom de la sous-clé est arbitraire ;  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ignore le nom de la sous-clé et utilise uniquement ses valeurs.

 Vous pouvez contrôler les contextes dans lesquels un filtre est utilisé en définissant des indicateurs, comme indiqué dans le tableau suivant. Si aucun indicateur n’est défini pour un filtre, celui-ci apparaîtra dans la liste des filtres communs de la boîte de dialogue **Ajouter un élément existant** et de la boîte de dialogue **ouvrir un fichier** , mais il ne sera pas utilisé dans la boîte de dialogue **Rechercher dans les fichiers** .

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

|Name|Tapez|Description|
|----------|----------|-----------------|
|CommonFindFilesFilter|REG_DWORD|Fait du filtre l’un des filtres courants dans la boîte de dialogue **Rechercher dans les fichiers** . Les filtres courants sont répertoriés dans la liste de filtres avant les filtres qui ne sont pas marqués comme communs.|
|CommonOpenFilesFilter|REG_DWORD|Fait du filtre l’un des filtres courants dans la boîte de dialogue **ouvrir un fichier** . Les filtres courants sont répertoriés dans la liste de filtres avant les filtres qui ne sont pas marqués comme communs.|
|FindInFilesFilter|REG_DWORD|Répertorie le filtre après les filtres courants de la boîte de dialogue **Rechercher dans les fichiers** .|
|NotOpenFileFilter|REG_DWORD|Indique que le filtre n’est pas utilisé dans la boîte de dialogue **ouvrir un fichier** .|
|NotAddExistingItemFilter|REG_DWORD|Indique que le filtre n’est pas utilisé dans la boîte de dialogue **Ajouter un élément existant** .|
|SortPriority|REG_DWORD|Définissez SortPriority pour régir l’ordre dans lequel les filtres sont affichés. Les valeurs SortPriority plus grandes apparaissent plus haut dans la liste de filtres.|

## <a name="directory-structure"></a>Structure de répertoires
 Les VSPackages peuvent placer des fichiers et des dossiers de modèle n’importe où sur un disque local ou distant, tant que l’emplacement est inscrit via l’environnement de développement intégré (IDE). Toutefois, pour faciliter l’organisation, nous vous recommandons d’utiliser la structure de répertoires suivante dans le chemin d’installation de votre produit.

 \Templates

 \Projets (contient les modèles de projet)

 \Journaux

 \Components

 \ ...

 \ProjectItems (contient les éléments de projet)

 \Class

 \Form

 Page \Web

 \HelperFiles (contient les fichiers utilisés dans les éléments de projet à plusieurs fichiers)

 \WizardFiles

## <a name="see-also"></a>Voir aussi

- [Ajout d’un projet et de modèles d’élément de projet](../../extensibility/internals/adding-project-and-project-item-templates.md)
- [Assistants](../../extensibility/internals/wizards.md)
- [Localisation d’applications](../../ide/globalizing-and-localizing-applications.md)
- [CATID des objets qui sont généralement utilisés pour étendre des projets](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)