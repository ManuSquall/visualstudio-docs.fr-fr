---
title: "&lt;customHostSpecified&gt; élément (développement Office dans Visual Studio) | Documents Microsoft"
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
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <customHostSpecified> element
- <customHostSpecified> element
- customHostSpecified element
ms.assetid: 2212b7eb-bf94-4398-b9ea-0ab00203203b
caps.latest.revision: "23"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c7ad3bb1e62e2ea98f5afe1de5cc9eb49f711234
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="ltcustomhostspecifiedgt-element-office-development-in-visual-studio"></a>&lt;customHostSpecified&gt; élément (développement Office dans Visual Studio)
  Le `customHostSpecified` élément indique que cette solution n’est pas une application autonome. Les solutions Office contiennent des composants qui sont hébergés au sein des applications Microsoft Office.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<customHostSpecified />  
```  
  
## <a name="elements-and-attributes"></a>Éléments et attributs  
 Le `customHostSpecified` élément est requis pour les solutions Office. Cet élément est dans le `co.v1` espace de noms et spécifie que ce déploiement contient un composant qui sera déployé sur un hôte personnalisé, et n’est pas une application autonome.  
  
 Cet élément est un enfant du premier `<entrypoint>` élément dans le manifeste d’application. Il ne peut y avoir aucun autre élément enfant qui `<entrypoint>` élément ou [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] génère une erreur de validation lors de l’installation.  
  
 Cet élément a pas d’attributs et pas d’éléments enfants.  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant illustre la `customHostSpecified` élément dans un manifeste d’application pour une solution Office. Cet exemple de code fait partie d’un exemple plus complet fourni dans [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md).  
  
```  
<entryPoint>  
    <co.v1:customHostSpecified />  
</entryPoint>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)   
 [Manifestes de déploiement pour les Solutions Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Manifeste d’application ClickOnce](/visualstudio/deployment/clickonce-application-manifest)  
  
  