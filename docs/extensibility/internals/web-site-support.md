---
title: Prise en charge des sites Web | Microsoft Docs
description: En savoir plus sur les systèmes de projet de site Web, qui sont créés en ajoutant des modèles et des attributs d’inscription à un système de projet existant.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- web site projects
ms.assetid: ce9f4266-bb64-4c09-be88-4bd6413f60d0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 141e4acf7db61130de859f38891670e69d3bd640
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99940018"
---
# <a name="web-site-support"></a>Prise en charge de site web
Un système de projet de site Web est un système de projet qui crée des projets Web. Les projets Web créent à leur tour des applications Web. Un projet de site Web génère un fichier exécutable pour chaque page Web associée à du code. Des fichiers exécutables supplémentaires sont générés à partir des fichiers de code source dans le dossier/App_Code.

 Les systèmes de projet de site Web sont créés en ajoutant des modèles et des attributs d’inscription à un système de projet existant. L’un de ces attributs sélectionne le fournisseur IntelliSense pour le langage. L’implémentation du fournisseur IntelliSense gère les références et appelle le compilateur de langage lorsqu’une page Web intelligente qui n’est pas mise en cache est demandée.

 Le compilateur de langage utilisé pour compiler des pages Web doit être inscrit auprès de [!INCLUDE[vstecasp](../../code-quality/includes/vstecasp_md.md)] . Vous pouvez utiliser l' [ \<compiler> élément](/dotnet/framework/configure-apps/file-schema/compiler/compiler-element) dans un fichier de Web.config pour inscrire le compilateur, comme dans l’exemple suivant :

```
<system.codedom>  <compilers>    <compiler language="py;IronPython" extension=".py"       type="IronPython.CodeDom.PythonProvider, IronPython,       Version=1.0.2391.18146, Culture=neutral,       PublicKeyToken=b03f5f7f11d50a3a" />  </compilers></system.codedom>
```

## <a name="in-this-section"></a>Dans cette section
- [Modèles de prise en charge de site web](../../extensibility/internals/web-site-support-templates.md)

 Répertorie les modèles que vous pouvez utiliser pour créer des projets de site Web et des éléments associés.

- [Attributs de prise en charge de site web](../../extensibility/internals/web-site-support-attributes.md)

 Présente les attributs d’inscription qui connectent un projet de site Web à [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] et [!INCLUDE[vstecasp](../../code-quality/includes/vstecasp_md.md)] .

## <a name="related-sections"></a>Sections connexes
- [Projets web](../../extensibility/internals/web-projects.md)

 Présente une vue d’ensemble des deux types de projets Web, des projets de site Web et des projets d’application Web.
