---
title: "&lt;friendlyName&gt; élément (développement Office dans Visual Studio) | Documents Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords: application manifests [Office development in Visual Studio], <friendlyName> element
ms.assetid: 80250fbf-fccf-4baa-948e-ace7f4449e9c
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a8019e2446da0feb23cb12dad1a4bbfd4f8a4920
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="ltfriendlynamegt-element-office-development-in-visual-studio"></a>&lt;friendlyName&gt; élément (développement Office dans Visual Studio)
  L’élément `friendlyName` de l’espace de noms `vstov4` stocke le nom qui apparaît dans la liste des programmes installés.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<friendlyName>  
</friendlyName>  
```  
  
## <a name="elements-and-attributes"></a>Éléments et attributs  
 L’élément `friendlyName` se trouve dans l’espace de noms `vstov4` . La valeur apparaît dans la liste des programmes installés sur l’ordinateur, ainsi que dans la boîte de dialogue des compléments VSTO COM des applications Microsoft Office.  
  
 L’élément `friendlyName` n’a aucun attribut ou élément enfant.  
  
## <a name="vsto-add-in-example"></a>Exemple de complément VSTO  
  
### <a name="description"></a>Description  
 L’exemple de code suivant illustre l’élément `friendlyName` d’une solution au niveau de l’application déployée à l’aide de [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Cet exemple de code fait partie d’un exemple plus complet fourni dans [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Code  
  
```  
<vstov4:friendlyName>  
  ContosoOutlookAddIn  
</vstov4:friendlyName>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)   
 [Manifestes de déploiement pour les Solutions Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Manifeste d’application ClickOnce](/visualstudio/deployment/clickonce-application-manifest)  
  
  