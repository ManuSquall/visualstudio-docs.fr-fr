---
title: '&lt;fileAssociation&gt; , élément (Application ClickOnce) | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <fileAssociation> element [ClickOnce application manifest]
- manifests [ClickOnce], fileAssociation element
ms.assetid: 8f951b4f-54f9-412e-a9e5-af4e379fcf08
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 3a3589387b00eb1ade9c9b60b0845bc2421b3486
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47493188"
---
# <a name="ltfileassociationgt-element-clickonce-application"></a>&lt;fileAssociation&gt; , élément (Application ClickOnce)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [ &lt;fileAssociation&gt; , élément (Application ClickOnce)](https://docs.microsoft.com/visualstudio/deployment/fileassociation-element-clickonce-application).  
  
Identifie une extension de fichier à associer à l’application.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<fileAssociation  
    xmlns="urn:schemas-microsoft-com:clickonce.v1"  
    extension  
    description  
    progid  
    defaultIcon  
/>  
```  
  
## <a name="elements-and-attributes"></a>Éléments et attributs  
 L’élément `fileAssociation` est facultatif. L’élément a les attributs suivants.  
  
|Attribut|Description|  
|---------------|-----------------|  
|`extension`|Obligatoire. L’extension de fichier à associer à l’application.|  
|`description`|Obligatoire. Description du type de fichier pour une utilisation par l’interpréteur de commandes.|  
|`progid`|Obligatoire. Un nom identifiant de manière unique le type de fichier.|  
|`defaultIcon`|Obligatoire. Spécifie l’icône à utiliser pour les fichiers avec cette extension. Le fichier icône doit être spécifié à l’aide de la [ \<fichier > élément](../deployment/file-element-clickonce-application.md) au sein de la [ \<assembly > élément](../deployment/assembly-element-clickonce-application.md) qui contient cet élément.|  
  
## <a name="remarks"></a>Notes  
 Cet élément doit inclure une référence d’espace de noms XML à « urn : schemas-microsoft-ClickOnce.v 1 ». Si le `<fileAssociation>` élément est utilisé, il doit être placée après le `<application>` élément dans son parent [ \<assembly > élément](../deployment/assembly-element-clickonce-application.md).  
  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] ne remplace pas les associations de fichiers existantes. Toutefois, une application ClickOnce peut remplacer l’extension de fichier pour l’utilisateur actuel uniquement. Une fois que cette application ClickOnce est désinstallée, ClickOnce supprime l’association de fichier pour l’utilisateur, et l’association de la machine est à nouveau active.  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant illustre `fileAssociation` manifeste des éléments dans une application pour un éditeur de texte déployé à l’aide [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]. Cet exemple de code inclut également le [ \<fichier > élément](../deployment/file-element-clickonce-application.md) requis par le `defaultIcon` attribut.  
  
```  
<file name="text.ico" size="4286">  
  <hash>  
    <dsig:Transforms>  
      <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />  
    </dsig:Transforms>  
    <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />  
    <dsig:DigestValue>0joAqhmfeBb93ZneZv/oTMP2brY=</dsig:DigestValue>  
  </hash>  
</file>  
<file name="writing.ico" size="9662">  
  <hash>  
    <dsig:Transforms>  
      <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />  
    </dsig:Transforms>  
    <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />  
    <dsig:DigestValue>2cL2U7cm13nG40v9MQdxYKazIwI=</dsig:DigestValue>  
  </hash>  
</file>  
<fileAssociation xmlns="urn:schemas-microsoft-com:clickonce.v1" extension=".text" description="Text  Document (ClickOnce)" progid="Text.Document" defaultIcon="text.ico" />  
<fileAssociation xmlns="urn:schemas-microsoft-com:clickonce.v1" extension=".writing" description="Writings (ClickOnce)" progid="Writing.Document" defaultIcon="writing.ico" />  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Manifeste d’application ClickOnce](../deployment/clickonce-application-manifest.md)



