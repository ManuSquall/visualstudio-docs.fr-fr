---
title: License, élément (schéma du module linguistique VSIX) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
ms.assetid: 57dac3b7-0cdd-405c-9af5-30ed9ca45e53
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 91f0792f64e09292836a3b2d60f669c67903b3a7
ms.sourcegitcommit: d9254e54079ae01cdf2d07b11f988faf688f80fc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/11/2020
ms.locfileid: "88114168"
---
# <a name="license-element-vsix-language-pack-schema"></a>Élément License (schéma du module linguistique VSIX)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

facultatif. Chemin d’accès d’une version localisée du fichier de licence pour l’extension.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<License>FilePath\license.txt</License>  
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
 Chemin d’accès relatif du fichier de licence localisé à afficher.  
  
## <a name="remarks"></a>Notes  
 Si l' `License` élément est défini, le texte du fichier de licence désigné s’affiche pendant l’installation et l’utilisateur doit accepter la licence pour continuer.  
  
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
