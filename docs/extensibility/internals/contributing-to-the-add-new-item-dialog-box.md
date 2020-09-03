---
title: Contribution à la boîte de dialogue Ajouter un nouvel élément | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80709277"
---
# <a name="contribute-to-the-add-new-item-dialog-box"></a>Contribuer à la boîte de dialogue Ajouter un nouvel élément
Un sous-type de projet peut fournir un nouveau répertoire complet d’éléments pour la boîte de dialogue **Ajouter un nouvel élément** en inscrivant ajouter des modèles d' **élément** sous la sous-clé de Registre **projects** .

## <a name="register-add-new-item-templates"></a>Inscrire ajouter un nouvel élément modèles
 Cette section se trouve sous **HKEY_LOCAL_MACHINE \software\microsoft\visualstudio\8.0\Projects** dans le registre. Les entrées de Registre ci-dessous supposent un [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] projet agrégé par un sous-type de projet hypothétique. Les entrées du [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] projet sont répertoriées ci-dessous.

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

 La sous-clé **AddItemTemplates\TemplateDirs** contient des entrées de Registre avec le chemin d’accès au répertoire où les éléments rendus disponibles dans la boîte de dialogue **Ajouter un nouvel élément** sont placés.

 L’environnement charge automatiquement toutes les données **AddItemTemplates** sous la sous-clé de Registre **projects** . Ces données peuvent inclure les données pour les implémentations de projet de base, ainsi que les données pour des types de sous-types de projet spécifiques. Chaque sous-type de projet est identifié par un **GUID**de type de projet. Le sous-type de projet peut spécifier qu’un autre ensemble de modèles d' **Ajout d’élément** doit être utilisé pour une instance de projet aromatisée particulière en prenant en charge l' `VSHPROPID_ AddItemTemplatesGuid` énumération à partir de <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> dans l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> implémentation de pour retourner la valeur GUID du sous-type de projet. Si la `VSHPROPID_AddItemTemplatesGuid` propriété n’est pas spécifiée, le GUID du projet de base est utilisé.

 Vous pouvez filtrer les éléments dans la boîte de dialogue **Ajouter un nouvel élément** en implémentant l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg> interface sur l’objet d’agrégation de sous-type de projet. Par exemple, un sous-type de projet qui implémente un projet de base de données en regroupant un [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] projet, peut filtrer les [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] éléments spécifiques de la boîte de dialogue **Ajouter un nouvel élément** en implémentant le filtrage et, à son tour, peut ajouter des éléments spécifiques au projet de base de données en prenant en charge `VSHPROPID_ AddItemTemplatesGuid` dans <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> . Pour plus d’informations sur le filtrage et l’ajout d’éléments à la boîte de dialogue **Ajouter un nouvel élément** , consultez [Ajouter des éléments à la boîte de dialogue Ajouter un nouvel élément](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md).

## <a name="see-also"></a>Voir aussi
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>
- [CATID des objets qui sont généralement utilisés pour étendre des projets](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)
