---
title: Élément MoreInfoURL (schéma du module linguistique VSIX) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
ms.assetid: 3f07b67b-95c5-4ae8-8b7e-d643cbbb0348
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e8012eb02d143a741cb7eea70c45cabc4ee92002
ms.sourcegitcommit: d9254e54079ae01cdf2d07b11f988faf688f80fc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/11/2020
ms.locfileid: "88114295"
---
# <a name="moreinfourl-element-vsix-language-pack-schema"></a>Élément MoreInfoURL (schéma du module linguistique VSIX)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

facultatif. Lien vers les informations localisées relatives à l’extension.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<MoreInfoURL>URL</MoreInfoURL>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|None||  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|None||  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[Élément VSIXLanguagePack](../extensibility/vsixlanguagepack-element-vsix-language-pack-schema.md)|Obligatoire. Fournit l’élément racine d’un module linguistique VSIX.|  
  
## <a name="text-value"></a>Valeur texte  
 facultatif. Lien vers un site Web. Le lien est une chaîne de texte.  
  
## <a name="element-information"></a>Informations sur les éléments  

:::row:::
    :::column:::
        Espace de noms
    :::column-end:::
    :::column:::
        `http://schemas.microsoft.com/developer/vsx-schema-lp/2010`
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::
        Nom du schéma
    :::column-end:::
    :::column:::
        Schéma du module linguistique VSIX
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::
        Fichier de validation
    :::column-end:::
    :::column:::
        VSIXLanguagePackSchema. xsd
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::
        Peut être vide
    :::column-end:::
    :::column:::
        Non applicable
    :::column-end:::
:::row-end:::

## <a name="see-also"></a>Voir aussi  
 [Référence de schéma du module linguistique VSX](../extensibility/vsx-language-pack-schema-reference.md)   
 [Localisation de packages VSIX](../extensibility/localizing-vsix-packages.md)   
 [Informations de référence sur le schéma d’extension VSIX 1,0](/previous-versions/dd393700(v=vs.110))
