---
title: "&#192; propos des Extensions de nom de fichier | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "extensions de fichier"
  - "extensions de nom de fichier"
ms.assetid: 99f4f9ff-fb84-4258-9787-6890f308a57f
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# &#192; propos des Extensions de nom de fichier
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Lorsque vous inscrivez une extension de fichier d'un VSPackage, vous l'associer à une version de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Ceci est important si plusieurs versions du [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] est installée sur un ordinateur.  
  
 Les extensions de fichier pour les VSPackages sont stockées sous la clé de HKEY\_CLASSES\_ROOT avec une valeur par défaut qui indique le progid associé \(progid\).  
  
 Voici un exemple des informations d'inscription pour l'extension de fichier .vcproj :  
  
```  
HKEY_CLASSES_ROOT\  
   .vcproj\  
      (default)=" VisualStudio.vcproj.8.0"   
```  
  
 Les fichiers associés à [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] doivent avoir un progid avec version, tel qu' `VisualStudio.vcproj.8.0`, pour permettre côte à côte dans les installations du produit pour gérer les associations d'extension de fichier entre les versions du produit.  Un progid spécifique à la version vous permet également aux verbes standard d'utilisation, tels que ouvert, la modification, etc., sans problème de remplacer ou remplacé par d'autres applications ou versions de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 Dans certains cas, l'identificateur programmatique associé à une extension de fichier ne doit pas être modifié.  Par exemple, l'identificateur programmatique pour l'extension de fichier .htm \(progid \= htmlfile\) est codé en dur dans un certain nombre de bits dans le système d'exploitation, et est largement connu et utilisé en liaison avec les fichiers .htm et .html.  
  
## Voir aussi  
 [L’inscription des Extensions de nom de fichier pour les déploiements côte à côte](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)   
 [Spécification des gestionnaires de fichiers pour les Extensions de nom de fichier](../extensibility/specifying-file-handlers-for-file-name-extensions.md)