---
title: Contribuer à l’ajout d’une nouvelle boîte de dialogue d’articles (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Add New Item dialog box, contributing to
ms.assetid: b2e53175-9372-4d17-8c2b-9264c9e51e9c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 83444d9be6ba23392b792a0187bf46dc9920c465
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709277"
---
# <a name="contribute-to-the-add-new-item-dialog-box"></a>Contribuer à la boîte de dialogue Add New Item
Un sous-type de projet peut fournir un nouvel annuaire complet des éléments pour la boîte de dialogue **Add New Item** en enregistrant des modèles Add **Item** sous le sous-clé du registre **des projets.**

## <a name="register-add-new-item-templates"></a>Inscrivez-vous Ajouter de nouveaux modèles d’objets
 Cette section est située sous **HKEY_LOCAL_MACHINE-SOFTWARE-Microsoft-VisualStudio-8.0-Projets** dans le registre. Les inscriptions au [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] registre ci-dessous supposent un projet agrégé par un sous-type hypothétique de projet. Les entrées [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pour le projet sont énumérées ci-dessous.

```
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Projects\{F184B08F-C81C-45F6-A57F-5ABD9991F28F}]
@="#2143"
"DefaultProjectExtension"="vbproj"
"PossibleProjectExtensions"="vbproj;vbp"
"ProjectTemplatesDir"="visualStudioInstallPath\\Vb\\.\\VBProjects"

[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Projects\{F184B08F-C81C-45F6-A57F-5ABD9991F28F}\AddItemTemplates\TemplateDirs\{12345678-1234-1234-1122334455667788}\/1]
@="#100"
"TemplatesDir"="projectSubTypeTemplatesDir\\VBProjectItems"
```

 Le sous-clé **AddItemTemplates-TemplateDirs** contient des entrées de registre avec le chemin vers l’annuaire où les articles mis à disposition dans la boîte de dialogue **Add New Item** sont placés.

 L’environnement charge automatiquement toutes les données **AddItemTemplates** sous la sous-clé du registre **des projets.** Ces données peuvent inclure les données relatives aux implémentations de projets de base ainsi que les données relatives à des types spécifiques de sous-types de projets. Chaque sous-type de projet est identifié par un type de projet **GUID**. Le sous-type de projet peut spécifier qu’un autre ensemble de modèles `VSHPROPID_ AddItemTemplatesGuid` **d’éléments d’ajout** doit être utilisé pour une instance de projet aromatisée particulière en soutenant le recensement de <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> la mise en <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> œuvre pour retourner la valeur GUID du sous-type du projet. Si `VSHPROPID_AddItemTemplatesGuid` la propriété n’est pas spécifiée, le projet de base GUID est utilisé.

 Vous pouvez filtrer les éléments de la boîte <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg> de dialogue Add New **Item** en implémentant l’interface sur l’objet d’agrégateur de sous-type de projet. Par exemple, un sous-type de projet qui implémente un [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] projet [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] de base de données en agrégeant un projet, peut filtrer les éléments `VSHPROPID_ AddItemTemplatesGuid` <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>spécifiques de la boîte de dialogue Add **New Item** en implémentant le filtrage, et à son tour, peut ajouter des éléments spécifiques à un projet de base de données en soutenant . Pour plus d’informations sur le filtrage et l’ajout d’éléments à la boîte de dialogue **Add New Item,** voir [Ajouter des éléments à la boîte de dialogue Add New Item](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md).

## <a name="see-also"></a>Voir aussi
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>
- [CATIDs pour les objets qui sont généralement utilisés pour étendre les projets](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)
