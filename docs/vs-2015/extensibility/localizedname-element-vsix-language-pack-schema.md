---
title: Élément LocalizedName (schéma du module linguistique VSIX) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 57b7f502-3b04-42d9-90d5-f57772a7c757
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5b183a0cbbf79442e8e5b79df14dd3a9dc091571
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51759884"
---
# <a name="localizedname-element-vsix-language-pack-schema"></a>Élément LocalizedName (schéma du module linguistique VSIX)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Obligatoire. Le nom localisé de l’extension à installer.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<Name>Localized name of the extension</Name>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|Aucun.||  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|Aucun.||  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[Élément VSIXLanguagePack](../extensibility/vsixlanguagepack-element-vsix-language-pack-schema.md)|Obligatoire. Fournit l’élément racine pour un module linguistique VSIX.|  
  
## <a name="text-value"></a>Valeur texte  
 Obligatoire. Le nom du module linguistique dans le langage cible.  
  
## <a name="element-information"></a>Informations sur les éléments  
  
|                 |                                                           |
|-----------------|-----------------------------------------------------------|
|    Espace de noms    | http://schemas.microsoft.com/developer/vsx-schema-lp/2010 |
|   Nom du schéma   |                 Schéma du module linguistique VSIX                 |
| Fichier de validation |                VSIXLanguagePackSchema.xsd                 |
|  Peut être vide   |                      Non applicable                       |
  
## <a name="see-also"></a>Voir aussi  
 [Référence de schéma du module linguistique VSX](../extensibility/vsx-language-pack-schema-reference.md)   
 [Localisation de Packages VSIX](../extensibility/localizing-vsix-packages.md)   
 [Référence du schéma 1.0 Extension VSIX](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)

