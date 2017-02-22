---
title: "&lt;customErrorReporting&gt; Element (ClickOnce Deployment) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "<customErrorReporting> element [ClickOnce deployment manifest]"
ms.assetid: 7d31816e-c692-46b5-9cc9-753284b3bcda
caps.latest.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 6
---
# &lt;customErrorReporting&gt; Element (ClickOnce Deployment)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Spécifie un URI à afficher lorsqu'une erreur se produit.  
  
## Syntaxe  
  
```  
<customErrorReporting  
   uri  
/>  
```  
  
## Notes  
 Cet élément est facultatif.  Sans lui, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] affiche une boîte de dialogue d'erreur indiquant la pile d'exception.  Si l'élément `customErrorReporting` est présent, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] affiche l'URI indiqué par le paramètre `uri`.  L'URI cible inclut la classe d'exception externe, la classe d'exception interne et le message d'exception interne sous forme de paramètres.  
  
 Utilisez cet élément pour ajouter les fonctionnalités de rapport d'erreurs à votre application.  Puisque l'URI généré inclut des informations concernant le type d'erreur, votre site Web peut analyser ces informations et afficher, par exemple, un écran de résolution des problèmes adapté.  
  
## Exemple  
 L'extrait de code suivant affiche l'élément `customErrorReporting`, accompagné de l'URI généré qu'il peut produire.  
  
```  
<customErrorReporting uri=http://www.contoso.com/applications/error.asp />  
  
Example Generated Error:  
http://www.contoso.com/applications/error.asp? outer=System.Deployment.Application.InvalidDeploymentException&&inner=System.Deployment.Application.InvalidDeploymentException&&msg=The%20application%20manifest%20is%20signed,%20but%20the%20deployment%20manifest%20is%20unsigned.%20Both%20manifests%20must%20be%20either%20signed%20or%20unsigned.  
```  
  
## Voir aussi  
 [ClickOnce Deployment Manifest](../deployment/clickonce-deployment-manifest.md)