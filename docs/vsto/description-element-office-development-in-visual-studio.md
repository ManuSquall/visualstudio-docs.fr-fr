---
title: '&lt;Description&gt; élément (développement Office dans Visual Studio) | Documents Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- description element
- <description> element
- application manifests [Office development in Visual Studio], <description> element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 13755a20b091696bf741c1f25360941e01b65945
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="ltdescriptiongt-element-office-development-in-visual-studio"></a>&lt;Description&gt; élément (développement Office dans Visual Studio)
  L’élément `description` de l’espace de noms `vstov4` stocke la description de la solution Office qui s’affiche dans la boîte de dialogue des compléments COM des applications Microsoft Office.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<description>  
</description>  
```  
  
## <a name="elements-and-attributes"></a>Éléments et attributs  
 Facultatif. L’élément `description` se trouve dans l’espace de noms `vstov4` . Il contient la description du complément qui s’affiche dans la boîte de dialogue des compléments COM des applications Microsoft Office.  
  
 L’élément `description` n’a aucun attribut ou élément.  
  
## <a name="vsto-add-in-example"></a>Exemple de complément VSTO  
  
### <a name="description"></a>description  
 L’exemple de code suivant illustre l’élément `description` d’une solution au niveau de l’application déployée à l’aide de [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Cet exemple de code fait partie d’un exemple plus complet fourni dans [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Code  
  
```  
<vstov4:description>  
  ContosoOutlookAddIn - Outlook add-in   
  created with Visual Studio Tools for Office  
</vstov4:description>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)   
 [Manifestes de déploiement pour les Solutions Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Manifeste d’application ClickOnce](/visualstudio/deployment/clickonce-application-manifest)  
  
  