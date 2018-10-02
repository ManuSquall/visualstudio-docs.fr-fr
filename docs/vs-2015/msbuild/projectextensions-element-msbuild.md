---
title: Élément ProjectExtensions (MSBuild) | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 156a35a953169c5b1ed8208c8d4f044f7b9fa36f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47508716"
---
# <a name="projectextensions-element-msbuild"></a>ProjectExtensions, élément (MSBuild)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [ProjectExtensions, élément (MSBuild)](https://docs.microsoft.com/visualstudio/msbuild/projectextensions-element-msbuild).  
  
  
Permet à des fichiers projet [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] de contenir des informations autres que [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]. Tout élément inclus dans un élément `ProjectExtensions` est ignoré par [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)].  
  
 \<Project>  
 \<ProjectExtensions >  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
  
|Élément|Description|  
|-------------|-----------------|  
|[Projet](../msbuild/project-element-msbuild.md)|Élément racine requis d'un fichier projet [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)].|  
  
## <a name="remarks"></a>Notes  
 Un seul élément `ProjectExtensions` peut être utilisé dans un projet [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)].  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant affiche les informations de l’environnement de développement intégré stockées dans un élément `ProjectExtensions`.  
  
```  
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
 [Informations de référence sur le schéma de fichier projet MSBuild](../msbuild/msbuild-project-file-schema-reference.md)  
 [MSBuild](msbuild.md)


