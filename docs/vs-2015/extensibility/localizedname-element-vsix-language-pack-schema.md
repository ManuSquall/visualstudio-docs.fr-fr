---
title: Élément LocalizedName (schéma du module linguistique VSIX) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
ms.assetid: 57b7f502-3b04-42d9-90d5-f57772a7c757
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0747dfe89c2d8d4ceb8321f00f723f973f3ff526
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58951272"
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
 [Référence du schéma 1.0 Extension VSIX](http://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)
