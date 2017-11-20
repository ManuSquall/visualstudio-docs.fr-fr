---
title: "&lt;postAction&gt; élément (développement Office dans Visual Studio) | Documents Microsoft"
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
- application manifests [Office development in Visual Studio], <postAction> element
- <postAction> element
- postAction element
ms.assetid: a047e2e2-9732-4140-b8bd-bc5bd1b84291
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 581ef7bafc075419df8e2dfb1731b334a9564455
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="ltpostactiongt-element-office-development-in-visual-studio"></a>&lt;postAction&gt; élément (développement Office dans Visual Studio)
  L’élément `postAction` de l’espace de noms `vstav3` contient les éléments `entrypoint` et tous les éléments `postActionData` associés à des actions de post-déploiement, lesquelles s’exécutent après l’installation des solutions Office.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<postAction>  
  <entryPoint>  
  </entryPoint>  
  <postActionData>  
  </postActionData>  
</postAction>  
```  
  
## <a name="elements-and-attributes"></a>Éléments et attributs  
 L’élément `postAction` est facultatif et se trouve dans l’espace de noms `vstav3` . Il existe un seul élément `postAction` défini dans un manifeste de l’application pour chaque action de post-déploiement.  
  
 L’élément `postAction` ne possède pas d’attributs.  
  
 `postAction` comporte les éléments suivants.  
  
### <a name="entrypoint"></a>entrypoint  
 Facultatif. Le rôle de la `entryPoint` élément dans le `vstav3` espace de noms est défini dans [&#60; entryPoints &#62; Élément &#40; développement Office dans Visual Studio &#41; ](../vsto/entrypoints-element-office-development-in-visual-studio.md).  
  
### <a name="postactiondata"></a>postActionData  
 Facultatif. Le rôle de la `postActionData` élément dans le `vstav3` espace de noms est défini dans [&#60; postActionData &#62; Élément &#40; développement Office dans Visual Studio &#41; ](../vsto/postactiondata-element-office-development-in-visual-studio.md).  
  
## <a name="post-deployment-action-example"></a>Exemple d’action de post-déploiement  
  
### <a name="description"></a>Description  
 L’exemple de code suivant illustre l’élément `postAction` d’un manifeste de l’application pour une solution Office déployée à l’aide de [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Cet exemple de code fait partie d’un exemple plus complet fourni dans [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Code  
  
```  
<vstav3:postAction>  
  <vstav3:entryPoint   
    class="PostDeploymentAction.PostDeploymentActionSample">  
    <assemblyIdentity   
      name="PostDeploymentAction"   
      version="1.0.0.0"   
      language="neutral"   
      processorArchitecture="msil" />  
  </vstav3:entryPoint>  
  <vstav3:postActionData>  
  </vstav3:postActionData>  
</vstav3:postAction>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)   
 [Manifestes de déploiement pour les Solutions Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Manifeste d’application ClickOnce](/visualstudio/deployment/clickonce-application-manifest)  
  
  