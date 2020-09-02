---
title: '&lt;&gt;élément FileAssociation (application ClickOnce) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: 4b31ac34627b244cb61b6fdb5c6ca214675ec045
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68150845"
---
# <a name="ltfileassociationgt-element-clickonce-application"></a>&lt;&gt;élément FileAssociation (application ClickOnce)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
|`extension`|Obligatoire. Extension de fichier à associer à l’application.|  
|`description`|Obligatoire. Description du type de fichier à utiliser par l’interpréteur de commandes.|  
|`progid`|Obligatoire. Nom identifiant de façon unique le type de fichier.|  
|`defaultIcon`|Obligatoire. Spécifie l’icône à utiliser pour les fichiers avec cette extension. Le fichier icône doit être spécifié à l’aide de l' [ \<file> élément](../deployment/file-element-clickonce-application.md) dans l' [ \<assembly> élément](../deployment/assembly-element-clickonce-application.md) qui contient cet élément.|  
  
## <a name="remarks"></a>Notes  
 Cet élément doit inclure une référence d’espace de noms XML à « urn : schemas-microsoft-com : ClickOnce. v1 ». Si l' `<fileAssociation>` élément est utilisé, il doit se trouver après l' `<application>` élément dans son [ \<assembly> élément](../deployment/assembly-element-clickonce-application.md)parent.  
  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] ne remplace pas les associations de fichiers existantes. Toutefois, une application ClickOnce peut remplacer l’extension de fichier pour l’utilisateur actuel uniquement. Après la désinstallation de cette application ClickOnce, ClickOnce supprime l’Association de fichiers pour l’utilisateur, et l’Association par ordinateur est à nouveau active.  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant illustre les `fileAssociation` éléments d’un manifeste d’application pour une application d’éditeur de texte déployée à l’aide de [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] . Cet exemple de code comprend également l' [ \<file> élément](../deployment/file-element-clickonce-application.md) requis par l' `defaultIcon` attribut.  
  
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
