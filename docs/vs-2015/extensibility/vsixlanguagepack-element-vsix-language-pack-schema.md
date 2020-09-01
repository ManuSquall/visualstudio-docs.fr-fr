---
title: Élément VSIXLanguagePack (schéma du module linguistique VSIX) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
ms.assetid: 767f5c22-8b87-49ca-92aa-a7a3f026469f
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e2e1df362fddeab5be98ff90460a8a1a7d4b7876
ms.sourcegitcommit: 26178b116cbf7353fee6ca989b8d872114f7b405
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/01/2020
ms.locfileid: "89284334"
---
# <a name="vsixlanguagepack-element-vsix-language-pack-schema"></a>Élément VSIXLanguagePack (schéma du module linguistique VSIX)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Obligatoire. Fournit l’élément racine d’un module linguistique VSIX. Le module linguistique VSIX fournit des informations d’installation localisées pour un package VSIX.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<VSIXLanguagePack>  
  <LocalizedName>...</LocalizedName>  
  <LocalizedDescription>...</LocalizedDescription>  
  <MoreInfoURL>...</MoreInfoURL>  
  <License>...</License>  
</VSIXLanguagePack>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`xmlns`|Espace de noms XML dans lequel le schéma du module linguistique VSIX est défini.|  
  
## <a name="xmlns-attribute"></a>Attribut xmlns  
  
|Valeur|Description|  
|-----------|-----------------|  
|`http://schemas.microsoft.com/developer/vsx-schema-lp/2010`|Obligatoire. Emplacement du fichier qui définit le schéma pour les modules linguistiques.|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[Élément LocalizedName](../extensibility/localizedname-element-vsix-language-pack-schema.md)|Obligatoire. Nom localisé de l’extension à installer.|  
|[Élément LocalizedDescription](../extensibility/localizeddescription-element-vsix-language-pack-schema.md)|Obligatoire. Description localisée de l’extension à installer.|  
|[Élément MoreInfoURL](../extensibility/moreinfourl-element-vsix-language-pack-schema.md)|facultatif. Lien vers les informations localisées relatives à l’extension.|  
|[Élément de licence](../extensibility/license-element-vsix-language-pack-schema.md)|facultatif. Chemin d’accès d’une version localisée du fichier de licence pour l’extension.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|Aucune||  
  
## <a name="element-information"></a>Informations sur les éléments  
  
|                 |                                                           |
|-----------------|-----------------------------------------------------------|
|    Espace de noms    | `http://schemas.microsoft.com/developer/vsx-schema-lp/2010` |
|   Nom du schéma   |                 Schéma du module linguistique VSIX                 |
| Fichier de validation |                VSIXLanguagePackSchema. xsd                 |
|  Peut être vide   |                            Non                             |
  
## <a name="see-also"></a>Voir aussi  
 [Référence de schéma du module linguistique VSX](../extensibility/vsx-language-pack-schema-reference.md) [localisation des packages VSIX](../extensibility/localizing-vsix-packages.md) [extension du schéma de l’extension VSIX 1,0](/previous-versions/dd393700(v=vs.110))
