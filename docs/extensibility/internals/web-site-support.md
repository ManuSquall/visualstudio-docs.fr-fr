---
title: Soutien au site Web (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- web site projects
ms.assetid: ce9f4266-bb64-4c09-be88-4bd6413f60d0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 22047ad1b0709cefa200656e61f8e0d39ace94c9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703443"
---
# <a name="web-site-support"></a>Prise en charge de site web
Un système de projet de site Web est un système de projet qui crée des projets Web. Les projets Web créent à leur tour des applications Web. Un projet de site Web génère un fichier exécutable pour chaque page Web qui a associé le code. D’autres fichiers exécutables sont générés à partir des fichiers de code source dans le dossier /App_Code.

 Les systèmes de projets de sites Web sont créés en ajoutant des modèles et des attributs d’enregistrement à un système de projet existant. L’un de ces attributs sélectionne le fournisseur IntelliSense pour la langue. La mise en œuvre du fournisseur IntelliSense gère les références et appelle le compilateur de langue lorsqu’une page Web intelligente qui n’est pas mise en cache est demandée.

 Le compilateur de langue utilisé pour compiler les pages Web doit être enregistré avec [!INCLUDE[vstecasp](../../code-quality/includes/vstecasp_md.md)]. Vous pouvez utiliser le [ \<compilateur> Element](/dotnet/framework/configure-apps/file-schema/compiler/compiler-element) dans un fichier Web.config pour enregistrer le compilateur, comme dans l’exemple suivant :

```
<system.codedom>  <compilers>    <compiler language="py;IronPython" extension=".py"       type="IronPython.CodeDom.PythonProvider, IronPython,       Version=1.0.2391.18146, Culture=neutral,       PublicKeyToken=b03f5f7f11d50a3a" />  </compilers></system.codedom>
```

## <a name="in-this-section"></a>Dans cette section
- [Modèles de prise en charge de site web](../../extensibility/internals/web-site-support-templates.md)

 Répertoriez les modèles que vous pouvez utiliser pour créer de nouveaux projets de sites Web et des éléments associés.

- [Attributs de prise en charge de site web](../../extensibility/internals/web-site-support-attributes.md)

 Présente les attributs d’enregistrement qui [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] [!INCLUDE[vstecasp](../../code-quality/includes/vstecasp_md.md)]relient un projet de site Web à et .

## <a name="related-sections"></a>Sections connexes
- [Projets web](../../extensibility/internals/web-projects.md)

 Présente un aperçu des deux types de projets Web, des projets de sites Web et des projets d’applications Web.
