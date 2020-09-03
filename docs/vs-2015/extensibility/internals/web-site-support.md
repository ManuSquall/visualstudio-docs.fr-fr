---
title: Prise en charge des sites Web | Microsoft Docs
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
ms.openlocfilehash: f1a96504783de466551c6fb9d055b95ba38df760
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65687695"
---
# <a name="web-site-support"></a>Prise en charge de site web
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Un système de projet de site Web est un système de projet qui crée des projets Web. Les projets Web créent à leur tour des applications Web. Un projet de site Web génère un fichier exécutable pour chaque page Web associée à du code. Des fichiers exécutables supplémentaires sont générés à partir des fichiers de code source dans le dossier/App_Code.  
  
 Les systèmes de projet de site Web sont créés en ajoutant des modèles et des attributs d’inscription à un système de projet existant. L’un de ces attributs sélectionne le fournisseur IntelliSense pour le langage. L’implémentation du fournisseur IntelliSense gère les références et appelle le compilateur de langage lorsqu’une page Web intelligente qui n’est pas mise en cache est demandée.  
  
 Le compilateur de langage utilisé pour compiler des pages Web doit être inscrit auprès de [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] . Vous pouvez utiliser l' [ \<compiler> élément](https://msdn.microsoft.com/library/7a151659-b803-4c27-b5ce-1c4aa0d5a823) dans un fichier de Web.config pour inscrire le compilateur, comme dans l’exemple suivant :  
  
```  
<system.codedom>  <compilers>    <compiler language="py;IronPython" extension=".py"       type="IronPython.CodeDom.PythonProvider, IronPython,       Version=1.0.2391.18146, Culture=neutral,       PublicKeyToken=b03f5f7f11d50a3a" />  </compilers></system.codedom>  
```  
  
## <a name="in-this-section"></a>Dans cette section  
 [Modèles de prise en charge de site web](../../extensibility/internals/web-site-support-templates.md)  
 Répertorie les modèles que vous pouvez utiliser pour créer des projets de site Web et des éléments associés.  
  
 [Attributs de prise en charge de site web](../../extensibility/internals/web-site-support-attributes.md)  
 Présente les attributs d’inscription qui connectent un projet de site Web à [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] et [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] .  
  
## <a name="related-sections"></a>Sections connexes  
 [Projets web](../../extensibility/internals/web-projects.md)  
 Présente une vue d’ensemble des deux types de projets Web, des projets de site Web et des projets d’application Web.
