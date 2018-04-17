---
title: '&lt;document&gt; élément (développement Office dans Visual Studio) | Documents Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- document element
- application manifests [Office development in Visual Studio], <document> element
- <document> element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 0e33e638937a02589a08e3ba2bebf9d3e9aeb1a4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="ltdocumentgt-element-office-development-in-visual-studio"></a>&lt;document&gt; élément (développement Office dans Visual Studio)
  Le `document` élément de la `vstov4` espace de noms stocke des informations spécifiques à la personnalisation pour les personnalisations au niveau du document.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<document solutionId />  
```  
  
## <a name="elements-and-attributes"></a>Éléments et attributs  
 Obligatoire uniquement pour les personnalisations au niveau du document. Le `document` élément se trouve dans le `vstov4` espace de noms. Le `document` élément a les attributs suivants.  
  
|Attribut|Description|  
|---------------|-----------------|  
|`solutionId`|Obligatoire. Le GUID utilisé par Visual Studio Tools pour Office runtime pour identifier de façon unique une solution au niveau du document. Cette valeur est stockée en tant que propriété _AssemblyLocation de document personnalisée. Pour plus d'informations, consultez [Custom Document Properties Overview](../vsto/custom-document-properties-overview.md).|  
  
 `document` ne comporte aucun élément enfant.  
  
## <a name="document-level-customization-example"></a>Exemple de personnalisation au niveau du document  
  
### <a name="description"></a>Description  
 L’exemple de code suivant illustre la `document` élément dans une solution d’Office au niveau du document déployée à l’aide de [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Cet exemple de code fait partie d’un exemple plus complet fourni dans [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Code  
  
```  
<vstov4:document   
  solutionId="73e" />  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)   
 [Manifestes de déploiement pour les Solutions Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Manifeste d’application ClickOnce](/visualstudio/deployment/clickonce-application-manifest)  
  
  