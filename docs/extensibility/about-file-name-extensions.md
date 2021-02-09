---
title: À propos des extensions de nom de fichier | Microsoft Docs
description: Découvrez comment inscrire des extensions de nom de fichier pour les VSPackages et les associer à une version spécifique de Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- file extensions
- file name extensions
ms.assetid: 99f4f9ff-fb84-4258-9787-6890f308a57f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c3f938eb31c06e1e88af21b058b4475bc192d49c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99874407"
---
# <a name="about-file-name-extensions"></a>À propos des extensions de nom de fichier
Lorsque vous inscrivez une extension de fichier d’un VSPackage, vous l’associez à une version de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Cela est important si plusieurs versions de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] sont installées sur un ordinateur.

 Les extensions de fichier pour les VSPackages sont inscrites sous **HKEY_CLASSES_ROOT** clé avec une valeur par défaut qui pointe vers l’identificateur programmatique (ProgID) associé.

 L’exemple suivant montre des informations d’inscription pour l’extension de fichier *. vcproj* :

```
HKEY_CLASSES_ROOT\
   .vcproj\
      (default)=" VisualStudio.vcproj.8.0"
```

 Les fichiers associés à [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] doivent avoir un ProgID avec version, tel que `VisualStudio.vcproj.8.0` . Un ProgID avec version permet aux installations côte à côte du produit de gérer les associations d’extension de fichier parmi les versions de produit. Un ProgID spécifique à la version vous permet également d’utiliser des verbes standard, tels que Open, Edit, etc., sans qu’il soit important de remplacer ou d’être remplacé par d’autres applications ou versions de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

 Dans certains cas, l’identificateur de programme (ProgID) associé à une extension de fichier ne doit pas être modifié. Par exemple, le ProgID de l’extension de fichier *. htm* (ProgID = htmlfile) est codé en dur dans un certain nombre d’emplacements dans le système d’exploitation et est largement connu et utilisé en association avec les fichiers *. htm* et *. html* .

## <a name="see-also"></a>Voir aussi
- [Inscrire des extensions de nom de fichier pour les déploiements côte à côte](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)
- [Spécifier des gestionnaires de fichiers pour les extensions de nom de fichier](../extensibility/specifying-file-handlers-for-file-name-extensions.md)
