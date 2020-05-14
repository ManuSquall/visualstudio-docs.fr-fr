---
title: Ajout d’articles aux boîtes de dialogue d’articles neufs Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Add New Item dialog box, adding items
ms.assetid: 2f70863b-425b-4e65-86b4-d6a898e29dc7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: af7f9e5c792785a23ad1674a50abeb4eb6d3cba9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710214"
---
# <a name="add-items-to-the-add-new-item-dialog-box"></a>Ajouter des éléments à la boîte de dialogue Add New Item
Le processus d’ajout d’éléments à la boîte de dialogue **Add New Item** commence par les clés du registre. Comme le montrent les entrées de registre suivantes, la section **AddItemTemplates** contient le chemin et le nom de l’annuaire dans lequel les éléments mis à disposition dans la boîte de dialogue **Add New Item** sont mis.

> [!NOTE]
> Le tableau immédiatement après le segment de code contient des informations supplémentaires sur la saisie du registre.

 Cette section est située sous **HKEY_LOCAL_MACHINE-SOFTWARE-Microsoft-VisualStudio-14.0Exp-Projets**.

 Le premier GUID est le CLSID pour les projets de ce type; le deuxième GUID indique le type de projet enregistré pour les modèles Add Items :

 **\\C061DB26-5833-11D2-96F5-0000000000000 \\AddItemTemplates\\TemplatesDir\\-ACEF4EB2-57CF-11D2-96F4-00000000000\\**

 **@**#6

 **TemplatesDir** = \\&lt;&gt;\\Visual Studio SDK trajectoire\\&lt;d’installation&gt;\\&lt;VSIntegration SomeFolder&gt;\\&lt;SomePackage SomeProject&gt;\\&lt;SomeProject SomeProjectItems&gt;

 **SortPriority** - dword:00000064

| Nom | Type | Données (à partir du fichier *.rgs)* | Description |
|------------------|-----------| - | - |
| (Par défaut) | REG_SZ | % IDS_ADDITEM_TEMPLATES_ENTRY % | ID de ressource pour les modèles **d’objets ajoutés.** |
| Val TemplatesDir | REG_SZ | % TEMPLATE_PATH%\\&lt;SomeProjectItems&gt; | Chemin des éléments du projet affichés dans le dialogue pour **l’assistant Add New Item.** |
| Val SortPriorité | REG_DWORD | 100[!INCLUDE[vcprx64](../../extensibility/internals/includes/vcprx64_md.md)]( ) | Détermine l’ordre de tri dans le nœud d’arbre des fichiers affichés dans la boîte de dialogue **Add New Item.** |

> [!NOTE]
> Les GUIDS pour les types de projets Visual CMD et Visual Basic sont les suivants :
> - [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]: 'FAE04EC0-301F-11D3-BF4B-00C04F79EF
> - [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]: F184B08F-C81C-45F6-A57F-5ABD9991F28F

 L’annuaire répertorié pour **TemplatesDir**, qui est *de\\&lt;%TEMPLATE_PATH%&gt;SomeProjectItems*, est le nœud sur le côté gauche de **l’arbre Add New Item** boîte de dialogue. D’autres éléments de l’arbre sont basés sur la sous-direction dans ce répertoire racinaire. Les fichiers disponibles pour être ajoutés au projet sont les éléments dans le bon volet de la boîte de dialogue **Add New Item.**

 Typiquement, ce dossier contiendra les fichiers de modèle pour votre projet tels qu’un fichier HTML ou *.cpp* de modèle, et n’importe quel fichier *.vsz* pour les assistants de départ. Pour contrôler la façon dont les éléments sont affichés, vous pouvez également inclure des fichiers *.vsdir* pour la localisation des noms d’annuaires et des icônes. La chaîne localisée est la légende qui apparaît dans la boîte de dialogue qui représente ce nœud dans **l’arbre de** boîte de dialogue Add New Item.

 Cependant, vous n’avez pas à avoir tout dans un fichier *.vsdir.* Vous pouvez avoir un fichier *.vsdir* pour chaque élément dans l’annuaire. Pour plus d’informations, voir [le fichier Wizard (.vsz) et](../../extensibility/internals/wizard-dot-vsz-file.md) les fichiers de description de [l’annuaire Template (.vsdir).](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)

> [!NOTE]
> Les fichiers *.vsdir* dans les répertoires de modèles sont facultatifs. Si vous souhaitez simplement mettre un élément de projet dans l’annuaire et l’afficher dans la boîte de dialogue **Add New Item,** vous pouvez mettre ce fichier dans l’annuaire des modèles spécifié dans la déclaration **TemplatesDir.** Le fichier sera ensuite affiché dans la partie droite de la boîte de dialogue **Add New Item** pour ce projet. Toutefois, si vous souhaitez afficher une légende localisée pour le fichier ou une icône, vous devez inclure au moins un fichier *.vsdir* dans le répertoire des modèles.

## <a name="group-project-items"></a>Éléments du projet de groupe
 Si vous souhaitez contenir des groupes de modèles dans des dossiers dans **l’arbre de** boîte de dialogue Add New Item, vous devez avoir des sous-directeurs sous le répertoire du modèle racine avec les éléments en eux. Lorsque la boîte de dialogue **Add New Item** est affichée aux utilisateurs, ils verront également les sous-dossiers et seront en mesure de sélectionner les éléments du projet à partir d’eux.

 La priorité de tri dans le segment de code détermine où ce répertoire de modèle sera créé dans l’arbre par rapport à d’autres éléments du nœud d’arbre. Pour la boîte de dialogue **Add New Item,** la priorité de tri est tout ce que vous devez inclure afin que vos articles soient affichés à l’emplacement correct dans la boîte de dialogue.

 Vous pouvez également <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2> implémenter l’interface pour filtrer ce qui est affiché dans la boîte de dialogue **Add New Item.** En implémentant cette interface, vous pouvez configurer un répertoire de modèle sur disque qui contient, par exemple, 50 fichiers de modèle et d’assistant. De cette façon, vous pouvez avoir différents types de projets avec 20 fichiers qui appartiennent à un type de projet, les 30 autres fichiers qui appartiennent à un autre type de projet, et tous les fichiers disponibles dans un type général de projet. De cette manière, selon le modèle de projet créé, vous pouvez afficher un ensemble différent de fichiers de modèle.

 Par exemple, dans le cadre d’un projet Visual Basic, vous pouvez avoir des projets Web et des projets clients. Les formulaires Web ne sont pas des éléments utiles à ajouter à un projet client, et les formulaires Windows ne sont pas des éléments utiles à ajouter à un projet de serveur Web. Par conséquent, vous pouvez créer un répertoire de modèle qui contient tous les fichiers pour les deux types de projet. Ensuite, en <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>implémentant, vous pouvez masquer des éléments qui ne doivent pas être affichés en fonction du type de projet ou des paramètres de projet dans le projet.

## <a name="filter-project-items"></a>Filtrer les éléments du projet
 `IVsFilterAddProjectItemDlg2`prévoit le filtrage des éléments de l’arbre (volet gauche) et des fichiers de projet (volet droit) de la manière suivante :

- Par les noms localisés (légendes affichées dans la boîte de dialogue qui `IVsFilterAddProjectItemDlg`est contenue dans le fichier *.vsdir)* fournies par .

- Par les noms réels des fichiers et dossiers sur disque (non localisé - `IVsFilterAddProjectItemDlg`pas de fichier *.vsdir)* fourni par .

- Par catégorie, `IVsFilterAddProjectItemDlg2`fournie par .

  Pour filtrer par catégorie, fournir une chaîne de catégorie à un élément du fichier *.vsdir,* comme *le formulaire Web* ou *l’élément Client* dans Visual Basic. Le code de la boîte de dialogue récupère ensuite la classification de la catégorie à partir du fichier *.vsdir* et vous la transmet. Vous pouvez ensuite transmettre ces informations `IVsFilterAddProjectItemDlg2` à votre implémentation pour filtrer la boîte de dialogue **Add New Item** par catégories. Vous pouvez également filtrer les éléments pour les pages Web ou en tant que cas d’application Win32 du client. En outre, [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] vous pouvez identifier les éléments étiquetés comme Microsoft Foundation Classes (MFC) ou des modèles actifs (ATL). Lorsque vous identifiez ces éléments, le système de projet peut définir ses propres classifications afin que le système puisse être filtré en fonction des catégories et des classifications.

  Si vous implémentez cette fonctionnalité de filtre, vous n’avez pas à cartographier une table de chaque élément qui doit être caché. Vous pouvez simplement classer les éléments en types et mettre les classifications dans le fichier *.vsdir* ou des fichiers. Ensuite, vous pouvez masquer l’un des éléments qui ont une classification spécifique en implémentant l’interface. De cette façon, vous pouvez faire les éléments dans la dynamique de la boîte de dialogue **Add New Item** basée sur l’état dans le projet.

## <a name="see-also"></a>Voir aussi
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>
- [Enregistrer les modèles de projets et d’objets](../../extensibility/internals/registering-project-and-item-templates.md)
- [CATIDs pour les objets qui sont généralement utilisés pour étendre les projets](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)
- [Ajouter des modèles de projet et d’élément de projet](../../extensibility/internals/adding-project-and-project-item-templates.md)
- [Template directory description (.vsdir) fichiers](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)
- [Fichier Wizard (.vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)
