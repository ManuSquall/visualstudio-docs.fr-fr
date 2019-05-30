---
title: À propos des Extensions de nom de fichier | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- file extensions
- file name extensions
ms.assetid: 99f4f9ff-fb84-4258-9787-6890f308a57f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 60a721581c3deb4588df59974768c634c2e9515f
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66313717"
---
# <a name="about-file-name-extensions"></a>À propos des extensions de nom de fichier
Lorsque vous inscrivez une extension de fichier d’un VSPackage, associez-la à une version de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Cela est important si, et plusieurs versions de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] est installé sur un ordinateur.

 Extensions de fichier pour les VSPackages sont enregistrées sous **HKEY_CLASSES_ROOT** clé avec une valeur par défaut qui pointe vers l’associée identificateur programmatique (ProgID).

 L’exemple suivant montre les informations d’inscription pour le *.vcproj* extension de fichier :

```
HKEY_CLASSES_ROOT\
   .vcproj\
      (default)=" VisualStudio.vcproj.8.0"
```

 Fichiers associés [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] doit avoir un ProgID avec contrôle de version, tel que `VisualStudio.vcproj.8.0`. Un ProgID avec contrôle de version permet des installations côte à côte du produit pour gérer les associations d’extension de fichier entre les versions de produit. Un ProgID spécifique à la version vous permet également d’utiliser des verbes standards, telles qu’Ouvrir, modifier et ainsi de suite, sans vous préoccuper de remplacer ni être remplacé par d’autres applications ou les versions de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

 Dans certains cas, le ProgID associé à une extension de fichier ne doit pas être modifié. Par exemple, le ProgID pour le *.htm* extension de fichier (progid = htmlfile) est codé en dur dans plusieurs emplacements dans le système d’exploitation, et est largement connue et utilisée en association avec *.htm* et *.html* fichiers.

## <a name="see-also"></a>Voir aussi
- [Inscrire des extensions de nom de fichier pour les déploiements côte à côte](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)
- [Spécifier des gestionnaires de fichier pour les extensions de nom de fichier](../extensibility/specifying-file-handlers-for-file-name-extensions.md)