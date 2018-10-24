---
title: Élément ProjectExtensions (MSBuild) | Microsoft Docs
ms.custom: ''
ms.date: 03/13/2017
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ProjectExtensions
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <ProjectExtensions> element [MSBuild]
- ProjectExtensions element [MSBuild]
ms.assetid: f95f312f-ff92-41eb-9469-ad99e236a307
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e0057d51256f9cddff7c30056d4c669e9f2f2dd7
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49895455"
---
# <a name="projectextensions-element-msbuild"></a>Élément ProjectExtensions (MSBuild)
Permet à des fichiers projet [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] de contenir des informations autres que [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. Tout élément inclus dans un élément `ProjectExtensions` est ignoré par [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].  

 \<Project>  
 \<ProjectExtensions >  

## <a name="syntax"></a>Syntaxe  

```xml  
<ProjectExtensions>  
    Non-MSBuild information to include in file.  
</ProjectExtensions>  
```  

## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  

### <a name="attributes"></a>Attributs  
 Aucun.  

### <a name="child-elements"></a>Éléments enfants  
 Aucun.  

### <a name="parent-elements"></a>Éléments parents  

| Élément | Description |
| - | - |
| [Projet](../msbuild/project-element-msbuild.md) | Élément racine requis d'un fichier projet [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] . |

## <a name="remarks"></a>Notes  
 Un seul élément `ProjectExtensions` peut être utilisé dans un projet [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].  

## <a name="example"></a>Exemple  
 L’exemple de code suivant affiche les informations de l’environnement de développement intégré stockées dans un élément `ProjectExtensions`.  

```xml  
<ProjectExtensions>  
    <VSIDE>  
        <External>  
            <!--  
            Raw XML passed to the IDE by an external source  
            -->  
        </External>  
    </VSIDE>  
</ProjectExtensions>  
```  

## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur le schéma de fichier projet](../msbuild/msbuild-project-file-schema-reference.md)  
 [MSBuild](../msbuild/msbuild.md)
