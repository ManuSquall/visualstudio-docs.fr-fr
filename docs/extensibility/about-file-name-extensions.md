---
title: À propos des extensions de nom de fichier ( Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- file extensions
- file name extensions
ms.assetid: 99f4f9ff-fb84-4258-9787-6890f308a57f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 03e07ec233ef975441a1f10507f0db872051558f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740349"
---
# <a name="about-file-name-extensions"></a>À propos des extensions de nom de fichier
Lorsque vous enregistrez une extension de fichier d’un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]VSPackage, vous l’associez à une version de . Ceci est important si plus [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] d’une version de est installé sur un ordinateur.

 Les extensions de fichiers pour VSPackages sont enregistrées sous **HKEY_CLASSES_ROOT** clé avec une valeur par défaut qui indique l’identifiant programmatique associé (ProgID).

 L’exemple suivant montre les informations d’inscription pour l’extension du fichier *.vcproj* :

```
HKEY_CLASSES_ROOT\
   .vcproj\
      (default)=" VisualStudio.vcproj.8.0"
```

 Fichiers associés [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] à doit avoir une version `VisualStudio.vcproj.8.0`ProgID, tels que . Un ProgID versionné permet aux installations côte à côte du produit de maintenir les associations d’extension de fichiers entre les versions de produits. Une version spécifique ProgID vous permet également d’utiliser des verbes standard, tels que l’ouverture, l’édition, et [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]ainsi de suite, sans le souci de l’écriture ou d’être écrasé par d’autres applications ou versions de .

 Dans certains cas, le ProgID associé à une extension de fichier ne doit pas être modifié. Par exemple, le ProgID pour l’extension de fichier *.htm* (progid - htmlfile) est codé dur dans un certain nombre d’endroits dans le système d’exploitation, et est largement connu et utilisé en association avec des fichiers *.htm* et *.html.*

## <a name="see-also"></a>Voir aussi
- [Enregistrer les extensions de noms de fichiers pour les déploiements côte à côte](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)
- [Spécifier les gestionnaires de fichiers pour les extensions de nom de fichier](../extensibility/specifying-file-handlers-for-file-name-extensions.md)
