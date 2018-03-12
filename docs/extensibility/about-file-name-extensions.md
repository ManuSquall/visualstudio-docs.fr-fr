---
title: "À propos des Extensions de nom de fichier | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- file extensions
- file name extensions
ms.assetid: 99f4f9ff-fb84-4258-9787-6890f308a57f
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 8f504a70950ea9e808d50bd8b9bc7ef5dd92d699
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="about-file-name-extensions"></a>À propos des Extensions de nom de fichier
Lorsque vous inscrivez une extension de fichier d’un VSPackage, associez-la à une version de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Cela est important si, et plusieurs versions de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] est installé sur un ordinateur.  
  
 Extensions de fichier pour les VSPackages sont enregistrées sous la clé HKEY_CLASSES_ROOT avec une valeur par défaut qui pointe vers l’associée identificateur programmatique (ProgID).  
  
 Voici un exemple des informations d’inscription de l’extension de fichier .vcproj :  
  
```  
HKEY_CLASSES_ROOT\  
   .vcproj\  
      (default)=" VisualStudio.vcproj.8.0"   
```  
  
 Fichiers associés [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] doit avoir un contrôle de version du ProgID, tel que `VisualStudio.vcproj.8.0`, pour autoriser les installations côte à côte du produit à mettre à jour les associations d’extensions de fichier entre les versions de produit. Un ProgID spécifique à la version vous permet également d’utiliser des verbes standard, par exemple ouvrir, modifier et ainsi de suite, sans vous préoccuper de remplacer ou être remplacé par d’autres applications ou les versions de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 Dans certains cas, le ProgID associé à une extension de fichier ne doit pas être modifié. Par exemple, le ProgID de l’extension de fichier .htm (progid = htmlfile) est codé dans plusieurs emplacements dans le système d’exploitation en dur, et est largement connue et utilisée dans l’association avec les fichiers .htm et .html.  
  
## <a name="see-also"></a>Voir aussi  
 [L’inscription des Extensions de nom de fichier pour les déploiements côte à côte](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)   
 [Spécification des gestionnaires de fichiers pour les extensions de nom de fichier](../extensibility/specifying-file-handlers-for-file-name-extensions.md)