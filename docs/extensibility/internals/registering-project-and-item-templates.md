---
title: Enregistrement des modèles de projets et d’objets ( Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], adding items
- registry, Add New Item dialog box
- Add New Item dialog box
- Add New Project dialog box
- registry, Add New Project dialog box
ms.assetid: 6b909f93-d7f5-4aec-81c6-ee9ff0f31638
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b64504c39b1fc3c4a82530b265cfd0e96832b4f2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705824"
---
# <a name="registering-project-and-item-templates"></a>Inscription de modèles de projet et d’élément
Les types de projets doivent enregistrer les répertoires où se trouvent leurs modèles de projets et d’éléments de projet. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]utilise les informations d’enregistrement associées à vos types de projets pour déterminer ce qu’il faut afficher dans les boîtes de dialogue **Add New Project** et Ajouter de nouveaux **éléments.**

 Pour plus d’informations sur les modèles, voir [Ajout de modèles d’éléments de projet et de projet](../../extensibility/internals/adding-project-and-project-item-templates.md).

## <a name="registry-entries-for-projects"></a>Inscriptions au registre des projets
 Les exemples suivants montrent les entrées de registre sous HKEY_LOCAL_MACHINE-Software-Microsoft-VisualStudio\\<*Version*>. Les tableaux d’accompagnement expliquent les éléments utilisés dans les exemples.

```
[Projects\{ProjectGUID}]
@="MyProjectType"
"DisplayName"="#2"
"Package"="{VSPackageGUID}"
"ProjectTemplatesDir"="C:\\MyProduct\\MyProjectTemplates"
```

|Nom|Type|Description|
|----------|----------|-----------------|
|@|REG_SZ|Nom par défaut de projets de ce type.|
|DisplayName|REG_SZ|Id de ressources du nom à récupérer à partir du satellite DLL enregistré sous paquets.|
|Package|REG_SZ|Id de classe du colis enregistré sous les paquets.|
|ProjetTemplatesDir|REG_SZ|Voie par défaut des fichiers Project Template. Les fichiers Project Template sont affichés par le **modèle du nouveau projet.**|

### <a name="registering-item-templates"></a>Enregistrement des modèles d’objets
 Vous devez enregistrer l’annuaire où vous stockez des modèles d’articles.

```
[Projects\{ProjectGUID}\AddItemTemplates\TemplateDirs\{VSPackageGUID}\1]
@="#7"
"TemplatesDir"="C:\\MyProduct\\MyProjectItemTemplates "
"TemplatesLocalizedSubDir"="#10"
"SortPriority"=dword:00000064
```

| Nom | Type | Description |
|--------------------------|-----------| - |
| @ | REG_SZ | ID de ressource pour les modèles d’objets ajoutés. |
| TemplatesDir | REG_SZ | Chemin des éléments du projet affichés dans la boîte de dialogue pour le magicien **Add New Item.** |
| TemplatesLocalizedSubDir | REG_SZ | Id de ressources d’une chaîne qui nomme la sous-direction de TemplatesDir qui contient des modèles localisés. Parce [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] que charge la ressource de chaîne à partir de DLL satellites si vous les avez, chaque satellite DLL peut contenir un nom sous-directionalisé localisé différent. |
| SortPriorité | REG_DWORD | Définissez SortPriority pour régir l’ordre dans lequel les modèles sont affichés dans la boîte de dialogue **Add New Item.** Les valeurs de la plus grande valeur de la priorité de sort apparaissent plus tôt dans la liste de modèle. |

### <a name="registering-file-filters"></a>Enregistrement des filtres de fichiers
 En option, vous pouvez [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] enregistrer les filtres qui utilisent lorsqu’il invite à obtenir des noms de fichiers. Par exemple, [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] le filtre de la boîte de dialogue **Open File** est :

 **Fichiers visuels C\*(.cs,\*\*.resx,\*.settings,\*.xsd, .wsdl); \*.cs,\*.resx,\*.settings,\*.xsd,\*.wsdl)**

 Pour prendre en charge l’enregistrement de plusieurs filtres, chaque filtre est enregistré dans\\<sa propre sous-clé\<sous HKEY_LOCAL_MACHINE-Software-Microsoft-VisualStudio*Version*>-Projets\\-*ProjectGUID*>- Filters\\<*Subkey*>. Le nom subkey est arbitraire; [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ignore le nom du sous-clé et n’utilise que ses valeurs.

 Vous pouvez contrôler les contextes dans lesquels un filtre est utilisé en définissant des drapeaux, affichés dans le tableau suivant. Si un filtre n’a pas d’ensemble de drapeaux, il sera répertorié après les filtres communs dans la boîte de dialogue **Add Existing Item** et la boîte de dialogue Open **File,** mais il ne sera pas utilisé dans la boîte de dialogue **Find in Files.**

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
|CommonFindFilesFilter|REG_DWORD|Fait du filtre l’un des filtres courants de la boîte de dialogue **Find in Files.** Les filtres courants sont répertoriés dans la liste des filtres avant que les filtres ne soient pas marqués comme communs.|
|CommonOpenFilesFilter|REG_DWORD|Fait du filtre l’un des filtres courants de la boîte de dialogue **Open File.** Les filtres courants sont répertoriés dans la liste des filtres avant que les filtres ne soient pas marqués comme communs.|
|TrouverInFilesFilter|REG_DWORD|Répertorie le filtre après les filtres courants dans la boîte de dialogue **Trouver dans les fichiers.**|
|NotOpenFileFilter|REG_DWORD|Indique que le filtre n’est pas utilisé dans la boîte de dialogue **Open File.**|
|NotAddExistingItemFilter|REG_DWORD|Indique que le filtre n’est pas utilisé dans la boîte de dialogue **Add Existing Item.**|
|SortPriorité|REG_DWORD|Définissez SortPriority pour régir l’ordre dans lequel les filtres sont affichés. Les valeurs de la plus grande valeur de la priorité de sort apparaissent plus tôt dans la liste de filtre.|

## <a name="directory-structure"></a>Structure de répertoires
 VSPackages peut mettre des fichiers et des dossiers de modèle n’importe où sur un disque local ou distant, tant que l’emplacement est enregistré par l’environnement de développement intégré (IDE). Cependant, pour faciliter l’organisation, nous recommandons la structure d’annuaire suivante sous le chemin d’installation de votre produit.

 Modèles

 Projets (contient les modèles de projet)

 Applications

 Composants

 \ ...

 ProjectItems (contient les éléments du projet)

 Classe

 Formulaire

 Page Web

 -HelperFiles (contient les fichiers utilisés dans les éléments de projet multi-fichiers)

 WizardFiles

## <a name="see-also"></a>Voir aussi

- [Ajout d’un projet et de modèles d’élément de projet](../../extensibility/internals/adding-project-and-project-item-templates.md)
- [Assistants](../../extensibility/internals/wizards.md)
- [Localisation d’applications](../../ide/globalizing-and-localizing-applications.md)
- [CATID des objets qui sont généralement utilisés pour étendre des projets](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)
