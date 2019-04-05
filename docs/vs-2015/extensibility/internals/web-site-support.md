---
title: Prise en charge du Site Web | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- web site projects
ms.assetid: ce9f4266-bb64-4c09-be88-4bd6413f60d0
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 91deb6d2e3ec58533ac9339c8c94634db23ec996
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58954103"
---
# <a name="web-site-support"></a>Prise en charge de site web
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Un système de projet de site Web est un système de projet qui crée des projets Web. À leur tour, les projets Web créent des applications Web. Un projet de site Web génère un fichier exécutable pour chaque page Web qui est associé à code. Fichiers exécutables supplémentaires sont générés à partir des fichiers de code source dans le dossier/App_Code.  
  
 Les systèmes de projet de site Web sont créées en ajoutant des modèles et des attributs d’inscription à un système de projet existant. Un de ces attributs sélectionne le fournisseur d’IntelliSense pour la langue. L’implémentation du fournisseur IntelliSense traite les références et appelle le compilateur de langage lorsqu’une page Web active qui n’est pas mis en cache est demandée.  
  
 Le compilateur de langage utilisé pour compiler les pages Web doit être enregistré avec [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)]. Vous pouvez utiliser la [ \<compilateur > élément](http://msdn.microsoft.com/library/7a151659-b803-4c27-b5ce-1c4aa0d5a823) dans un fichier Web.config pour inscrire le compilateur, comme dans l’exemple suivant :  
  
```  
<system.codedom>  <compilers>    <compiler language="py;IronPython" extension=".py"       type="IronPython.CodeDom.PythonProvider, IronPython,       Version=1.0.2391.18146, Culture=neutral,       PublicKeyToken=b03f5f7f11d50a3a" />  </compilers></system.codedom>  
```  
  
## <a name="in-this-section"></a>Dans cette section  
 [Modèles de prise en charge de site Web](../../extensibility/internals/web-site-support-templates.md)  
 Répertorie les modèles que vous pouvez utiliser pour créer des projets de site Web et les éléments associés.  
  
 [Attributs de prise en charge de site Web](../../extensibility/internals/web-site-support-attributes.md)  
 Présente les attributs d’inscription qui se connectent à un projet de site Web [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] et [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)].  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Projets Web](../../extensibility/internals/web-projects.md)  
 Présente une vue d’ensemble des deux types de projets Web, les projets de site Web et les projets d’application Web.
