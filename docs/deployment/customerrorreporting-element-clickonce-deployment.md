---
title: "&lt;customErrorReporting&gt; élément (déploiement ClickOnce) | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords: <customErrorReporting> element [ClickOnce deployment manifest]
ms.assetid: 7d31816e-c692-46b5-9cc9-753284b3bcda
caps.latest.revision: "6"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: b6b6726ebf45522834d916897f456952b66a3605
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltcustomerrorreportinggt-element-clickonce-deployment"></a>&lt;customErrorReporting&gt; élément (déploiement ClickOnce)
Spécifie un URI à afficher en cas d'erreur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<customErrorReporting  
   uri  
/>  
```  
  
## <a name="remarks"></a>Notes  
 Cet élément est facultatif. Sans lui, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] affiche une boîte de dialogue d’erreur indiquant la pile d’exception. Si le `customErrorReporting` élément est présent, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] affichera à la place de l’URI indiqué par le `uri` paramètre. L’URI cible inclut la classe d’exception externe, la classe de l’exception interne et le message d’exception interne en tant que paramètres.  
  
 Utilisez cet élément pour ajouter le rapport d’erreurs des fonctionnalités à votre application. Étant donné que l’URI généré inclut des informations sur le type d’erreur, votre site Web peut analyser ces informations et afficher, par exemple, un écran de dépannage approprié.  
  
## <a name="example"></a>Exemple  
 L’extrait de code de suivant le `customErrorReporting` élément, ainsi que l’URI généré qu’il peut produire.  
  
```  
<customErrorReporting uri=http://www.contoso.com/applications/error.asp />  
  
Example Generated Error:  
http://www.contoso.com/applications/error.asp? outer=System.Deployment.Application.InvalidDeploymentException&&inner=System.Deployment.Application.InvalidDeploymentException&&msg=The%20application%20manifest%20is%20signed,%20but%20the%20deployment%20manifest%20is%20unsigned.%20Both%20manifests%20must%20be%20either%20signed%20or%20unsigned.  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Manifeste de déploiement ClickOnce](../deployment/clickonce-deployment-manifest.md)