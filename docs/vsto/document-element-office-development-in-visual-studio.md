---
title: '&lt;document&gt; élément (développement Office dans Visual Studio)'
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
ms.openlocfilehash: 07d8172ec4e56352c2244aef02d947ac48833ab7
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/22/2018
---
# <a name="ltdocumentgt-element-office-development-in-visual-studio"></a>&lt;document&gt; élément (développement Office dans Visual Studio)
  Le `document` élément de la `vstov4` espace de noms stocke des informations spécifiques à la personnalisation pour les personnalisations au niveau du document.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<document solutionId />  
```  
  
## <a name="elements-and-attributes"></a>Éléments et attributs  
 Obligatoire uniquement pour les personnalisations au niveau du document. Le `document` élément se trouve dans le `vstov4` espace de noms. Le `document` élément a les attributs suivants.  
  
|Attribut|Description|  
|---------------|-----------------|  
|`solutionId`|Obligatoire. Le GUID utilisé par Visual Studio Tools pour Office runtime pour identifier de façon unique une solution au niveau du document. Cette valeur est stockée en tant que propriété _AssemblyLocation de document personnalisée. Pour plus d’informations, consultez [vue d’ensemble des propriétés de document personnalisées](../vsto/custom-document-properties-overview.md).|  
  
 `document` ne comporte aucun élément enfant.  
  
## <a name="document-level-customization-example"></a>Exemple de personnalisation au niveau du document  
  
### <a name="description"></a>Description  
 L’exemple de code suivant illustre la `document` élément dans une solution d’Office au niveau du document déployée à l’aide de [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Cet exemple de code fait partie d’un exemple plus complet fourni dans [manifestes d’Application pour les solutions Office](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Code  
  
```xml
<vstov4:document   
  solutionId="73e" />  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Manifestes d’application pour les solutions Office](../vsto/application-manifests-for-office-solutions.md)   
 [Manifestes de déploiement pour les solutions Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Manifeste d’application ClickOnce](/visualstudio/deployment/clickonce-application-manifest)  
  
  