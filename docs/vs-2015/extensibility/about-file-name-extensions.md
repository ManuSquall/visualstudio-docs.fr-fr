---
title: À propos des extensions de nom de fichier | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- file extensions
- file name extensions
ms.assetid: 99f4f9ff-fb84-4258-9787-6890f308a57f
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 866a30279ca2c79f4a490a040f76bc3a86c6a6e1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68148033"
---
# <a name="about-file-name-extensions"></a>À propos des extensions de nom de fichier
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Lorsque vous inscrivez une extension de fichier d’un VSPackage, vous l’associez à une version de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Cela est important si plusieurs versions de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] sont installées sur un ordinateur.  
  
 Les extensions de fichier pour les VSPackages sont inscrites sous HKEY_CLASSES_ROOT clé avec une valeur par défaut qui pointe vers l’identificateur programmatique (ProgID) associé.  
  
 Voici un exemple d’informations d’inscription pour l’extension de fichier. vcproj :  
  
```  
HKEY_CLASSES_ROOT\  
   .vcproj\  
      (default)=" VisualStudio.vcproj.8.0"   
```  
  
 Les fichiers associés à [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] doivent avoir un ProgID avec version, tel que `VisualStudio.vcproj.8.0` , pour permettre l’installation côte à côte du produit afin de conserver les associations d’extension de fichier entre les versions du produit. Un ProgID spécifique à la version vous permet également d’utiliser des verbes standard, tels que Open, Edit, etc., sans qu’il soit important de remplacer ou d’être remplacé par d’autres applications ou versions de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
 Dans certains cas, l’identificateur de programme (ProgID) associé à une extension de fichier ne doit pas être modifié. Par exemple, le ProgID de l’extension de fichier. htm (ProgID = htmlfile) est codé en dur dans un certain nombre d’emplacements dans le système d’exploitation et est largement connu et utilisé en association avec les fichiers. htm et. html.  
  
## <a name="see-also"></a>Voir aussi  
 [Inscription des extensions de nom de fichier pour les déploiements côte à côte](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)   
 [Spécification des gestionnaires de fichiers pour les extensions de nom de fichier](../extensibility/specifying-file-handlers-for-file-name-extensions.md)
