---
title: "&lt;fileAssociation&gt; Element (ClickOnce Application) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "<fileAssociation> element [ClickOnce application manifest]"
  - "manifests [ClickOnce], fileAssociation element"
ms.assetid: 8f951b4f-54f9-412e-a9e5-af4e379fcf08
caps.latest.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 8
---
# &lt;fileAssociation&gt; Element (ClickOnce Application)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Identifie une extension de fichier à associer à l'application.  
  
## Syntaxe  
  
```  
<fileAssociation  
    xmlns="urn:schemas-microsoft-com:clickonce.v1"  
    extension  
    description  
    progid  
    defaultIcon  
/>  
```  
  
## Éléments et attributs  
 L'attribut `fileAssociation` est facultatif.  L'élément possède les attributs suivants.  
  
|Attribut|Description|  
|--------------|-----------------|  
|`extension`|Obligatoire.  Extension de fichier à associer à l'application.|  
|`description`|Obligatoire.  Description du type de fichier pour une utilisation par le shell.|  
|`progid`|Obligatoire.  Nom n'identifiant que le type de fichier.|  
|`defaultIcon`|Obligatoire.  Spécifie l'icône à utiliser pour les fichiers avec cette extension.  Le fichier icône doit être spécifié à l'aide de l'[\<file\> Element](../Topic/%3Cfile%3E%20Element%20\(ClickOnce%20Application\).md) de l'[\<assembly\> Element](../deployment/assembly-element-clickonce-application.md) qui contient cet élément.|  
  
## Notes  
 Cet élément doit inclure la référence à l'espace de noms XML « urn:schemas\-microsoft\-com:clickonce.v 1 ».  Si l'élément `<fileAssociation>` est utilisé, il doit se situer après l'élément `<application>` dans son [\<assembly\> Element](../deployment/assembly-element-clickonce-application.md) parent.  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] ne remplace pas les associations de fichiers existantes.  Toutefois, une application ClickOnce peut remplacer l'extension de fichier pour l'utilisateur actuel uniquement.  Une fois l'application ClickOnce désinstallée, ClickOnce supprime l'association de fichiers pour l'utilisateur et l'association par ordinateur est à nouveau active.  
  
## Exemple  
 L'exemple de code suivant illustre les éléments `fileAssociation` d'un manifeste d'application pour un éditeur de texte déployé avec [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  Cet exemple de code inclut également l'[\<file\> Element](../Topic/%3Cfile%3E%20Element%20\(ClickOnce%20Application\).md) requis par l'attribut `defaultIcon`.  
  
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
  
## Voir aussi  
 [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md)